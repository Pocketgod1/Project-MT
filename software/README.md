# Software Development Guide

## Setup & Environment

### Python Environment

**Prerequisites**:
- Python 3.8 or higher
- pip (package manager)

**Create Virtual Environment**:

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

**Install Core Dependencies**:

```bash
pip install numpy scipy matplotlib opencv-python pyserial
```

### Microcontroller Development

**Arduino IDE** (if using Arduino-compatible boards):
- Download: https://www.arduino.cc/en/software
- Install STM32 core (if using STM32 board)

**STM32CubeIDE** (if using STM32 microcontroller):
- Download: https://www.st.com/en/development-tools/stm32cubeide.html

---

## Code Organization

### kinematics/
**Purpose**: Forward and inverse kinematics solvers

```
kinematics/
├── __init__.py
├── forward_kinematics.py     # FK computations
├── inverse_kinematics.py     # FABRIK IK solver
├── trajectory_planner.py     # Smooth motion generation
├── collision_checker.py      # Workspace validation
└── tests/
    └── test_kinematics.py
```

### control_system/
**Purpose**: Motor control and feedback loops

```
control_system/
├── __init__.py
├── pid_controller.py         # PID loops for each joint
├── motor_interface.py        # Motor driver communication
├── state_machine.py          # Robot operating states
├── safety_monitor.py         # Safety checks
└── calibration.py            # Calibration utilities
```

### animation/
**Purpose**: Game animation processing

```
animation/
├── __init__.py
├── animation_parser.py       # FBX/GLTF parsing
├── skeleton_mapper.py        # Game→Robot mapping
├── animation_player.py       # Playback engine
└── blend_animations.py       # Animation blending
```

### firmware/
**Purpose**: Embedded microcontroller code (C/C++)

```
firmware/
├── main.c                    # Entry point
├── motor_driver.h/.c         # Motor control
├── uart_interface.h/.c       # Serial communication
├── pid_controller.h/.c       # PID implementation
├── sensor_interface.h/.c     # Sensor reading
└── safety.h/.c               # Watchdog & safety
```

---

## Example: Running Your First Kinematics Test

### 1. Create kinematics/forward_kinematics.py

```python
import numpy as np

class ForwardKinematics:
    def __init__(self, dh_params):
        """
        dh_params: List of (a, alpha, d, theta_min, theta_max)
        """
        self.dh_params = dh_params
    
    def compute_transformation(self, theta, dh):
        """Compute DH transformation matrix."""
        a, alpha, d, _, _ = dh
        
        T = np.array([
            [np.cos(theta), -np.sin(theta)*np.cos(alpha), np.sin(theta)*np.sin(alpha), a*np.cos(theta)],
            [np.sin(theta), np.cos(theta)*np.cos(alpha), -np.cos(theta)*np.sin(alpha), a*np.sin(theta)],
            [0, np.sin(alpha), np.cos(alpha), d],
            [0, 0, 0, 1]
        ])
        return T
    
    def forward_kinematics(self, angles):
        """Compute end-effector position from joint angles."""
        T = np.eye(4)
        
        for angle, dh in zip(angles, self.dh_params):
            T_i = self.compute_transformation(angle, dh)
            T = T @ T_i
        
        position = T[0:3, 3]
        return position, T
```

### 2. Create tests/test_kinematics.py

```python
import sys
sys.path.insert(0, '../')

from kinematics.forward_kinematics import ForwardKinematics
import numpy as np

# Example: Simple 2-link arm
# Link 1: length = 1m
# Link 2: length = 0.8m
dh_params = [
    (1.0, 0, 0, -np.pi, np.pi),      # Link 1
    (0.8, 0, 0, -np.pi/2, np.pi/2)  # Link 2
]

fk = ForwardKinematics(dh_params)

# Test 1: Both joints at 0°
angles_1 = [0, 0]
pos_1, T_1 = fk.forward_kinematics(angles_1)
print(f"Config 1 (0°, 0°): End-effector at {pos_1}")
# Expected: [1.8, 0, 0] (both links aligned horizontally)

# Test 2: Joint 1 at 90°, Joint 2 at 0°
angles_2 = [np.pi/2, 0]
pos_2, T_2 = fk.forward_kinematics(angles_2)
print(f"Config 2 (90°, 0°): End-effector at {pos_2}")
# Expected: [0, 1.8, 0] (both links vertical)

# Test 3: Random configuration
angles_3 = [np.pi/4, -np.pi/4]
pos_3, T_3 = fk.forward_kinematics(angles_3)
print(f"Config 3 (45°, -45°): End-effector at {pos_3}")
```

### 3. Run the test

```bash
cd kinematics
python ../tests/test_kinematics.py
```

---

## Development Workflow

### 1. Write Code
```python
# software/kinematics/inverse_kinematics.py
def fabrik_solver(target_pos, chain_lengths, joint_limits):
    # Implement FABRIK
    pass
```

### 2. Write Tests
```python
# software/kinematics/tests/test_ik.py
def test_fabrik_reaches_target():
    target = [1.0, 1.0, 0.0]
    result = fabrik_solver(target, ...)
    assert distance(result[-1], target) < 0.01
```

### 3. Run Tests
```bash
pytest software/kinematics/tests/
```

### 4. Commit
```bash
git add software/kinematics/
git commit -m "Implement FABRIK IK solver"
```

---

## Serial Communication Protocol

### Motor Command Format (50ms cycle)

**Packet Structure**:
```
[START_BYTE][CMD_TYPE][MOTOR_ID][ANGLE_HIGH][ANGLE_LOW][CHECKSUM][END_BYTE]
```

**Example**: Set Motor 1 to 90°
```
[0xAA][0x01][0x01][0x01][0x68][CRC][0xFF]
       Command  ID   Angle (90° = 360 in ticks)
```

### Python Serial Interface

```python
import serial
import struct

class RobotInterface:
    def __init__(self, port='/dev/ttyUSB0', baudrate=115200):
        self.serial = serial.Serial(port, baudrate, timeout=1)
    
    def set_joint_angles(self, angles_dict):
        """
        angles_dict: {'motor_1': 90, 'motor_2': 45, ...} (in degrees)
        """
        for motor_id, angle_deg in angles_dict.items():
            # Convert degrees to motor ticks (0-255)
            ticks = int(angle_deg * 255 / 180)
            
            # Build packet
            packet = bytearray([
                0xAA,  # START
                0x01,  # SET_ANGLE command
                motor_id,
                ticks,
                0x00,  # Checksum placeholder
                0xFF   # END
            ])
            
            # Calculate checksum
            packet[4] = sum(packet[1:4]) & 0xFF
            
            self.serial.write(packet)
            response = self.serial.read(1)
            if response != b'\x06':  # ACK
                print(f"No ACK for motor {motor_id}")
```

---

## Continuous Integration

### .github/workflows/test.yml

```yaml
name: Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.8
      - run: pip install -r requirements.txt
      - run: pytest software/*/tests/
```

---

## Documentation Standards

### Docstring Format

```python
def fabrik_solver(target_pos, chain_lengths, max_iterations=10):
    """
    Solve inverse kinematics using FABRIK algorithm.
    
    Args:
        target_pos (list): Target end-effector position [x, y, z]
        chain_lengths (list): Distance between joints [l1, l2, l3, ...]
        max_iterations (int): Maximum solver iterations (default: 10)
    
    Returns:
        list: Joint angles that reach target_pos
    
    Raises:
        ValueError: If target is unreachable
    
    Example:
        >>> angles = fabrik_solver([1.0, 0.5, 0.0], [1.0, 0.8])
        >>> print(angles)
        [1.234, -0.567]
    """
```

---

## Performance Profiling

### Profile Kinematics

```python
import cProfile
import pstats

def profile_ik_solver():
    # Warm up
    for _ in range(100):
        fabrik_solver([1, 1, 0], [1, 1])
    
    # Profile
    pr = cProfile.Profile()
    pr.enable()
    
    for _ in range(1000):
        fabrik_solver([1, 1, 0], [1, 1])
    
    pr.disable()
    ps = pstats.Stats(pr)
    ps.sort_stats('cumulative')
    ps.print_stats(10)  # Top 10 functions
```

---

## Debugging Tips

### Use Logging

```python
import logging

logging.basicConfig(level=logging.DEBUG)
logger = logging.getLogger(__name__)

def fabrik_solver(target):
    logger.debug(f"Solving IK for target: {target}")
    logger.info(f"Iteration 5: error = {error:.4f}")
    logger.warning(f"Joint 2 approaching limit: {angle:.1f}°")
```

### Visualization

```python
import matplotlib.pyplot as plt

def plot_trajectory(joints_over_time):
    for joint_id, angles in joints_over_time.items():
        plt.plot(angles, label=f'Joint {joint_id}')
    plt.legend()
    plt.xlabel('Time (frames)')
    plt.ylabel('Angle (degrees)')
    plt.show()
```

---

## Next Steps

1. Set up Python virtual environment
2. Create skeleton of software/kinematics/
3. Implement simple FK solver
4. Write and run tests
5. Progress to IK solver

