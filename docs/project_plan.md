# Project MT - Detailed Project Plan

## Executive Summary

Build a human-sized, bipedal humanoid robot capable of autonomously replicating animation sequences from video games. The project leverages the InMoov open-source platform as a mechanical foundation and will require custom control systems for animation playback.

## Phase 0: Planning & Research (Weeks 1-8)

### 0.1 InMoov Framework Analysis
- Study InMoov's design philosophy and mechanical constraints
- Document servo requirements (type, torque, response time)
- Analyze joint ranges of motion
- Identify customization points for animation capabilities

### 0.2 Game Animation Analysis
- Extract animations from Elden Ring (via modding community tools)
- Analyze skeleton structure and bone hierarchies
- Document movement velocity and acceleration profiles
- Identify animation primitives (idle, walk, attack, dodge)

### 0.3 Hardware Component Selection
- **Motors**: Research servo motors, stepper motors, brushless DC options
- **Power**: Calculate power requirements, select batteries/PSU
- **Controllers**: Compare microcontrollers (Arduino, STM32, Raspberry Pi)
- **Sensors**: Inertial Measurement Units (IMUs), potentiometers, load cells
- **Actuators**: Pneumatic vs. electric trade-off analysis

### 0.4 System Architecture Design
- **Software Stack**: Define layers (animation → kinematics → motor control)
- **Communication Protocol**: Serial, CAN bus, or wireless options
- **Real-time Requirements**: Determine control loop frequency
- **State Machine**: Design robot states (idle, moving, animating, emergency stop)

### 0.5 Kinematics Calculations
- Develop forward kinematics (joint angles → end-effector position)
- Develop inverse kinematics (target position → joint angles)
- Validate against InMoov DOF constraints
- Prepare simulation environment

**Deliverables**: 
- BOM (Bill of Materials) with estimated costs
- System architecture diagram
- Kinematics documentation (math + code)
- Research summary report

---

## Phase 1: Hardware Foundation (Weeks 9-24)

### Phase 1A: HAND MECHANISM (Weeks 9-12) ⭐ CURRENTLY ACTIVE

**Starting April 15, 2026 - Focus on finger mechanism**

### 1.1a Component Procurement - Hand Parts
- ✅ Ordered: 10x HK15298B servos (€180)
- ✅ Ordered: 2x MG996R servos (€22)
- ✅ Ordered: 0.8mm braided fishing line (€10)
- ✅ Ordered: Extension springs x10 (€5)
- ✅ Ordered: Fasteners - bolts, screws (€15)
- ✅ Ordered: 1.5kg ABS filament natural (€70)
- **Subtotal**: €302 for hand mechanism

### 1.2a 3D Model Customization - Hand
- Download InMoov hand/finger CAD files (free from GitHub)
- Verify servo mounting holes match HK15298B specifications
- Check tendon routing paths in finger mechanism
- Review joint ranges for 0-90° servo rotation

### 1.3a 3D Printing - Hand Parts
- Print finger components (phalanges, metacarpals)
- Print palm and finger structures
- Estimated print time: 40-60 hours
- Total filament: ~1.5kg per hand

### 1.4a Motor Testing - Hand Servos
- Test each HK15298B servo individually
  - Verify 20kg torque at 6V
  - Check 90° rotation range
  - Listen for noise (should be quiet)
- Test MG996R wrist servos
  - Verify 180° rotation
  - Check for noise or binding
- Document operating characteristics

### 1.5a Assembly - Hand Mechanism
- Mount servos in 3D-printed housing
- Route tendons (fishing line) through fingers
- Install return springs for finger opening
- Calibrate servo min/max positions in software
- Test finger flexion/extension
- Build left hand, then right hand

**Deliverables - Phase 1A**:
- ✅ Fully functional hand mechanism (left + right, if desired)
- ✅ Tested servos with calibration profiles
- ✅ Tendon routing documentation
- ✅ Assembly guide for hand mechanism
- ✅ Video demo of finger movement

---

### Phase 1B: ARM PREPARATION (Weeks 13-20)

After hand success, proceed to arm mechanism

### 1.1b Component Procurement - Arm Parts
- Order: 8x Hitec HS805BB servos (€240)
- Order: Servo mounting hardware
- Order: Power distribution board components

### 1.2b 3D Model Customization - Arm
- Download InMoov arm/shoulder CAD files
- Verify servo mounting for HS805BB
- Check load calculations (8 servos + hand weight)

### 1.3b 3D Printing - Arm Parts
- Print bicep, forearm, shoulder structures
- Estimated print time: 40-60 hours
- Total filament: ~1.5kg per arm

### 1.4b Motor Testing - Arm Servos
- Test 8x Hitec HS805BB servos
- Verify 27.5kg torque at 6V
- Check 180° rotation
- Document thermal characteristics

### 1.5b Assembly & Integration
- Mount arm servos in housing
- Attach hand to arm assembly
- Test arm + hand coordination
- Build left arm, then right arm

**Deliverables - Phase 1B**:
- ✅ Fully functional arm mechanism (left + right)
- ✅ Arm + hand integration tested
- ✅ Assembly guide for arm mechanism

---

## OLD PHASE 1 SCHEDULE (For Reference)

### 1.1 Component Procurement
- ✅ Order 3D printer materials (if not already printing) - ABS confirmed
- ⏳ Purchase all motors, servos, and controllers (in progress)
- ⏳ Acquire power systems and distribution boards (Phase 1b)
- ⏳ Gather tools (soldering, crimping, digital multimeter) (Phase 2)

### 1.2 3D Model Customization
- Download InMoov base models (available on GitHub)
- Identify required modifications for motor mounting
- Customize joint interfaces for selected servos
- Document print time and material estimates

### 1.3 3D Printing
- Print major components (torso, limbs, head frame)
- Estimate total print time: 200-500+ hours
- Organize printing schedule
- Store and organize printed parts

### 1.4 Motor & Servo Testing
- Individual motor characterization (speed, torque, power draw)
- Response time testing under load
- Thermal testing under continuous operation
- Document operating curves

### 1.5 Power System Design
- Calculate total power draw (sum of all motors at peak)
- Select battery chemistry and capacity
- Design power distribution board
- Implement emergency shutdown mechanism

**Deliverables**:
- Printed and organized mechanical components
- Tested and characterized motors/servos
- Power distribution schematic
- Assembly guide for base robot

---

## Phase 2: Basic Control System (Weeks 21-28)

### 2.1 Motor Drivers & Control Boards
- Set up microcontroller development environment
- Program motor driver interfaces
- Establish serial communication protocol
- Create diagnostic tools for motor testing

### 2.2 Serial Communication Framework
- Define command format (e.g., joint angles in 50ms cycles)
- Implement error checking and watchdog timers
- Create logging system for debugging
- Test latency and reliability

### 2.3 Individual Joint Control
- Implement PID controllers for each joint
- Calibrate gain constants through testing
- Add position feedback (potentiometers or encoders)
- Test stability and responsiveness

### 2.4 Calibration Utilities
- Home position calibration routine
- Range-of-motion verification
- Temperature and power monitoring
- Create calibration profile storage

**Deliverables**:
- Functional motor control firmware
- PC-based control software (Python)
- Calibration toolkit
- First successful motor movement demo

---

## Phase 3: Kinematics & Movement (Weeks 29-40)

### 3.1 Inverse Kinematics Implementation
- Code IK solver for each limb
- Implement numerically (iterative methods)
- Handle singularities and joint limits
- Optimize for real-time performance

### 3.2 Forward Kinematics Testing
- Validate FK model against actual robot measurements
- Create visualization tools (3D model overlay)
- Test accuracy across workspace

### 3.3 Balance Algorithms
- Implement center-of-mass (CoM) tracking
- Design balance feedback loop using IMU
- Develop emergency stability recovery

### 3.4 Bipedal Walking (Static → Dynamic)
- Start with statically stable walking (always 3+ points of contact)
- Implement simple gait patterns (straight line)
- Gradually increase walking speed
- Add directional changes and turning

**Deliverables**:
- Functional IK solver
- Robot standing without external support
- Robot walking in straight line (slow, stable)
- Motion capture videos

---

## Phase 4: Animation Integration (Weeks 41-56)

### 4.1 Game Animation Extraction Tools
- Research and acquire animation export tools for Elden Ring
- Parse animation data (FBX, GLTF, or custom formats)
- Extract bone hierarchies and keyframes

### 4.2 Animation Format Parsing
- Decode animation file formats
- Convert frame data to time-series
- Implement playback engine

### 4.3 Skeleton Mapping
- Map game skeleton to robot DOF structure
- Handle differences in bone count and ranges
- Implement animation blending for out-of-range movements

### 4.4 Real-Time Animation Playback
- Stream animation keyframes to motor controllers
- Interpolate between keyframes for smooth motion
- Implement speed scaling and animation blending
- Handle emergency stops mid-animation

**Deliverables**:
- Animation extraction toolchain
- Animation playback engine
- Demo of robot performing basic animation sequences
- Performance metrics (latency, smoothness)

---

## Phase 5: AI & Perception (Weeks 57+)

### 5.1 Computer Vision System
- Mount camera(s) on robot
- Integrate OpenCV or MediaPipe for object detection
- Implement environment mapping

### 5.2 Environment Mapping
- Create 3D map of surrounding space
- Identify obstacles and floor surface
- Update map in real-time

### 5.3 Motion Planning Algorithms
- Plan safe paths through environment
- Transition between animations based on obstacles
- Implement collision avoidance

**Deliverables**:
- Real-time environment awareness
- Safe autonomous movement
- Adaptive animation selection based on environment

---

## Risk Mitigation

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Component delays | Schedule slip | Order early, identify substitutes |
| Motor failures | Testing delay | Test thoroughly, maintain spares |
| Mechanical binding | Robot damage | Careful assembly, incremental testing |
| Control latency | Poor animation | Optimize firmware, use real-time OS |
| Power consumption | Reduced runtime | Optimize motion algorithms |
| Complex kinematics | Incorrect motion | Extensive simulation before hardware |

---

## Success Criteria

✓ Robot stands independently without external support  
✓ Robot walks 5+ meters in straight line  
✓ Robot performs 3+ animation sequences smoothly  
✓ Animation playback latency < 100ms  
✓ Battery life > 30 minutes of continuous operation  
✓ Emergency stop responsive (< 200ms to halt)  

---

## Notes

- This timeline assumes 20 hours/week commitment (~1 year)
- 3D printing time is non-blocking; can proceed with other phases
- Simulation work can begin immediately (Phase 0)
- Budget estimate: $3,000 - $8,000 (motors, electronics, materials)

