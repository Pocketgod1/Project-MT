# Cosplay Humanoid Robot

> A fully 3D-printed, servo-driven humanoid robot built for cosplay competition performance — capable of executing choreographed movement sequences derived from video game animation data.

<!-- Replace the line below with an actual demo video thumbnail once you have footage -->
<!-- [![Demo video](https://img.youtube.com/vi/YOUR_VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID) -->

---

## What this is

A ground-up humanoid robot build combining:

- **3D printed structural frame** — custom-designed joints, limbs, and torso optimized for PETG printing on a standard FDM printer
- **Servo-driven motion system** — [N] degrees of freedom across arms, shoulders, wrists, and [other joints as you add them]
- **Performance sequencer** — scripted movement timelines synchronized to audio, triggered for live cosplay competition routines
- **Game animation pipeline** — a custom Python tool that extracts enemy movesets from game BVH animation data and retargets them to the robot's joint structure

The long-term goal is a full human-sized wearable/standalone robot platform that can perform a scripted routine at cosplay competitions — think Malenia from Elden Ring, but physical.

---

## Current build status

| Module | Status | Notes |
|---|---|---|
| EEZYbotARM MK2 | ✅ Complete | Starter arm, all servos working |
| Custom shoulder assembly | 🔧 In progress | Printing v3 of joint housing |
| InMoov hand/wrist | 🔧 In progress | Individual finger control |
| Torso frame | 📐 Designing | |
| Leg structure | 📐 Designing | |
| ROS 2 integration | 🔧 In progress | Basic joint control working |
| Performance sequencer | ✅ v1 complete | See `/software/performance_sequencer` |
| Game animation pipeline | ✅ Complete | See [game-anim-to-robot](https://github.com/yourusername/game-anim-to-robot) |

---

## Hardware

### Bill of materials (current phase)

| Part | Qty | Approx. cost |
|---|---|---|
| MG996R servo (main joints) | 12 | ~$35 |
| SG90 micro servo (fingers/wrist) | 8 | ~$15 |
| PCA9685 16-channel servo driver | 2 | ~$20 |
| Raspberry Pi 5 (main controller) | 1 | ~$70 |
| Arduino Mega (low-level servo I/O) | 1 | ~$40 |
| PETG filament (1kg spools) | ~6 | ~$120 |
| M3/M4 hardware assortment | — | ~$20 |
| 6V 10A power supply | 1 | ~$25 |
| IMU (MPU-6050) | 1 | ~$8 |

Full BOM with suppliers and alternatives: [`docs/bom.md`](docs/bom.md)

### Print settings (PETG)

```
Layer height:   0.2mm
Perimeters:     4
Infill:         45% gyroid
Nozzle temp:    235–240°C
Bed temp:       80–85°C
Fan:            30–50%
Supports:       Organic/tree on overhangs
```

All STL files are in [`hardware/stl/`](hardware/stl/). Source CAD files (Fusion 360 / Blender) are in [`hardware/cad/`](hardware/cad/).

---

## Software

### Repo structure

```
software/
├── ros2_ws/                   # ROS 2 workspace
│   └── src/
│       ├── humanoid_control/  # Main robot control package
│       ├── joint_trajectory/  # Joint trajectory execution
│       └── performance/       # Performance sequence player
├── firmware/
│   └── servo_controller/      # Arduino servo I/O sketches
├── bvh_to_servo.py            # Game animation converter
└── performance_sequencer/     # Timeline + audio sync tool
```

### Dependencies

```bash
# ROS 2 (Humble or later)
sudo apt install ros-humble-desktop

# Python dependencies
pip install numpy scipy blender-python-api

# Arduino libraries
# - Servo.h (built-in)
# - Adafruit_PWMServoDriver
```

### Running the performance sequencer

```bash
# Convert a BVH animation to servo commands
python bvh_to_servo.py --input animation.bvh --dof 6 --format json --output sequence.json

# Play a sequence on the robot via ROS 2
ros2 run performance play_sequence --file sequence.json --speed 0.8
```

### Game animation pipeline

The full BVH extraction and retargeting workflow lives in its own repo:
**[game-anim-to-robot](https://github.com/yourusername/game-anim-to-robot)**

Short version:
1. Extract `.hkx` files from game using **UXM / Yabber**
2. Convert to `.fbx` using **HKX2FBX**
3. Import into **Blender**, retarget to robot skeleton
4. Export as `.bvh`
5. Run `bvh_to_servo.py` → servo command CSV/JSON/Arduino header

---

## Build log

The full build journal with photos, failures, and design decisions is in [`docs/build-log.md`](docs/build-log.md).

Selected entries:

- [2025-XX-XX — First servo linkage test, joint binding issue and fix](docs/build-log.md)
- [2025-XX-XX — PETG warping on shoulder housing, print orientation solution](docs/build-log.md)
- [2025-XX-XX — ROS 2 + PCA9685 first successful multi-joint move](docs/build-log.md)

*(Update these as you go — dated entries with photos are the most valuable part of this repo)*

---

## Inspiration and references

- [InMoov](https://inmoov.fr) — open-source 3D printed humanoid, community and design reference
- [EEZYbotARM MK2](https://www.thingiverse.com/thing:1454048) — starter arm build
- [AR2/AR3](https://github.com/Chris-Annin/AR2) — 6-DOF arm design reference
- [ROS 2 documentation](https://docs.ros.org/en/humble/)
- [MoveIt 2](https://moveit.ros.org) — motion planning

---

## About this project

Self-taught builder — background in 3D printing, CAD modeling, and programming. No formal robotics education. This project is the education.

**Goal:** Enter a cosplay competition with a humanoid robot performing a choreographed routine from an Elden Ring enemy moveset.

**Timeline:** Ongoing. Started [your start date here].

Follow the build: [YouTube / blog / social link here]

---

## License

Hardware designs (STL, CAD): [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
Software: [MIT](LICENSE)
