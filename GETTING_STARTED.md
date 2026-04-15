# Getting Started - Quick Setup Guide

## Welcome to Project MT!

This guide will get you oriented with the project structure and help you tackle Phase 0 (Planning & Research).

---

## What is Project MT?

A human-sized, bipedal humanoid robot based on InMoov that can replicate animation movement patterns from video games like Elden Ring.

**Your Role**: Build from the ground up with 3D printing, robotics, and software.

---

## Quick Navigation

### 📚 For Understanding the Project
1. Start here: [README.md](README.md)
2. Understand phases: [docs/project_plan.md](docs/project_plan.md)
3. System design: [docs/architecture.md](docs/architecture.md)

### 🔧 For Hardware
1. Component list: [hardware/bom.md](hardware/bom.md)
2. Motor specs: [hardware/motor_specs.md](hardware/motor_specs.md) *(create next)*
3. Power system: [hardware/power_system.md](hardware/power_system.md) *(create next)*

### 💻 For Software
1. Kinematics math: [docs/kinematics.md](docs/kinematics.md)
2. Architecture: [docs/architecture.md](docs/architecture.md)
3. Animation mapping: [docs/animation_mapping.md](docs/animation_mapping.md)

### 🔬 For Research
1. Resources & links: [research/resources.md](research/resources.md)
2. InMoov platform: https://inmoov.fr/
3. Robotics theory: See resources.md for course links

---

## Phase 0: What to Do Right Now

### Week 1-2: Research & Analysis

- [ ] **Explore InMoov**
  - Visit https://inmoov.fr/
  - Download base 3D models
  - Study design constraints
  - Document DOF and servo specifications

- [ ] **Analyze Target Animations**
  - Find Elden Ring animation assets
  - Map game skeleton structure
  - Identify which animations to replicate
  - Note: Use modding tools (legal and available)

- [ ] **Study Kinematics**
  - Review [docs/kinematics.md](docs/kinematics.md)
  - Learn forward/inverse kinematics concepts
  - Understand DOF and reachability

### Week 3-4: Planning & Validation

- [ ] **Refine Architecture**
  - Review [docs/architecture.md](docs/architecture.md)
  - Identify potential bottlenecks
  - Plan simulation approach

- [ ] **Select Components**
  - Review [hardware/bom.md](hardware/bom.md)
  - Research servo motor options
  - Check availability and cost
  - Decide on microcontroller platform

- [ ] **Create Action Items**
  - Prioritize Phase 1 tasks
  - Set procurement schedule
  - Identify first prototype scope

---

## Project Structure

```
Project MT/
├── README.md (overview)
├── .github/
│   └── copilot-instructions.md (custom AI guidance)
├── docs/
│   ├── project_plan.md ⭐ (phase breakdown)
│   ├── architecture.md (system design)
│   ├── kinematics.md (math for motion)
│   └── animation_mapping.md (game→robot conversion)
├── hardware/
│   ├── bom.md (bill of materials)
│   ├── motor_specs.md (servo details) [TODO]
│   ├── power_system.md (battery & power) [TODO]
│   └── sensor_specs.md (sensors & feedback) [TODO]
├── software/
│   ├── firmware/ (embedded C/C++)
│   ├── control_system/ (motor control in Python)
│   ├── kinematics/ (FK/IK solvers)
│   ├── animation/ (game animation processing)
│   └── perception/ (vision & sensing)
├── cad_models/
│   ├── inmov_base/ (downloaded models)
│   ├── custom_parts/ (your modifications)
│   └── assembly_guides/ (instructions)
└── research/
    └── resources.md (links & references)
```

---

## Key Decisions to Make (Phase 0)

### 1. Hardware Platform
- [ ] Servo motors: MG996R or upgrade?
- [ ] Power: LiPo batteries or AC PSU?
- [ ] Microcontroller: Arduino, STM32, or Raspberry Pi?
- [ ] Communication: Serial UART or CAN bus?

### 2. Software Stack
- [ ] Primary: Python (recommended)
- [ ] Embedded: Arduino IDE or STM32CubeIDE?
- [ ] Simulation: Gazebo/RViz? (optional but helpful)
- [ ] ROS: Use ROS 2 framework? (later phases)

### 3. Project Scope (MVP)
- [ ] Start with arm only or full body?
- [ ] How many motors in Phase 2?
- [ ] Which animations are priority?
- [ ] Timeline: 1 year? 2 years?

---

## Tools You'll Need

### Free & Recommended
- **Python**: Download from python.org
- **Blender**: For 3D models & animation (https://blender.org/)
- **VS Code**: Code editor (https://code.microsoft.com/)
- **Git**: Version control
- **Arduino IDE**: If using Arduino-compatible boards

### Optional (Later Phases)
- **Gazebo**: Physics simulation
- **RViz**: Visualization
- **CAD Software**: FreeCAD (free) or Fusion 360 (free for students)

---

## First Week Checklist

### By End of Week 1, Complete:

- [ ] Read through [docs/project_plan.md](docs/project_plan.md)
- [ ] Watch InMoov introduction video (https://inmoov.fr/)
- [ ] Sketch preliminary design (arm positions, workspace)
- [ ] Create GitHub repository (optional but recommended)
- [ ] Join robotics communities (Reddit r/robotics, GitHub discussions)

### By End of Week 2, Complete:

- [ ] Deep-dive into servo motor options
- [ ] Analyze Elden Ring skeleton (document bone names, ranges)
- [ ] Draft kinematics for 1 arm (4 joints)
- [ ] Simulate IK in Python (if comfortable with coding)
- [ ] Create first hardware prototype plan

---

## Getting Help

### Debugging Tools
- Print statements and logging (Python)
- Multimeter (circuit debugging)
- RViz visualization (kinematics validation)

### Communities
- **GitHub**: Post issues, ask questions in discussions
- **Stack Overflow**: Programming questions
- **Reddit r/robotics**: General robotics help
- **InMoov forums**: Platform-specific questions

### Documentation
- Revisit [research/resources.md](research/resources.md) for courses & papers
- InMoov official guides: https://github.com/InMoov/InMoov
- Robotics textbooks (see resources.md)

---

## Milestones

| Phase | Goal | Timeline |
|-------|------|----------|
| **Phase 0** (NOW) | Complete hardware research & architecture design | Weeks 1-8 |
| **Phase 1** | Print parts & assemble base robot | Weeks 9-20 |
| **Phase 2** | Motor control & feedback loops working | Weeks 21-28 |
| **Phase 3** | Robot standing & walking (basic) | Weeks 29-40 |
| **Phase 4** | Animation playback (Elden Ring!) | Weeks 41-56 |
| **Phase 5+** | Vision & autonomous movement | Weeks 57+ |

---

## Tips for Success

1. **Start small**: Prototype with 1-2 motors before committing to 20
2. **Simulate first**: Test kinematics in code before hardware
3. **Document everything**: Future you will thank present you
4. **Test incrementally**: Each phase builds on previous
5. **Join communities**: Other roboticists have solved problems you'll face
6. **Budget for failures**: Expect 10-20% component failures; plan accordingly
7. **Version control**: Use Git from day 1

---

## Next Steps

1. **Today**: Read through README.md and project_plan.md
2. **This Week**: Review InMoov platform and hardware BOM
3. **Next Week**: Start researching servo motors and animation extraction
4. **In 2 weeks**: Make final hardware selections and begin Phase 1

---

**Happy building! 🤖**

Last Updated: April 2026

