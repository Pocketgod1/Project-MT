# Project MT - Comprehensive Timeline & Milestones

**Planning Date**: April 17, 2026  
**Work Schedule**: Evenings & Weekends Only  
**Buffer Period**: 6 months for moving + unforeseen problems  
**Realistic Completion**: 18-24 months from start

---

## ⚡ QUICK TIMELINE OVERVIEW

```
Start: April 2026
├─ Phase 0-1 Learning & Foundation: Apr 2026 - Oct 2026 (7 months)
├─ Phase 2 Hand Mechanism: Oct 2026 - Feb 2027 (5 months)
├─ Phase 3 Arm & Torso: Feb 2027 - Jul 2027 (6 months)
├─ Phase 4 Control System & Testing: Jul 2027 - Dec 2027 (6 months)
├─ Phase 5 Animation Integration: Dec 2027 - Apr 2028 (5 months)
├─ Buffer Period: Apr 2028 - Oct 2028 (6 months for move + problems)
└─ Final Testing & Demo: Oct 2028 - Dec 2028 (3 months)

✅ TARGET COMPLETION: December 2028 (32 months total, ~2.5 years)
```

---

## 📚 PHASE 0: LEARNING FOUNDATION (April - October 2026)

### Timeline: 7 Months (vs. 6 weeks full-time equivalent)

**Why it takes 7 months on evenings/weekends**:
- Full-time: 40 hours/week × 6 weeks = 240 hours total
- Part-time: 10-15 hours/week × 7 months = ~280-420 hours
- Learning complex concepts requires time for absorption + practice

### 0.1 Robotics & Math Fundamentals (April - May 2026)
**Effort**: 4 weeks at 10-15 hours/week = ~50-60 hours  
**Status**: Starting now

| Week | Focus | Hours/Week | Deliverable |
|------|-------|-----------|-------------|
| Apr 15-21 | Linear algebra, coordinate systems, Arduino basics | 12 | Understanding of 3D coordinates |
| Apr 22-28 | Trigonometry review, DH parameters intro | 12 | DH notation comprehension |
| Apr 29-May 5 | Servo motor electronics, PWM signals | 12 | Servo control concepts |
| May 6-12 | Practice projects & review | 10 | Simple Arduino servo blink |

**Cumulative Time**: ~50 hours

### 0.2 Core Kinematics & Math (May - June 2026)
**Effort**: 5 weeks at 12-15 hours/week = ~60-75 hours  

| Week | Focus | Hours/Week | Deliverable |
|------|-------|-----------|-------------|
| May 13-19 | Forward kinematics theory | 13 | FK calculator (2-DOF arm) |
| May 20-26 | Matrix transformations | 14 | Matrix multiplication understanding |
| May 27-Jun 2 | Inverse kinematics concepts | 13 | IK solver pseudocode |
| Jun 3-9 | Python NumPy/SciPy practice | 14 | Working IK solver (2-DOF) |
| Jun 10-16 | 3-DOF arm implementation | 12 | 3-DOF IK solver |

**Cumulative Time**: ~110 hours

### 0.3 Animation & Blender Intro (June - August 2026)
**Effort**: 8 weeks at 10-14 hours/week = ~90-112 hours  

| Week | Focus | Hours/Week | Deliverable |
|------|-------|-----------|-------------|
| Jun 17-23 | Blender interface + basics | 12 | Simple 3D model |
| Jun 24-30 | Blender rigging fundamentals | 14 | Rigged humanoid skeleton |
| Jul 1-7 | Animation and keyframes | 12 | Animated character sequence |
| Jul 8-14 | FBX export and file parsing | 13 | Parse FBX animation data |
| Jul 15-21 | Game animation research | 10 | Elden Ring animation extraction |
| Jul 22-28 | Skeleton mapping theory | 12 | Robot ↔ Game skeleton mapping |
| Jul 29-Aug 4 | Animation to angles conversion | 13 | Animation → joint angles pipeline |
| Aug 5-11 | Testing & optimization | 12 | Full animation parsing working |

**Cumulative Time**: ~200 hours

### 0.4 CAD Design & Electronics (August - September 2026)
**Effort**: 5 weeks at 12-14 hours/week = ~60-70 hours  

| Week | Focus | Hours/Week | Deliverable |
|------|-------|-----------|-------------|
| Aug 12-18 | FreeCAD fundamentals | 12 | Simple CAD part |
| Aug 19-25 | Servo mounting design | 14 | Servo horn adapter CAD |
| Aug 26-Sep 1 | Power system electronics | 13 | Power distribution circuit diagram |
| Sep 2-8 | Control circuit design | 12 | Motor control circuit |
| Sep 9-15 | Review + practice | 11 | All CAD/circuit designs validated |

**Cumulative Time**: ~260 hours

### 0.5 Integration & Testing (September - October 2026)
**Effort**: 4 weeks at 10-13 hours/week = ~44-52 hours  

| Week | Focus | Hours/Week | Deliverable |
|------|-------|-----------|-------------|
| Sep 16-22 | Python servo control module | 11 | Arduino ↔ Python communication |
| Sep 23-29 | Full software stack integration | 13 | Animation → Kinematics → Servo commands |
| Sep 30-Oct 6 | Testing on simulation | 12 | PyBullet simulation working |
| Oct 7-13 | Documentation & review | 10 | Learning phase summary |

**Cumulative Time**: ~305 hours total for Phase 0

---

## 🏗️ PHASE 1: HARDWARE FOUNDATION (October 2026 - February 2027)

### Phase 1A: HAND MECHANISM (October 2026 - January 2027)
**Effort**: 16 weeks (vs. 4 weeks full-time)  
**Why it takes 4x longer**:
- Shipping delays (2-4 weeks component delivery)
- 3D printing takes time (40-60 hours continuous)
- Assembly + testing takes methodical approach
- Working weekends only = fewer concentrated hours

| Week | Task | Duration | Cumulative |
|------|------|----------|-----------|
| Oct 1-15 | Order all parts (servos, filament, fasteners) | 2 weeks | 2 weeks |
| Oct 16-31 | Wait for parts to arrive | 2 weeks | 4 weeks |
| Nov 1-15 | 3D print finger components | 3 weeks | 7 weeks |
| Nov 16-30 | Parts QA & servo testing | 2 weeks | 9 weeks |
| Dec 1-15 | Assembly (tendons, springs, calibration) | 2 weeks | 11 weeks |
| Dec 16-31 | Testing, debugging, optimization | 2 weeks | 13 weeks |
| Jan 1-15 | Documentation & final tweaks | 2 weeks | 15 weeks |
| Jan 16-31 | Video demo + validation | 2 weeks | 16 weeks |

**Phase 1A Completion**: Late January 2027

**Deliverables**:
- ✅ Left hand fully functional (12 servos: 10x finger + 2x wrist)
- ✅ Right hand fully functional (optional: can skip to accelerate)
- ✅ Servo calibration profiles documented
- ✅ Assembly guide with photos/video
- ✅ Demo video showing finger movement

---

### Phase 1B: ARM MECHANISM (February 2027 - July 2027)
**Effort**: 20 weeks (vs. 8 weeks full-time)  

| Week | Task | Duration | Cumulative |
|------|------|----------|-----------|
| Feb 1-15 | Order arm servos & hardware | 2 weeks | 2 weeks |
| Feb 16-Mar 15 | Parts arrival + QA | 4 weeks | 6 weeks |
| Mar 16-Apr 15 | 3D print arm components | 4 weeks | 10 weeks |
| Apr 16-30 | Servo testing (8x Hitec HS805BB) | 2 weeks | 12 weeks |
| May 1-15 | Assembly (mounting, wiring) | 2 weeks | 14 weeks |
| May 16-31 | Arm + hand integration | 2 weeks | 16 weeks |
| Jun 1-15 | Testing & calibration | 2 weeks | 18 weeks |
| Jun 16-30 | Software integration (arm control) | 2 weeks | 20 weeks |

**Phase 1B Completion**: Early July 2027

**Deliverables**:
- ✅ Left arm fully functional (8 servos)
- ✅ Right arm fully functional
- ✅ Hand + arm coordination working
- ✅ 3D test movement patterns

---

## 👤 PHASE 2: TORSO & LEGS (July 2027 - December 2027)

### Phase 2A: TORSO & HEAD (July - September 2027)
**Effort**: 12 weeks

| Task | Duration | Notes |
|------|----------|-------|
| Component ordering | 2 weeks | Neck/spine/chest servos |
| Parts arrival + QA | 3 weeks | Multiple shipments |
| 3D printing torso | 4 weeks | Large parts, multiple prints |
| Assembly + testing | 3 weeks | Complex spine mechanism |

**Completion**: Mid-September 2027

---

### Phase 2B: LEGS & LOCOMOTION (September - December 2027)
**Effort**: 16 weeks

| Task | Duration | Notes |
|------|----------|-------|
| Component ordering | 2 weeks | Hip/knee/ankle servos |
| Parts arrival + QA | 3 weeks | Heavy components |
| 3D printing legs | 5 weeks | Most parts needed |
| Assembly (lower body) | 4 weeks | Complex hip/knee joints |
| Testing (standing balance) | 2 weeks | Critical milestone |

**Completion**: End of December 2027

**Deliverables**:
- ✅ Full body assembled and standing
- ✅ All servos responsive
- ✅ Basic balance testing

---

## ⚙️ PHASE 3: CONTROL SYSTEM & INTEGRATION (January - June 2028)

**Effort**: 24 weeks

| Phase | Duration | Focus |
|-------|----------|-------|
| Software stack architecture | 3 weeks | Revise control layer design |
| Motor control refinement | 4 weeks | Individual joint testing |
| Kinematics system integration | 4 weeks | Full body FK/IK |
| Real-time control loop | 3 weeks | 50Hz+ servo update rate |
| Synchronization & coordination | 4 weeks | Multi-servo motion patterns |
| Testing & debugging | 6 weeks | Stability, safety, responsiveness |

**Completion**: End of June 2028

---

## 🎬 PHASE 4: ANIMATION INTEGRATION (July - October 2028)

**Effort**: 16 weeks

| Task | Duration | Notes |
|------|----------|-------|
| Animation format testing | 2 weeks | Elden Ring + other games |
| Skeleton mapping validation | 3 weeks | Robot ↔ Game skeleton |
| Simple animation playback | 3 weeks | Idle animation first |
| Complex animation sequences | 4 weeks | Walk, attack, dodge animations |
| Playback optimization | 2 weeks | Smooth, natural movement |
| Testing & validation | 2 weeks | Record demo video |

**Completion**: Early October 2028

---

## 🧠 PHASE 5: BUFFER & CONTINGENCY (October 2028)

**Allocated**: 1 month before final target

**Buffer covers**:
- ✅ Unforeseen hardware failures
- ✅ Component delays
- ✅ Software bugs
- ✅ Moving disruptions
- ✅ Personal emergencies

---

## 🎯 FINAL MILESTONE: DEMONSTRATION (November - December 2028)

**Target**: Working humanoid robot playing Elden Ring animations

| Deliverable | Status |
|-------------|--------|
| Standing humanoid robot | ✅ Target |
| Hand/arm movement | ✅ Target |
| Full body animation playback | ✅ Target |
| Demo video published | ✅ Target |
| Complete documentation | ✅ Target |
| Open-source code released | ✅ Target |

---

## 📊 MONTHLY BREAKDOWN WITH BUFFER

```
2026 (Learning Phase)
Apr ████░░░░░░ Fundamentals start
May ████████░░ Kinematics study
Jun ████████░░ Animation/Blender intro
Jul ████████░░ 3D design & electronics
Aug ████████░░ CAD & integration
Sep ████████░░ Testing & review
Oct ████░░░░░░ Final learning phase

2027 (Hardware Phase 1: Hands & Arms)
Nov ████████░░ Hand parts ordered → printing
Dec ████████░░ Hand assembly & testing
Jan ████░░░░░░ Hand finalization
Feb ████████░░ Arm parts ordered
Mar ████████░░ Arm printing
Apr ████████░░ Arm assembly
May ████████░░ Hand+Arm integration
Jun ████░░░░░░ Testing & calibration
Jul ████░░░░░░ Phase 1 completion

2027 (Hardware Phase 2: Body & Legs)
Aug ████████░░ Torso ordered → printing
Sep ████████░░ Torso assembly
Oct ████████░░ Legs ordered & printing
Nov ████████░░ Legs assembly
Dec ████░░░░░░ Full body standing test

2028 (Control & Software)
Jan ████████░░ Software architecture
Feb ████████░░ Motor control refinement
Mar ████████░░ Kinematics integration
Apr ████████░░ Real-time control loops
May ████████░░ Multi-servo coordination
Jun ████░░░░░░ Control system finalized

2028 (Animation & Buffer)
Jul ████████░░ Animation integration start
Aug ████████░░ Animation playback
Sep ████████░░ Complex sequences
Oct ████░░░░░░ Buffer period / contingency
Nov ████░░░░░░ Final testing
Dec ████░░░░░░ Demonstration ready
```

---

## ⏰ WORK HOURS ESTIMATE BY PHASE

| Phase | Weeks | Hours/Week | Total Hours | Notes |
|-------|-------|-----------|------------|-------|
| Phase 0: Learning | 28 | 11 | ~310 | 2025-2026 hours/week average |
| Phase 1A: Hand | 16 | 15 | ~240 | More concentrated, hands-on |
| Phase 1B: Arm | 20 | 14 | ~280 | Shipping delays offset work |
| Phase 2: Body/Legs | 28 | 13 | ~360 | Most intensive hardware phase |
| Phase 3: Control | 24 | 12 | ~290 | Software focus |
| Phase 4: Animation | 16 | 11 | ~176 | Fine-tuning phase |
| Buffer & contingency | 4 | 20 | ~80 | High intensity if needed |
| **TOTAL** | **136 weeks / 32 months** | **~13 avg** | **~1,736 hours** | |

**Perspective**: 1,736 hours over 32 months = ~4.5 hours/week average  
*(Realistic for hobbyist with other commitments)*

---

## 🚨 RISK FACTORS & CONTINGENCY

### High Risk Items (Likely to Cause Delays)

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Servo motor unavailability (HK15298B shortage) | 2-4 weeks | Have alternative servo selected (JX PDI-6221MG) |
| 3D printing failures | 1-2 weeks per failure | Print critical parts twice; have backup filament |
| Shipping delays (international) | 2-4 weeks | Order parts earlier than needed |
| Component defects | 1-2 weeks | Test everything immediately upon arrival |
| Moving disruption | 2-4 weeks | Buffer period allocated (October 2028) |
| Software integration bugs | 1-3 weeks | Incremental testing, not end-phase integration |
| Design flaws discovered | 2-4 weeks | Iterate on hand first as proof-of-concept |

### Contingency Time Usage

**If 1-2 minor issues**: Absorbed within Phase 4 buffer  
**If 1 major issue** (servo shortage, design flaw): Use 2-3 weeks from buffer  
**If moving happens mid-project**: Buffer allocated at end handles this  
**If multiple issues**: Extend timeline by 2-4 months past December 2028  

---

## 📅 DECISION POINTS & CHECKPOINTS

### Monthly Checkpoint Questions

**Every Month Ask Yourself**:
- [ ] Did I complete planned tasks? (If not, why?)
- [ ] Are there unexpected delays building up?
- [ ] Do I need to re-order something?
- [ ] Is the timeline still achievable?

### Critical Decision Points

| Date | Decision | Options |
|------|----------|---------|
| July 2026 | Continue learning or start ordering parts? | A) Finish all learning first / B) Start ordering Phase 1 parts |
| October 2026 | Build one hand or both hands? | A) One hand (faster) / B) Both hands (more work now) |
| February 2027 | Full torso or skip to simpler legs first? | A) Full body / B) Bipedal legs only initially |
| June 2028 | Simple walk or complex animations first? | A) Idle/walk / B) Attack animations |
| October 2028 | If behind schedule, cut features or extend? | A) Remove legs locomotion / B) Extend to 2029 |

---

## 🎯 SUCCESS METRICS

### Phase 1A Success
- [ ] Hand mechanism moves smoothly
- [ ] Servo response time < 100ms
- [ ] Tendon routing doesn't slip
- [ ] Video demo of finger movement

### Phase 2 Success
- [ ] Full body assembled and wired
- [ ] Standing balance for > 10 seconds
- [ ] All 30+ servos responding to commands

### Phase 3 Success
- [ ] Animation → kinematics → servo commands working end-to-end
- [ ] Movement is smooth and coordinated
- [ ] No servo overheating or stalling

### Phase 4 Success
- [ ] Robot replicates game animations recognizably
- [ ] Movement is fluid and natural-looking
- [ ] Timing matches game speed

### Final Success
- [ ] Published video showing full animation playback
- [ ] Code released on GitHub with documentation
- [ ] Community engagement (comments, improvements, forks)

---

## 📋 QUICK START NEXT ACTIONS

**This Week (Apr 17-23)**:
- [ ] Review LEARNING_RESOURCES.md (pick starting point)
- [ ] Schedule 10-15 hours learning time for next week
- [ ] Set up workspace: laptop, notebook, reference materials
- [ ] Begin Phase 0.1 (linear algebra videos, Arduino basics)

**Next Month (May 2026)**:
- [ ] Complete Phase 0.1 (robotics fundamentals)
- [ ] Begin Phase 0.2 (kinematics math)
- [ ] Start simple forward kinematics implementation

**After Learning Complete (October 2026)**:
- [ ] Finalize hand mechanism CAD
- [ ] Place orders for Phase 1A parts
- [ ] Prepare workspace for 3D printing
- [ ] Set up servo testing equipment

---

## 📝 TIMELINE UPDATE NOTES

**Track your actual progress**:
- Update this file monthly with actual vs. planned time
- Note any delays or accelerations
- Adjust future estimates based on reality
- Share progress with community

**Repository Note**:
- This timeline should be reviewed quarterly
- Update buffer if moving date changes
- Adjust phases if learning takes longer/shorter
- Document major blockers and solutions

---

**Last Updated**: April 17, 2026  
**Next Review**: May 17, 2026 (1 month check-in)  
**Contact**: GitHub Issues for timeline feedback
