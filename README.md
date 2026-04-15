# Project MT: InMoov-Based Bipedal Robot with Animation Mimicry

A full-scale, human-sized bipedal humanoid robot capable of replicating animation movement patterns from video games (Elden Ring and similar titles).

## Project Overview

**Status**: In Planning Phase  
**Base Platform**: [InMoov](https://inmoov.fr/) (Open-source 3D-printed humanoid robot)  
**Primary Goal**: Create a functional bipedal robot that mimics complex animation sequences  
**Target Complexity**: Elden Ring-style combat and movement animations  

## Key Features (Target)

- Full-body bipedal locomotion with dynamic balance
- 4+ degrees of freedom per arm (reaching and grasping)
- Spine articulation for realistic movement
- Real-time animation pattern recognition and playback
- Inverse kinematics for limb positioning
- Computer vision for environment awareness
- Motor control synchronization

## Project Phases

### Phase 0: Planning & Research (Current)
- [ ] InMoov framework deep-dive
- [ ] Animation format analysis (Elden Ring)
- [ ] Hardware component selection
- [ ] System architecture design
- [ ] Kinematics calculations

### Phase 1: Hardware Foundation
- [ ] Component procurement
- [ ] 3D model customization
- [ ] 3D printing of major components
- [ ] Motor and servo selection and testing
- [ ] Power system design

### Phase 2: Basic Control System
- [ ] Motor drivers and control boards
- [ ] Serial communication framework
- [ ] Individual joint control
- [ ] Calibration utilities

### Phase 3: Kinematics & Movement
- [ ] Inverse kinematics implementation
- [ ] Forward kinematics testing
- [ ] Balance algorithms
- [ ] Bipedal walking (statically stable → dynamic)

### Phase 4: Animation Integration
- [ ] Game animation extraction tools
- [ ] Animation format parsing
- [ ] Skeleton mapping (game → robot)
- [ ] Real-time animation playback

### Phase 5: AI & Perception
- [ ] Computer vision system
- [ ] Environment mapping
- [ ] Motion planning algorithms

## Project Structure

```
Project MT/
├── docs/                  # Documentation
│   ├── project_plan.md
│   ├── architecture.md
│   ├── kinematics.md
│   └── animation_mapping.md
├── hardware/              # Hardware specifications
│   ├── bom.md            # Bill of Materials
│   ├── motor_specs.md
│   ├── power_system.md
│   └── sensor_specs.md
├── software/              # Control software
│   ├── firmware/          # Embedded controller code
│   ├── control_system/    # Motor and joint control
│   ├── kinematics/        # IK/FK calculations
│   ├── animation/         # Animation processing
│   └── perception/        # Vision and sensing
├── cad_models/            # 3D model references
│   ├── inmov_base/
│   ├── custom_parts/
│   └── assembly_guides/
├── research/              # Reference materials
│   ├── animation_analysis/
│   ├── robotics_theory/
│   └── resources.md
└── README.md
```

## Getting Started

1. **Review Documentation**: Start with [docs/project_plan.md](docs/project_plan.md)
2. **Understand InMoov**: Visit [inmoov.fr](https://inmoov.fr/) and review base design
3. **Analyze Target Animations**: Collect and analyze movement patterns
4. **Component Research**: Review [hardware/bom.md](hardware/bom.md) for initial parts list

## Key Technologies

- **Robotics**: ROS 2 (tentative), Gazebo (simulation)
- **Control**: Python, C++ (firmware)
- **Kinematics**: NumPy, SciPy, potential UrdfFast
- **Animation**: Blender (FBX/GLTF parsing), game modding tools
- **Computer Vision**: OpenCV, MediaPipe

## Resources

- InMoov Official: https://inmoov.fr/
- GitHub: https://github.com/InMoov/InMoov
- Community Forums: https://github.com/InMoov/InMoov/discussions

## Notes for Beginners

This is an advanced robotics project combining:
- 3D printing & mechanical engineering
- Embedded systems & motor control
- Kinematics & dynamics
- Animation processing
- Software architecture

**Recommendation**: Start with static posturing (Phase 2), then progress to walking, then animation.

---

**Last Updated**: April 2026  
**Project Owner**: [Your Name]
