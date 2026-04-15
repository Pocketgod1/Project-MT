# System Architecture - Project MT

## High-Level Overview

```
┌─────────────────────────────────────────────────────────────┐
│                   ANIMATION LAYER                            │
│  (Game extraction, parsing, skeleton mapping)                │
└──────────────┬──────────────────────────────────────────────┘
               │
┌──────────────▼──────────────────────────────────────────────┐
│              KINEMATICS LAYER                                │
│  (IK/FK calculations, joint trajectory planning)             │
└──────────────┬──────────────────────────────────────────────┘
               │
┌──────────────▼──────────────────────────────────────────────┐
│           CONTROL SYSTEM LAYER                               │
│  (PID loops, motor commands, feedback processing)            │
└──────────────┬──────────────────────────────────────────────┘
               │
┌──────────────▼──────────────────────────────────────────────┐
│          HARDWARE INTERFACE LAYER                            │
│  (Serial/CAN communication, low-level drivers)               │
└──────────────┬──────────────────────────────────────────────┘
               │
┌──────────────▼──────────────────────────────────────────────┐
│              PHYSICAL ROBOT                                  │
│  (Motors, sensors, mechanical structure)                     │
└────────────────────────────────────────────────────────────┘
```

## Detailed Component Breakdown

### 1. Animation Layer
**Purpose**: Extract, parse, and map game animations to robot movement

**Components**:
- `animation_extractor`: Converts game animation files to standardized format
- `skeleton_mapper`: Maps game skeleton to robot DOF structure
- `animation_player`: Queues and plays back animation sequences
- `animation_blender`: Smoothly transitions between animations

**Input**: FBX/GLTF animation files from games  
**Output**: Joint angle trajectories over time  
**Update Rate**: Event-driven (animation changes)  

### 2. Kinematics Layer
**Purpose**: Convert animation target positions to joint angles

**Components**:
- `forward_kinematics`: Compute end-effector position from joint angles
- `inverse_kinematics`: Solve joint angles from target end-effector position
- `trajectory_planner`: Generate smooth joint trajectories
- `collision_checker`: Validate motion feasibility

**Key Challenge**: Real-time IK solving while respecting joint limits  
**Update Rate**: 50-100 Hz  

### 3. Control System Layer
**Purpose**: Command motors to reach target angles

**Components**:
- `pid_controller`: Individual joint PID loops
- `state_machine`: Robot operating states (idle, moving, animating, emergency)
- `feedback_processor`: Read and filter sensor data
- `safety_monitor`: Check power, temperature, torque limits

**Update Rate**: 50-200 Hz (real-time control loop)  

### 4. Hardware Interface Layer
**Purpose**: Communicate with physical hardware

**Components**:
- `serial_interface`: UART/CAN communication with motor drivers
- `sensor_interface`: Read IMU, potentiometers, load cells
- `motor_driver`: Command format generation and CRC
- `firmware`: Embedded C/C++ code running on microcontroller

**Hardware**: Microcontroller (STM32F4, Arduino Due, or Raspberry Pi)  
**Communication Protocol**: Custom serial protocol or CAN bus  

---

## Data Flow Example: Simple Animation Playback

```
Game Animation (Elden Ring - slash attack)
    │
    ▼
[Animation Extractor]
Skeleton: {rightArm: [0°, 30°, 45°, 90°], leftArm: [5°, 0°, 0°, 0°], ...}
    │
    ▼
[Skeleton Mapper]
Map to robot (game bone → robot joint)
    │
    ▼
[IK Solver]
Frame N: target positions → joint angles
Frame N+1: target positions → joint angles
    │
    ▼
[Trajectory Planner]
Smooth interpolation between frames (50ms intervals)
    │
    ▼
[Motor Controller] (50ms loop)
Set PID targets for each joint
Monitor feedback, adjust in real-time
    │
    ▼
Physical Motors Move
    │
    ▼
Sensors Feedback (position, load)
Back to controller for next cycle
```

---

## Concurrency & Real-Time Constraints

### Main Control Loop (50-200 Hz)
**Priority**: CRITICAL (must never miss deadline)
- Read sensor feedback
- Update PID controllers
- Command motors
- Emergency stop check

### Animation Playback Loop (50 Hz)
**Priority**: HIGH
- Update current animation frame
- Queue next IK target

### Background Tasks (non-real-time)
**Priority**: LOW
- Logging and diagnostics
- Communication with external systems
- Trajectory pre-computation

---

## Software Technology Stack

### Host Computer (High-level Control)
- **Language**: Python 3.8+
- **Libraries**: NumPy (math), OpenCV (vision), PySerial (communication)
- **Optional**: ROS 2 for larger system integration

### Microcontroller (Motor Control)
- **Language**: C/C++
- **Framework**: STM32CubeIDE or Arduino IDE
- **Real-time Requirements**: Deterministic control loop

### Simulation Environment (Optional but Recommended)
- **Gazebo**: Physics simulation
- **RViz**: 3D visualization
- **URDF**: Robot model definition

---

## Safety Architecture

### Multi-Layer Safety

1. **Software Watchdog**: 
   - Microcontroller watchdog timer (100ms timeout)
   - Host sends heartbeat every 50ms
   - Loss of signal → halt all motors

2. **Hardware Limits**:
   - Joint mechanical stops (prevent over-rotation)
   - Current limits on motor drivers
   - Thermal cutoffs

3. **Feedback Monitoring**:
   - Torque sensing detects collisions
   - Position feedback detects joint slipping
   - IMU detects abnormal acceleration (falling)

4. **Emergency Stop**:
   - Physical E-stop button (hard-wired)
   - Software emergency command
   - Loss of communication → safe state

---

## Power Distribution

```
Battery Pack
    │
    ├──→ [Main Breaker]
    │
    ├──→ [Power Distribution Board]
    │
    ├──→ Motor Power Rail (24V)
    │    ├──→ [Motor Driver 1] → Motors 1-6
    │    ├──→ [Motor Driver 2] → Motors 7-12
    │    └──→ [Motor Driver 3] → Motors 13-18
    │
    ├──→ Logic Power Rail (5V)
    │    ├──→ [Microcontroller]
    │    ├──→ [Sensors]
    │    └──→ [Communication Module]
    │
    └──→ [Power Monitor]
         └──→ Reports to microcontroller
```

---

## Scaling Considerations

### Phase 0-2: Simple Serial Protocol
- Single microcontroller
- Point-to-point communication
- Suitable for < 20 motors

### Phase 3-4: Multi-Node Architecture
- Multiple local controllers (one per limb)
- Communication between nodes
- Handles > 30 motors

### Phase 5+: Distributed System
- ROS 2 middleware
- Separation of real-time and non-real-time tasks
- Support for multiple computers

---

## Dependency Graph

```
Animation Layer (Phase 4)
    ↓ depends on
Kinematics Layer (Phase 3)
    ↓ depends on
Control System Layer (Phase 2)
    ↓ depends on
Hardware Interface (Phase 2)
    ↓ depends on
Physical Hardware (Phase 1)
    ↓ depends on
System Architecture ← (YOU ARE HERE)
```

---

## Next Steps

1. Define communication protocol (serial format)
2. Select microcontroller platform
3. Determine motor driver requirements
4. Create URDF model for simulation
5. Prototype kinematics in simulation first

