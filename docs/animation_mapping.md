# Animation Mapping & Format Specification - Project MT

## Overview

This document specifies how animations from games (Elden Ring) are extracted, parsed, and mapped to robot kinematics.

---

## Animation File Formats

### FBX Format (Preferred)
- **Extension**: `.fbx`
- **Encoding**: Binary (can be exported as ASCII)
- **Contents**: Skeleton, animation keyframes, blend shapes
- **Tools**: Blender (free), 3DS Max, Maya
- **Game Support**: Most AAA games (Elden Ring uses similar)

### Skeleton Structure (JSON Export Example)

```json
{
  "skeleton": {
    "bones": [
      {
        "id": 0,
        "name": "Armature",
        "parent": -1,
        "position": [0, 0, 0],
        "rotation": [0, 0, 0, 1]
      },
      {
        "id": 1,
        "name": "Hips",
        "parent": 0,
        "position": [0, 1, 0],
        "rotation": [0, 0, 0, 1]
      },
      {
        "id": 2,
        "name": "RightThigh",
        "parent": 1,
        "position": [0.1, 0, 0],
        "rotation": [0, 0, 0, 1]
      }
    ]
  },
  "animations": {
    "idle": {
      "frame_rate": 30,
      "total_frames": 60,
      "keyframes": [
        {
          "frame": 0,
          "bones": [
            {"id": 0, "rotation": [0, 0, 0, 1]},
            {"id": 1, "rotation": [0, 0, 0, 1]}
          ]
        }
      ]
    }
  }
}
```

---

## Skeleton Mapping: Game → Robot

### Mapping Strategy

A human skeleton has ~90 DOF; the robot has ~20-30. Must identify which movements to preserve.

### Key Anatomical Correspondence

| Game Bone | Robot Joint | DOF | Notes |
|-----------|------------|-----|-------|
| Hips | Hip Flexion | 1 | Vertical translate → hip angle |
| Spine | Torso Bend | 2 | Combined into 2D bending |
| UpperArm.R | Shoulder + Elbow | 2 | Combined into reaching |
| Forearm.R | Wrist Rotation | 1 | Grip orientation |
| Thigh.R | Hip Flexion | 1 | Forward/backward leg swing |
| Shin.R | Knee Flexion | 1 | Leg extension |
| Foot.R | Ankle | 0 | Simplified; attached to shin |

### Mapping Configuration (YAML)

```yaml
skeleton_mapping:
  game_to_robot:
    hips:
      target: hip_flexion
      scale: 1.0
      offset: 0
    spine.001:
      target: torso_bend_xy
      scale: [1.0, 1.0]
      offset: [0, 0]
    armature_UpperArm_R:
      target: [shoulder_flex, shoulder_abd]
      scale: [1.0, 0.5]
      offset: [0, 0]
```

---

## Animation Pipeline

### Step 1: Export from Game
```python
# Blender script to export FBX
# Save skeleton and animation keyframes
```

### Step 2: Parse FBX
```python
import fbx

def parse_fbx(filename):
    scene = fbx.load(filename)
    skeleton = extract_skeleton(scene)
    animations = extract_animations(scene)
    return skeleton, animations
```

### Step 3: Map to Robot Skeleton
```python
def map_animation_to_robot(game_animation, mapping_config):
    robot_animation = {
        'frames': [],
        'frame_rate': game_animation['frame_rate']
    }
    
    for game_frame in game_animation['keyframes']:
        robot_frame = {}
        for game_joint, robot_joint in mapping_config.items():
            if game_joint in game_frame:
                robot_frame[robot_joint] = apply_mapping(game_frame[game_joint])
        robot_animation['frames'].append(robot_frame)
    
    return robot_animation
```

### Step 4: Validate & Smooth
```python
def validate_animation(robot_animation, joint_limits):
    for frame in robot_animation['frames']:
        for joint, angle in frame.items():
            if not is_within_limits(angle, joint_limits[joint]):
                # Clamp or blend to valid configuration
                frame[joint] = clamp(angle, joint_limits[joint])
    
    # Smooth transitions between frames
    robot_animation['frames'] = smooth_trajectory(robot_animation['frames'])
    
    return robot_animation
```

---

## Animation Blending

When animation requires movements outside robot's workspace:

### Blend Strategies

1. **Scale**: Reduce animation intensity (e.g., 80% of original range)
2. **Remap**: Map out-of-bounds movements to nearest valid configuration
3. **Interpolate**: Blend between valid nearby poses

### Example: Arm Reaching

```python
def blend_reaching_motion(game_target, robot_limits):
    """
    If game target is outside reachable workspace, find closest valid pose.
    """
    # Try to reach game target
    ik_result = solve_ik(game_target)
    
    if ik_result and all_within_limits(ik_result, robot_limits):
        return ik_result  # Success
    
    # Fallback: blend toward valid configuration
    safe_target = scale_toward_origin(game_target, scale=0.8)
    ik_result = solve_ik(safe_target)
    
    return ik_result
```

---

## Common Elden Ring Animations

### Critical Animations to Extract

| Animation | Key Joints | Complexity | Notes |
|-----------|-----------|-----------|-------|
| Idle | Torso, arms, legs | Low | Foundation of all animations |
| Walk Forward | Hips, legs, torso | Medium | Bipedal gait pattern |
| Run | Same as walk, higher speed | Medium | Frequency-scaled walking |
| Attack (Slash) | Arms, shoulders, torso | High | Complex coordinated motion |
| Dodge Roll | Entire body | High | Dynamic balance required |
| Block | Arms, shoulders | Low | Static posture variation |
| Fall/React | All joints | Very high | Uncontrolled motion |

### Extraction Priority

1. **Phase 4 Start**: Idle + basic arm reaching
2. **Phase 4 Mid**: Walk forward + turn
3. **Phase 4 Late**: Basic attack motions
4. **Phase 5**: Complex choreography (dodge, multi-hit)

---

## Performance Metrics

### Animation Playback

- **Latency**: Time from animation frame to motor command < 100ms
- **Smoothness**: Jerk (3rd derivative of position) < threshold
- **Accuracy**: Achieved pose matches target within 5° per joint

### Validation

```python
def measure_animation_quality(game_animation, robot_feedback):
    latency = measure_latency()
    smoothness = measure_jerk(robot_feedback)
    accuracy = measure_pose_error(target=game_animation, actual=robot_feedback)
    
    return {
        'latency_ms': latency,
        'smoothness': smoothness,
        'accuracy_degrees': accuracy
    }
```

---

## Future Work

- Real-time animation mixing (blend between animations)
- Dynamic constraint adjustment
- Machine learning-based pose correction
- Multi-character synchronization

