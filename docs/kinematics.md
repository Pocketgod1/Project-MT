# Kinematics Framework - Project MT

## Executive Summary

This document outlines the inverse kinematics (IK) and forward kinematics (FK) approach for Project MT. Kinematics is the mathematical foundation that converts animation target positions into motor commands.

## Terminology

- **Forward Kinematics (FK)**: Joint angles → End-effector position
- **Inverse Kinematics (IK)**: Target end-effector position → Joint angles
- **DOF (Degrees of Freedom)**: Number of independent joints
- **End-effector**: Hand, foot, or other extremity
- **Joint Space**: Representation using joint angles
- **Cartesian Space**: Representation using 3D coordinates (x, y, z)

---

## Planned DOF Per Limb

### Arm (each side) - 4 DOF
1. Shoulder abduction/adduction (0° to 90°)
2. Shoulder flexion/extension (0° to 180°)
3. Elbow flexion/extension (0° to 150°)
4. Wrist rotation (0° to 180°)
   - Note: Simplified; full wrist has 3 DOF (flexion, rotation, deviation)

### Leg (each side) - 3 DOF
1. Hip flexion/extension (0° to 120°)
2. Hip abduction/adduction (-45° to +45°)
3. Knee flexion/extension (0° to 130°)
4. Ankle (simplified, grouped with knee for initial work)

### Torso - 2 DOF
1. Spine flexion/extension (-30° to +30°)
2. Spine rotation (-60° to +60°)

### Total Initial DOF: ~18-22 motors

---

## Forward Kinematics

### Mathematical Foundation

**Denavit-Hartenberg (DH) Convention**: Standard method for representing robot kinematics

For each joint, define:
- $a_i$: Link offset (distance along rotated x-axis)
- $\alpha_i$: Link twist (rotation about rotated x-axis)
- $d_i$: Link length (distance along z-axis)
- $\theta_i$: Joint angle (rotation about z-axis)

**Transformation Matrix**: Each joint has a 4×4 homogeneous transformation matrix:

$$T_i = \begin{bmatrix}
\cos\theta_i & -\sin\theta_i\cos\alpha_i & \sin\theta_i\sin\alpha_i & a_i\cos\theta_i \\
\sin\theta_i & \cos\theta_i\cos\alpha_i & -\cos\theta_i\sin\alpha_i & a_i\sin\theta_i \\
0 & \sin\alpha_i & \cos\alpha_i & d_i \\
0 & 0 & 0 & 1
\end{bmatrix}$$

**End-Effector Position**:
$$T_{EE} = T_0 \cdot T_1 \cdot T_2 \cdots T_n$$

### Python Implementation (Pseudocode)

```python
import numpy as np

def forward_kinematics(theta_array):
    """
    Compute end-effector position from joint angles.
    
    Args:
        theta_array: Joint angles [θ1, θ2, θ3, θ4, ...]
    
    Returns:
        Position: (x, y, z, roll, pitch, yaw)
    """
    T = np.eye(4)  # Homogeneous matrix
    
    for i, theta in enumerate(theta_array):
        T_i = dh_matrix(theta, dh_params[i])
        T = T @ T_i
    
    # Extract position
    position = T[0:3, 3]
    # Extract orientation (roll, pitch, yaw)
    orientation = matrix_to_euler(T[0:3, 0:3])
    
    return position, orientation
```

---

## Inverse Kinematics

### Challenge

IK is harder than FK:
- Multiple solutions possible (arm can reach a point via different configurations)
- Some positions unreachable
- Mathematical complexity (non-linear equations)

### Solution Strategy: FABRIK Algorithm

**Forward And Backward Reaching IK** - Numerical, iterative approach

**Advantages**:
- Works for any DOF
- Handles joint limits naturally
- Relatively fast (few iterations)
- Intuitive behavior (mimics natural motion)

**Algorithm**:
1. Start with current joint angles
2. **Forward pass**: Move end-effector toward target
3. **Backward pass**: Ensure base stays fixed
4. Repeat until convergence or max iterations

### Python Implementation (Simplified)

```python
def fabrik(target_pos, chain_lengths, joint_limits, max_iterations=10):
    """
    FABRIK inverse kinematics solver.
    
    Args:
        target_pos: Target end-effector position [x, y, z]
        chain_lengths: Distance between joints [l1, l2, l3, ...]
        joint_limits: Min/max angles per joint
        max_iterations: Convergence iterations
    
    Returns:
        Joint angles that reach target_pos (or closest approximation)
    """
    positions = initialize_chain()
    
    for iteration in range(max_iterations):
        # Forward pass
        positions[-1] = target_pos
        for i in range(len(positions) - 2, 0, -1):
            direction = positions[i] - positions[i + 1]
            positions[i] = positions[i + 1] + chain_lengths[i] * normalize(direction)
        
        # Backward pass (fix base)
        positions[0] = base_position
        for i in range(1, len(positions)):
            direction = positions[i] - positions[i - 1]
            positions[i] = positions[i - 1] + chain_lengths[i - 1] * normalize(direction)
        
        # Check convergence
        if distance(positions[-1], target_pos) < tolerance:
            break
    
    # Convert positions to angles
    theta_array = positions_to_angles(positions)
    theta_array = clamp_to_limits(theta_array, joint_limits)
    
    return theta_array
```

---

## Trajectory Planning

### Smooth Motion Between Frames

Animation provides target positions at discrete frames (e.g., 30 fps). Robot control runs at higher frequency (50-200 Hz). Need smooth interpolation.

### Cubic Interpolation

```python
def interpolate_trajectory(start_angles, end_angles, num_steps):
    """
    Generate smooth trajectory between two joint configurations.
    Uses cubic (smooth, zero acceleration at endpoints).
    """
    trajectory = []
    for step in range(num_steps):
        t = step / num_steps
        # Cubic interpolation: 3t² - 2t³
        s = 3 * t**2 - 2 * t**3
        current = start_angles + s * (end_angles - start_angles)
        trajectory.append(current)
    return trajectory
```

---

## Balance & Center of Mass

### Key Concept

For bipedal standing and walking, the robot's center of mass (CoM) must stay within the support polygon (feet).

### Implementation

```python
def check_stability(joint_angles, link_masses, link_positions):
    """
    Compute center of mass and check if within support base.
    """
    total_mass = sum(link_masses)
    com_position = sum(mass * pos for mass, pos in zip(link_masses, link_positions)) / total_mass
    
    # Support polygon (simplified to feet positions)
    support_base = compute_support_polygon(foot_positions)
    
    is_stable = point_in_polygon(com_position, support_base)
    
    return is_stable, com_position
```

---

## Collision Detection

### Simple Box Collisions

```python
def check_collision(joint_angles):
    """
    Quick collision check using axis-aligned bounding boxes.
    """
    link_positions = forward_kinematics(joint_angles)
    
    for i, link_i in enumerate(link_positions):
        for j, link_j in enumerate(link_positions):
            if i < j:
                if boxes_overlap(link_i, link_j):
                    return True  # Collision detected
    
    return False  # No collision
```

---

## Real-Time Considerations

### Performance Targets

- **FK computation**: < 1 ms
- **IK computation**: < 10 ms
- **Trajectory planning**: Precomputed
- **Collision check**: < 5 ms

### Optimization Strategies

1. **Pre-compute complex matrices**: Cache DH parameters
2. **Use fast matrix libraries**: NumPy (C backend)
3. **Limit IK iterations**: Usually converges in 5-10 iterations
4. **GPU acceleration**: For heavy computations (future optimization)

---

## Singularities & Limitations

### Wrist Singularity

When shoulder and wrist rotation axes align, one DOF is lost. Solution:
- Avoid this configuration in animation
- Blend nearby valid configurations
- Reduce animation to reachable space

### Joint Limits

Each servo has physical limits (e.g., 0° to 180°). Solutions:
- Enforce limits in IK solver (FABRIK handles naturally)
- Pre-validate animations
- Use configuration space planning

---

## Testing & Validation

### Unit Tests (Pseudocode)

```python
def test_forward_kinematics():
    # Test known configuration
    theta = [0, 0, 0, 0]  # All joints aligned
    pos = forward_kinematics(theta)
    expected = [1.5, 0, 1.2]  # Known end-effector position
    assert distance(pos, expected) < 0.01

def test_inverse_kinematics():
    # Test round-trip: IK(FK(angles)) == angles
    angles = [30, 45, 60, 90]
    pos = forward_kinematics(angles)
    recovered_angles = fabrik(pos, ...)
    assert angles_close(angles, recovered_angles)

def test_balance():
    # Ensure standing poses are stable
    standing_angles = get_standing_configuration()
    is_stable, com = check_stability(standing_angles)
    assert is_stable
```

---

## Next Steps

1. **Week 1**: Measure InMoov dimensions and derive DH parameters
2. **Week 2**: Implement FK solver in Python
3. **Week 3**: Implement FABRIK IK solver
4. **Week 4**: Test in simulation (Gazebo)
5. **Week 5**: Validate against real robot

---

## References

- Denavit & Hartenberg (1955): "A Kinematic Notation for Lower-Pair Mechanisms"
- Buss & Kim (2005): "FABRIK: A Fast Reaching IK Solver"
- Craig, J.J. (2005): "Introduction to Robotics: Mechanics and Control" (textbook)

