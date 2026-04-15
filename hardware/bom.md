# Bill of Materials (BOM) - Project MT

## Overview

**Source**: Official InMoov Platform (Updated 04/05/2016)  
**Base Configuration**: Full humanoid robot (head, arms, hands, torso, waist legs TBD)

**Note**: Prices listed are from original BOM (circa 2016). Current market prices will differ. All components are based on the official InMoov project specifications.

---

## Core Computing & Control

| Component | Qty | Model | Specs | Price (2016) | Notes |
|-----------|-----|-------|-------|-------------|-------|
| **Arduino Mega** | 2 | Arduino Mega 2560 | Microcontroller | €40 each (~€80) | Recommended: 1x Uno + 1x Mega; upgrade to 2x Mega if needed |
| **Nervo Board** | 2 | Custom InMoov | Servo multiplexer | Included in kit | I2C servo controller |
| **Arduino Nano** | 1 | Arduino Nano | Microcontroller | €10-15 | Optional: for additional sensors |
| **USB Hub** | 1 | 8-port USB 3.0 | High-speed connectivity | €15-30 | Powers Arduinos, cameras, peripherals |

---

## Servo Motors & Actuators (Official Specifications)

### Hands & Forearms (Left, Right)

| Component | Qty | Model | Torque | Rotation | Price Each | Subtotal | Notes |
|-----------|-----|-------|--------|----------|-----------|----------|-------|
| **Finger Servos** | 10 | HK15298B | 20kg | 90° | €18 | €180 | Best choice for fingers (strong, quiet, reliable) |
| **Wrist Rotation** | 2 | MG996R | 10kg | 180° | €11 | €22 | Rotational wrist movement |
| **Braided Fishing Line** | 1 | 0.8mm, 200LB | - | - | €10 | €10 | Tendon-driven finger mechanism |
| **Extension Springs** | 10 | 0.51mm diameter | - | - | Included | - | Finger return springs (1cm length) |
| **Misc Bolts** | - | M3, M4 hardware | - | - | €10 | €10 | From local hardware store |
| **ABS Filament** | 1.5kg | Natural ABS | - | - | €70 | €70 | 3D printing material |
| **Hands/Forearms Subtotal** | | | | | | **€362** | |

### Arms & Shoulders (Left, Right)

| Component | Qty | Model | Torque | Rotation | Price Each | Subtotal | Notes |
|-----------|-----|-------|--------|----------|-----------|----------|-------|
| **Bicep/Shoulder Servos** | 8 | Hitec HS805BB | 27.5kg | 180° | €30 | €240 | **Recommended**: Get stronger torque if possible (60kg options available) |
| **Misc Bolts** | - | M3, M4 hardware | - | - | €10 | €10 | From local hardware store |
| **ABS Filament** | 1.5kg | Black, Yellow, Natural | - | - | €37 | €37 | 3D printing material |
| **Arms/Shoulders Subtotal** | | | | | | **€287** | |

### Head, Torso & Neck

| Component | Qty | Model | Torque | Rotation | Purpose | Price Each | Subtotal | Notes |
|-----------|-----|-------|--------|----------|---------|-----------|----------|-------|
| **Head Up/Down** | 2 | Hitec HS805BB | 27.5kg | 180° | Head movement | €30 | €60 | Vertical head rotation |
| **Neck Tilting** | 2 | HK15298B | 20kg | 90° | Neck tilt | €18 | €36 | 1 master, 1 slave for synchronization |
| **Jaw Mechanism** | 1 | HK15298B | 20kg | 90° | Jaw opening | €18 | €18 | Mouth movement |
| **Eye Mechanism** | 2 | DS929hvCorona (or similar) | 8-10kg | 90° | Eye movement | €15 | €30 | Horizontal/vertical eye gaze |
| **Stomach (High)** | 2 | Hitec HS805BB | 27.5kg | 180° | Torso flex | €30 | €60 | Upper torso bending |
| **Stomach (Mid)** | 2 | Hitec HS805BB or HK15338 | 25-27kg | 180° | Torso bend | €25-30 | €50-60 | Middle torso bending |
| **Misc Bolts** | - | M3, M4 hardware | - | - | - | €10 | €10 | From hardware store |
| **ABS Filament** | 4kg | Natural ABS | - | - | - | €140 | €140 | 3D printing material (head, torso, neck) |
| **Fishing Line** | 1 | 0.8mm, 200LB | - | - | - | €5 | €5 | Tendons for facial animation |
| **Head/Torso Subtotal** | | | | | | | **€309-319** | |

### Servo Preference Ranking (Per InMoov Designer)

**For Hands:**
1. JX PDI-6221MG (20-36kg torque, 180°, most reliable)
2. JX PDI-6225MG-300 (20-36kg torque, 300°, for advanced hands)
3. **HK15298B** (20kg torque, 90°, InMoov standard)
4. MG996R (10kg torque, 180°, budget option)
5. MG946R (12kg torque, 180°)
6. MG995 (10kg torque, burns easily - avoid)

**For Biceps/Shoulders/Torso:**
- **Hitec HS805BB** (27.5kg torque, 180°, InMoov standard)
- Alternative: JX Servo PDI-HV2060MG (60kg torque - overkill but reliable)
- HK15338 (25kg torque, needs resistors)

**For Eyes:**
- TowerPro SG91
- TowerPro SG92R
- JX PDI-1109MG

---

## Power System

| Component | Qty | Model/Spec | Capacity | Price (2016) | Notes |
|-----------|-----|-----------|----------|------------|-------|
| **Battery Option A** | 1 | 6V 12Ah LiPo | 12Ah | €35 | Primary power + charger (6V 1.5A) |
| **Battery Option B** | 1 | 6V 60A Power Supply | 60A continuous | €40-60 | For all-day operation (recommended) |
| **Battery Charger** | 1 | 6V 1.5A charger | 1.5A | Included | Keeps battery topped up during use |
| **Adjustable DC-DC Converter** | 1 | 5V→6V adjustable | 50A+ | €20-30 | To boost 5V supplies to 6V for servos |
| **Power Distribution Board** | 1 | Custom PCB | Multiple outputs | €15-25 | Distributes power to all subsystems |
| **Emergency Breaker** | 1 | 30A automotive breaker | Safety cutoff | €5-10 | Hard-wired safety mechanism |
| **Power System Subtotal** | | | | | **€115-160** |

---

## Sensors & Vision

| Component | Qty | Model/Option | Specs | Price (2016) | Notes |
|-----------|-----|--------------|-------|-------------|-------|
| **Camera (Choose One)** | 1 | Hercules HD (dismantled) | HD video | €20-30 | Most common choice |
| | 1 | LifeCam 3000 (Microsoft) | HD video | €30-40 | Alternative option |
| | 1 | OAK-D-Lite | Fixed focus, depth | €100+ | Advanced (for Phase 5) |
| **PIR Motion Sensor** | 1 | Retriggered PIR | Motion detection | €5-10 | Room awareness |
| **HC-SRC04** | 2 | Ultrasonic | Distance sensing | €3-5 each | Obstacle detection |
| **Pressure Sensors** | 10 | Finger pressure | Analog input | €2-5 each | Finger force feedback |
| **Sensors Subtotal** | | | | | **€90-150** |

---

## Communication & Cabling

| Component | Qty | Spec | Length | Price (2016) | Notes |
|-----------|-----|------|--------|-------------|-------|
| **Ribbon Cable** | - | Standard | See below | €20-40 | Interconnect distances |
| Nervo board → Neck | 1 | Ribbon | 10cm | - | Head connection |
| Nervo board → Head (Eyes/Jaw) | 1 | Ribbon | 55cm | - | Face control |
| Nervo board → Arm | 1 | Ribbon | 75cm | - | Arm to main board |
| Nervo board → Hand | 1 | Ribbon | 90cm | - | Hand control |
| Nervo board → Finger Sensors | 1 | Ribbon | 120cm | - | Sensor feedback |
| Nervo board → Stomach | 1 | Ribbon | 30cm | - | Torso control |
| **USB Cables** | 5+ | USB-A to USB-B, 3.0 | Standard | €5-15 each | Arduino, hub connectivity |
| **Power Cables** | - | Various gauges | Custom | €10-15 | XT60, XT90, barrel connectors |
| **Cabling Subtotal** | | | | | **€60-100** |

---

## Audio & Multimedia

| Component | Qty | Model/Spec | Specs | Price (2016) | Notes |
|-----------|-----|-----------|-------|-------------|-------|
| **Mini PC Speaker** | 2 | 8Ohm 10W | 10W each | €5-10 each | For audio output |
| **Mini Amplifier** | 1 | 6V | 6V input | €10-15 | Powers speakers |
| **USB Sound Card** | 1 | External USB | Audio I/O | €10-20 | If main computer lacks audio |
| **NeoPixel LED Strips** | 3 | Addressable RGB | Programmable | €5-10 each | Eyes, decorative lighting |
| **Audio/Multimedia Subtotal** | | | | | **€45-90** |

---

## Hardware & Fasteners

| Component | Qty | Size | Purpose | Price (2016) | Notes |
|-----------|-----|------|---------|-------------|-------|
| **Allen Countersunk Bolts** | - | M3x20mm | ~50 units | €5-10 | General fastening |
| | - | M4x20mm | ~50 units | €5-10 | Larger fastening |
| | - | M8x100mm | ~15 units | €5-10 | Heavy-duty mounting |
| **Phillips Flat-Head Wood Screws** | - | M3x12mm | ~100 units | €5-10 | Small servo mounting |
| | - | M4x20mm | ~50 units | €5-10 | Large servo mounting |
| **Miscellaneous Hardware** | 1 | Various | General | €10-20 | Bolts, nuts, washers from local store |
| **Fasteners Subtotal** | | | | | **€35-70** |

---

## 3D Printing Materials

| Component | Qty | Material | Color | Price (2016) | Notes |
|-----------|-----|----------|-------|-------------|-------|
| **Hands/Forearms** | 1.5kg | ABS | Natural | €70 | 3D printer filament |
| **Arms/Shoulders** | 1.5kg | ABS | Black, Yellow, Natural | €56 | 3D printer filament |
| **Head/Torso/Neck** | 4kg | ABS | Natural | €140 | 3D printer filament |
| **Total ABS Filament** | **7kg** | ABS | Mixed | **€266** | **Approx. 200-500 hours print time** |
| **3D Printing Materials Subtotal** | | | | | **€266** |

---

## Optional: Advanced Computing Platform (for later phases)

### Option A: NUC Mini PC (Recommended for Phase 4+)

| Component | Spec | Price (2016) | Notes |
|-----------|------|-------------|-------|
| CPU | 8th Gen Intel i7-8550U | €600-800 | Quad Core 4.0GHz |
| SSD | 256GB (OS + software) | €80-100 | Ubuntu + Windows 10 Pro dual boot |
| HDD | 500GB (optional) | €30-50 | Backup/additional storage |
| RAM | 32GB | €80-120 | For vision processing |
| Size | 113x108x30mm | - | Compact, fits in robot |
| **NUC Subtotal** | | **€790-1,070** | Optional upgrade for Phase 5 |

### Option B: Tablet Controller (Older Setup - Budget Option)

| Component | Model | Price (2016) | Notes |
|-----------|-------|-------------|-------|
| Tablet | Lenovo ThinkPad 8" | €200-300 | 8" touchscreen, OTG cable required |
| Powerbank | 10,000mAh 5V | €20-30 | Powers all USB devices via hub |
| USB Hub | 8-port USB 3.0 | €15-30 | Powers tablets, Arduinos, cameras |
| Keyboard | Bluetooth detachable | €30-50 | Optional wireless control |
| **Tablet Setup Subtotal** | | **€265-410** | Legacy option; may have compatibility issues |

---

## Summary by Robot Section

| Section | Primary Components | Approx Cost (€) | Print Time |
|---------|------------------|-----------------|-----------|
| **Hands & Forearms** | 10x HK15298B, 2x MG996R, fishing line | €362 | 40-60 hours |
| **Arms & Shoulders** | 8x Hitec HS805BB | €287 | 40-60 hours |
| **Head & Torso** | 2x HS805BB, 1x HK15298B, 2x HK15298B (neck), 2x DS929 (eyes) | €309-319 | 80-120 hours |
| **Control Electronics** | 2x Arduino Mega, Nervo boards | €80-150 | N/A |
| **Power System** | 6V battery/PSU + distribution | €115-160 | N/A |
| **Sensors & Vision** | Camera, PIR, pressure sensors | €90-150 | N/A |
| **Hardware & Cabling** | Bolts, screws, ribbon cables | €95-170 | N/A |
| **3D Printing Materials** | 7kg ABS filament | €266 | 200-500 hours |
| **Audio & Multimedia** | Speakers, amplifier, NeoPixels | €45-90 | N/A |



---

## TOTAL PROJECT ESTIMATE

### Minimum Build (Base Configuration)

| Category | Estimated Cost (€) |
|----------|------------------|
| Servos & Actuators | €958 |
| Computing & Control | €80-150 |
| Power System | €115-160 |
| Sensors & Vision | €90-150 |
| Communication & Cabling | €60-100 |
| Audio & Multimedia | €45-90 |
| Hardware & Fasteners | €35-70 |
| 3D Printing Materials | €266 |
| **SUBTOTAL** | **€1,649-1,934** |

### With Optional Advanced Setup (Phase 4+)

| Category | Cost |
|----------|------|
| Base Configuration | €1,649-1,934 |
| NUC Mini PC (advanced) | €790-1,070 |
| **TOTAL (with NUC)** | **€2,439-3,004** |

**Conclusion**: €1,650 - €3,000 for a fully functional InMoov humanoid robot

---

## Budget Notes

1. **Prices are circa 2016** - Current market prices (2026) will be higher
2. **3D Printer not included** - You already have one or access to one
3. **Optional components** - Advanced vision, tablets, NUC are not mandatory for Phase 1-3
4. **Servo motor costs vary widely** - Premium brands more reliable than budget alternatives
5. **Substitute components possible** - See servo preference rankings above

---

## Servo Motor Substitution Guide

### For Hands (Finger Servos)

**Recommended Hierarchy**:
1. ✅ **JX PDI-6221MG** (20-36kg torque, 180°, most reliable)
2. ✅ **JX PDI-6225MG-300** (20-36kg torque, 300°, extended motion)
3. ✅ **HK15298B** (20kg torque, 90°, InMoov standard, **current choice**)
4. ⚠️ **HK15298** (15kg torque, noisier than HK15298B)
5. ⚠️ **MG996R** (10kg torque, lower power, may burn out)
6. ⚠️ **MG946R** (12kg torque, noisy)
7. ❌ **MG995** (10kg torque, burns easily - avoid)

### For Arms, Shoulders & Torso (High-Torque Servos)

**Recommended Hierarchy**:
1. ✅ **JX Servo PDI-HV2060MG** (60kg torque, 180°, overkill but very reliable)
2. ✅ **TS-80 Tower Hobbies** (24kg torque, identical to HS805BB)
3. ✅ **Hitec HS805BB** (27.5kg torque, 180°, InMoov standard, **current choice**)
4. ✅ **HK15338** (25kg torque, fits perfectly but needs resistors)
5. ✅ **HS5805MG** (27.5kg torque, should fit)
6. ✅ **Savöx SV-0235MG** (35kg torque, fits well)
7. ⚠️ **CYS model S8218** (40kg torque, requires software modifications)

### Alternative Servo Options (Not Tested by InMoov Team)

| Servo Model | Torque | Rotation | Application | Notes |
|-------------|--------|----------|-------------|-------|
| TGY-5521MDHV | 24kg | 180° | Hand | Should fit (untested) |
| RS-550MGC-HV | 11.2kg | Variable | Hand | May work for fingers |
| HS-311 | 3.5kg | 180° | Hand | Low torque, not recommended |
| XQ-S4020D | 21.5kg | 180° | Hand | Untested but promising |
| Ds5160 SSG | 60kg | 180° | Shoulders/Stomach | Heavy-duty option |
| FS6535M | 33kg | 180° | Shoulders/Torso | Good middle ground |

### For Eyes

**Recommended Options**:
- TowerPro SG91 (smallest, lightest)
- TowerPro SG92R (standard servo)
- JX PDI-1109MG (compact high-torque)

---

## Known Issues & Important Notes

### Servo-Specific Requirements

1. **HK15338 servos**: Require reversed polarity resistor modifications (check forums)
2. **All servos need min/max calibration** in software (varying rotation degrees)
3. **Servo mounting**: Different models have different horn attachment points
4. **Current draw**: Each servo 20kg+ draws ~0.5-1A at stall; total robot can draw 30+ amps

### 3D Printing Considerations

- **Total print time**: 200-500+ hours (plan accordingly)
- **ABS vs PLA**: InMoov uses ABS for durability; PLA may not hold up to servo vibration
- **Print orientation**: Critical for strength (parts will be stress-tested)
- **Support material**: Required for many parts; adds print time

### Power Management

- **6V 60A supply recommended** over battery for continuous operation
- **Battery option** (6V 12Ah) works but limits runtime to ~2 hours
- **Charger during operation** keeps battery topped up but adds complexity
- **Current draw**: Arm movement alone can pull 10-20A; full robot 30-50A peaks

---

## Recommended Build Order

### Phase 1 (Weeks 1-4)
- [ ] Order Arduinos, Nervo boards, power supply
- [ ] Get 3D printer filament
- [ ] Begin hand/forearm printing

### Phase 2 (Weeks 5-8)
- [ ] Order arm servos (8x Hitec HS805BB)
- [ ] Order hand servos (10x HK15298B, 2x MG996R)
- [ ] Continue printing arm parts

### Phase 3 (Weeks 9-12)
- [ ] Order head/torso servos
- [ ] Order vision camera
- [ ] Print head and torso pieces

### Phase 4 (Weeks 13+)
- [ ] Order optional computing upgrades
- [ ] Begin assembly testing

---

## Sourcing Tips

### Recommended Suppliers (circa 2016, check current availability)

- **Servo Motors**: Hobbyking, eBay, AliExpress
- **Electronics**: eBay, Amazon, local electronics stores
- **3D Printer Filament**: Orbi-Tech (mentioned in BOM), Prusament, Hatchbox
- **Hardware**: Local hardware stores (bolts, screws, springs)
- **Fishing Line/Tendons**: Sporting goods stores or Amazon

### Cost Optimization

1. **Bulk purchases**: Order similar components together for discounts
2. **Used equipment**: Some 3D printer filament sources offer bulk discounts
3. **Regional alternatives**: Prices vary significantly by country
4. **Community discounts**: InMoov forums may have group buys

---

## Safety Notes

⚠️ **IMPORTANT**:
- All high-torque servos can cause injury; implement mechanical stops
- Power supply (60A) requires proper fusing and breakers
- LiPo batteries require careful charging and storage
- Test each servo individually before full assembly
- Implement emergency stop switch before first power-up

---

## Official InMoov Resources

- **GitHub**: https://github.com/InMoov/InMoov
- **Official Website**: https://inmoov.fr/
- **Parts Lists**: Check GitHub repository for latest BOM
- **Forums**: GitHub discussions for community support

---

## Revision History

| Date | Version | Source |
|------|---------|--------|
| 04/05/2016 | v1.0 | Official InMoov Platform |
| April 2026 | v2.0 | Updated for Project MT with official InMoov specs |

**Last Updated**: April 15, 2026

