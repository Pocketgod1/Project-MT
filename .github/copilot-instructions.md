# Copilot Instructions for Project MT

## Project Context

Project MT is an advanced robotics initiative to build a human-sized bipedal humanoid robot based on the InMoov open-source platform, capable of replicating animation movement patterns from games like Elden Ring.

## Development Approach

### When providing assistance, consider:

1. **Robotics-First Mindset**: Think about physical constraints, actuator limitations, and real-world dynamics
2. **Modular Architecture**: Keep control systems, kinematics, and animation layers separate
3. **Simulation Before Hardware**: Encourage testing in simulation (Gazebo/RViz) before deployment
4. **Progressive Complexity**: Move from static posturing → walking → animation playback

### Key Guidelines

- **Beginner Context**: Project lead has 3D printing experience and Python skills but is new to robotics
- **Hardware-Software Integration**: Always consider how software decisions impact mechanical design
- **Documentation**: Maintain clear architecture docs as systems grow in complexity
- **Testing Framework**: Establish unit tests for kinematics, motor control, and animation parsing early

### Focus Areas

- Motor control and servo synchronization
- Inverse/forward kinematics calculations
- Animation format parsing and mapping
- Balance and gait algorithms
- Power system management

## Preferred Technologies

- **Primary Language**: Python (control logic, high-level coordination)
- **Embedded**: C/C++ (motor controllers, real-time systems)
- **Simulation**: Gazebo + RViz (optional, but recommended)
- **Kinematics**: NumPy/SciPy or specialized libraries
- **Animation**: Blender integration, FBX/GLTF parsing

## Communication Style

- Be concise but thorough when explaining robotics concepts
- Provide pseudocode or diagrams for complex kinematics
- Highlight physical constraints and limitations early
- Suggest prototyping approaches for unproven concepts

## Current Project Status

- **Phase**: 0 (Planning & Research)
- **Next Steps**: Complete hardware research and architecture design
- **Known Constraints**: Budget-conscious, 3D-printed components, single developer
