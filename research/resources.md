# Research & Resources - Project MT

## Official InMoov Resources

### Primary Sources
- **InMoov Official Website**: https://inmoov.fr/
- **GitHub Repository**: https://github.com/InMoov/InMoov
- **Community Forums**: https://github.com/InMoov/InMoov/discussions
- **3D Model Library**: https://www.thingiverse.com/search?q=inmoov&type=things&sort=relevant

### Key InMoov Documentation
- InMoov Design Principles & Constraints
- Servo Specifications & Joint Ranges
- Assembly Guides & CAD Models
- Control Software Architecture (Java-based, will be replaced)

---

## Robotics Theory & Mathematics

### Kinematics Resources
- **Forward Kinematics (FK)**: Denavit-Hartenberg Convention
  - Reference: Introduction to Robotics by Craig (textbook, comprehensive)
  - Online: https://www.youtube.com/results?search_query=denavit+hartenberg
  
- **Inverse Kinematics (IK)**: Numerical Solutions
  - Jacobian-based methods
  - Cyclical Coordinate Descent (CCD)
  - FABRIK (Forward And Backward Reaching IK)
  - References: Buss & Kim (FABRIK paper), UrdfFast library

### Dynamics & Control
- **Bipedal Walking**: Center of Pressure, Zero-Moment Point
  - Reference: "Bipedal Robotics" by Grizzle et al.
  - Online courses: MIT OpenCourseWare (Humanoid Robotics)

- **PID Control**: Feedback loops for motor control
  - Reference: "Control Systems Engineering" by Nise
  - Practical tuning: Ziegler-Nichols method

### Balance & Stability
- IMU (Inertial Measurement Unit) integration
- Complementary filters for sensor fusion
- Fall detection and recovery

---

## Game Animation Resources

### Animation Extraction Tools
- **Blender FBX Import**: Standard 3D animation format
- **Modding Communities**:
  - Elden Ring: https://www.nexusmods.com/eldenring
  - FromSoftware modding community (various forums)
  - Skeleton data extraction from game files
  
- **Animation Formats**:
  - FBX (Autodesk) - most common game format
  - GLTF/GLB (Khronos) - modern, lightweight
  - Proprietary formats (require reverse engineering)

### Animation Analysis
- Bone hierarchy mapping (game skeleton → robot skeleton)
- Keyframe data extraction
- Motion capture data preparation
- Animation blending techniques

---

## Software & Programming

### Python Libraries (Recommended)
```python
NumPy                # Numerical computations, matrices
SciPy                # Scientific computing, IK solvers
OpenCV               # Computer vision
PySerial             # Serial communication with microcontroller
Blender (Python API) # Animation/3D model processing
Matplotlib           # Plotting and visualization
```

### Microcontroller Frameworks
- **STM32CubeIDE**: STM32 development (C/C++)
- **Arduino IDE**: Arduino-compatible boards
- **PlatformIO**: Multi-platform embedded development

### ROS 2 (Optional, for future expansion)
- Robot Operating System 2
- Package-based architecture
- Middleware for multi-robot systems
- Simulation integration (Gazebo)

### Simulation Platforms
- **Gazebo**: Physics engine + robotics simulation
- **RViz**: 3D visualization of robot and sensor data
- **URDF**: Unified Robot Description Format (XML-based)

---

## Computer Vision

### Object Detection & Pose Estimation
- **OpenCV**: Traditional computer vision
- **MediaPipe**: ML-based pose detection (human pose transfer)
- **YOLOv8**: Real-time object detection
- **Deep Learning**: PyTorch, TensorFlow for custom models

### Motion Capture Alternatives
- Optical motion capture (expensive, professional)
- Markerless motion capture (MediaPipe, OpenPose)
- Depth cameras (RealSense, Kinect)

---

## Hardware & Prototyping

### Servo Motors (Recommended Brands)
- **MG996R**: Standard high-torque servo, widely available
- **Futaba**: Premium quality, expensive
- **Tower Pro**: Budget option (less reliable)
- **Custom brushless**: High performance, complex control

### Power Systems
- **LiPo Batteries**: Standard for robotics (3S, 4S common)
- **NiMH**: Older alternative, heavier
- **LiFePO4**: Safer but heavier than LiPo

### Microcontroller Comparison
| Platform | Pros | Cons | Cost |
|----------|------|------|------|
| Arduino | Beginner-friendly, large community | Slower, limited memory | $15-30 |
| STM32F4 | Fast, real-time capable | Steeper learning curve | $20-40 |
| Raspberry Pi | Powerful, Linux OS | Overkill for Phase 2-3 | $35-75 |

---

## Learning Resources

### Online Courses
- **edX - "Robot Mechanics and Control"**: MIT (free)
- **Coursera - "Robotics"**: University of Pennsylvania
- **YouTube Channels**:
  - Robotics Back-end (kinematics tutorials)
  - Paul McWhorter (Arduino basics)
  - MIT OpenCourseWare (Robotics lectures)

### Books
- "Introduction to Robotics" by John J. Craig (classic, comprehensive)
- "Robotics: Modelling, Planning and Control" by Siciliano et al.
- "Humanoid Robots" by Goswami & Vadakkepat (specialized)
- "Real-Time Collision Detection" by Christer Ericson (for motion planning)

### Research Papers
- FABRIK algorithm: Buss & Kim (2004)
- Zero-Moment Point (ZMP): Vukobratovic & Borovac (2004)
- Bipedal gait generation: Grizzle et al. (2001)

---

## Community & Forums

- **Stack Overflow**: Programming questions
- **ROS Answers**: ROS-specific questions
- **GitHub Issues**: Component-specific help
- **Reddit**:
  - r/robotics
  - r/learnprogramming
  - r/3Dprinting

---

## Tools & Software Recommendations

### Phase 0-1 (Planning)
- [ ] Blender (3D modeling, animation preview)
- [ ] Python environment (Anaconda or venv)
- [ ] Git (version control)
- [ ] Jupyter Notebook (prototyping kinematics)

### Phase 2-3 (Development)
- [ ] STM32CubeIDE or Arduino IDE (firmware)
- [ ] VS Code (Python development)
- [ ] GitKraken (version control GUI)
- [ ] Gazebo + RViz (optional simulation)

### Phase 4-5 (Advanced)
- [ ] ROS 2 (multi-node architecture)
- [ ] OpenCV (vision processing)
- [ ] Machine learning frameworks (if autonomous movement)

---

## Known Challenges & Solutions

| Challenge | Root Cause | Solution |
|-----------|-----------|----------|
| Servo jitter | Electrical noise on power rail | Add capacitors, filter power |
| Latency in animation | Serial communication bottleneck | Optimize protocol or use CAN |
| IK singularities | Math, not hardware | Pre-plan motions, use damping |
| Poor balance | Incorrect CoM model | Calibrate with IMU feedback |
| Motor burnout | Continuous high torque | Monitor temperature, limit duty cycle |

---

## Next Steps

1. **Week 1**: Review InMoov platform in detail
2. **Week 2**: Analyze Elden Ring animation skeleton
3. **Week 3**: Deep-dive into inverse kinematics (implement in simulation)
4. **Week 4**: Finalize hardware selections and procurement

---

## Bookmark This Section!

Return here to add discovered resources, tools, papers, and community links as the project progresses.

Last updated: April 2026

