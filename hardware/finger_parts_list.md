# InMoov Hand & Finger Mechanism - Complete Parts List with Ordering Links

## 🎯 Quick Start: Print This for Shopping!

**Total Cost**: $385-440 (all parts, standard servos)  
**Total Cost (Premium Servos)**: $440-550 (if using JX PDI-6221MG as substitute)  
**Servo Count**: 12 servos (10x finger + 2x wrist)  
**Print Time**: 40-60 hours  
**Estimated Assembly**: 8-12 hours  

⚠️ **NOTE**: HK15298B is hard to find (April 2026). See alternatives section below.  

---

## Phase 1 Build Focus: Hand/Finger Mechanism (Left + Right)

### Why Start with Fingers?
✅ Self-contained system (can test independently)  
✅ High learning value (servo control, tendon mechanism)  
✅ Relatively quick to print (~50 hours)  
✅ Foundation for arm assembly later  
✅ Demonstrates full mechanical integration

---

## ORDERING CHECKLIST: Copy & Paste Ready

### ✅ SERVO MOTORS (Primary Supply)

| Component | Qty | Model | Unit Price | Est. Total | Supplier | Link |
|-----------|-----|-------|-----------|-----------|----------|------|
| **Finger Servos** | 10 | HK15298B (20kg torque) ⚠️ HARD TO FIND | $20 | $198 | Hobbyking/AliExpress | https://hobbyking.com/ (search: HK15298B) |
| **Wrist Servos** | 2 | MG996R (10kg torque) | $12 | $24 | eBay | https://www.ebay.com/ (search: MG996R servo) |
| **SERVO SUBTOTAL** | | | | **$222** | | |

### ✅ MECHANICAL COMPONENTS

| Component | Qty | Size/Spec | Unit Price | Est. Total | Supplier | Link |
|-----------|-----|-----------|-----------|-----------|----------|------|
| **Fishing Line** | 1 spool | 0.8mm diameter, 200LB | $11 | $11 | Amazon / eBay | https://www.amazon.com/ (search: 0.8mm braided fishing line) |
| **Extension Springs** | 10 | 0.51mm dia, 1cm length | $0.55 | $5.50 | AliExpress | https://www.aliexpress.com/ (search: extension spring 0.51mm) |
| **Allen M3x20 Bolts** | 50 | Countersunk | $0.11 | $5.50 | Hardware Store (local) | Any local hardware/DIY store |
| **Phillips M3x12 Screws** | 100 | Wood screws | $0.06 | $5.50 | Hardware Store (local) | Any local hardware/DIY store |
| **Misc Bolts/Nuts** | Assorted | M3, M4 hardware | $11 | $11 | Hardware Store (local) | Any local hardware/DIY store |
| **MECHANICAL SUBTOTAL** | | | | **$39** | | |

### ✅ 3D PRINTING MATERIALS (ABS Filament)

| Component | Qty | Color | Unit Price/kg | Est. Total | Supplier | Link |
|-----------|-----|-------|-----------|-----------|----------|------|
| **ABS Filament** | 1.5kg | Natural | $20-31/kg | $66 | OVERTURE (Amazon - Highest Rated) | https://www.amazon.com/s?k=OVERTURE+ABS+Filament+1.75mm |
| | or | | $22-28/kg | $77 | Orbi-Tech (EU) | https://www.orbitech.de/ |
| | or | | $28-39/kg | $77 | Prusament | https://shop.prusa3d.com/ |
| **PRINTING MATERIAL SUBTOTAL** | | | | **$77** | | |

### ✅ OPTIONAL: TESTING & TUNING

| Component | Qty | Spec | Price | Supplier | Link |
|-----------|-----|------|-------|----------|------|
| **Multimeter** | 1 | Digital | $13 | Amazon/eBay | For servo diagnostics |
| **Servo Tester** | 1 | Manual PWM | $16.50 | AliExpress | https://www.aliexpress.com/ (search: servo tester) |
| **Jumper Wires** | 1 pack | Male/Female | $9 | Amazon | For testing |
| **Breadboard** | 1 | Mini | $5.50 | Amazon | Development board |
| **USB Power Bank** | 1 | 5V 3A+ | $22 | Any retailer | For testing servos |
| **OPTIONAL TESTING SUBTOTAL** | | | **$66** | | |

---

## DETAILED PART-BY-PART LINKS & RECOMMENDATIONS

### 🎯 TIER 1: CRITICAL (Order First)

#### Servo Motors - HK15298B (Finger Servos) ⭐ PRIORITY 1

⚠️ **AVAILABILITY NOTE (April 2026)**: HK15298B is hard to find. See alternatives below.

**Why This Model?**
- Official InMoov recommendation
- 20kg torque (strong, quiet, reliable)
- 90° rotation (perfect for finger spread)
- Never burns out (tested by InMoov community)

**Ordering Options:**

1️⃣ **PRIMARY: AliExpress** (Most likely current source)
   - Website: https://www.aliexpress.com/
   - Search: "HK15298B servo"
   - Expected Price: $13-20 each
   - Shipping: 2-4 weeks
   - **Note**: Check multiple sellers, some may have stock
   - **Link**: https://www.aliexpress.com/wholesale?SearchText=HK15298B

2️⃣ **BACKUP: eBay** (International sellers)
   - Website: https://www.ebay.com/
   - Search: "HK15298B servo 20kg"
   - Expected Price: $20-28 each
   - Shipping: 3-7 days (seller dependent)
   - Sellers: Look for +99% rating

3️⃣ **IF UNAVAILABLE: Use JX PDI-6221MG** ✅ RECOMMENDED SUBSTITUTE
   - Website: https://www.aliexpress.com/
   - Search: "JX PDI-6221MG servo"
   - Torque: 20-36kg (same class as HK15298B)
   - Price: $28-33 each (~$275-330 for 10)
   - **Advantage**: More modern, higher quality, more reliable
   - **Disadvantage**: Slightly more expensive
   - **Note**: Housing may need minor adjustment (servo slightly larger)

**Quantity Needed: 10 servos**

**Shopping Priority**:
1. ✅ Try to find HK15298B on AliExpress first
2. ⚠️ If out of stock everywhere, order JX PDI-6221MG instead
3. ❌ DO NOT use HK4140MG or other large-scale servos (too big, wrong purpose)

**Shopping Notes:**
- Qty 10 = ~$198 (HK15298B) or ~$275-330 (JX substitute)
- **IMPORTANT**: Check packaging states "HK15298B" not "HK15298" (if you find original)
- Verify torque spec: should say "20kg.cm" or higher at 6V
- If substituting JX PDI-6221MG: verify mounting hole pattern matches CAD

---

#### Servo Motors - MG996R (Wrist Rotation)

**Why This Model?**
- 10kg torque (good for wrist rotation)
- 180° rotation (full wrist span)
- Budget-friendly, widely available
- Lower wear than larger servos

**Ordering Options:**

1️⃣ **PRIMARY: eBay**
   - Search: "MG996R servo motor"
   - Expected Price: $11-16 each
   - Link: https://www.ebay.com/sch/i.html?_nkw=MG996R+servo

2️⃣ **ALTERNATIVE: Amazon**
   - Search: "MG996R servo"
   - Price: $13-20 each
   - Link: https://www.amazon.com/s?k=MG996R+servo

3️⃣ **BUDGET: AliExpress**
   - Search: "MG996R servo motor"
   - Price: $9-13 each
   - Link: https://www.aliexpress.com/wholesale?SearchText=MG996R

**Quantity Needed: 2 servos**

**Shopping Notes:**
- Get 2 for left + right wrist
- These WILL burn out if overloaded; use current limiting
- Some users report noise; acceptable for wrist use

---

### 🎯 TIER 2: ESSENTIAL (Order Second)

#### Braided Fishing Line (Tendon Material)

**Specification**: 0.8mm diameter, 200lb test weight

**Why?**
- Transmits finger flexion from servo to finger phalanges
- Must be strong (tendons pull ~50N force)
- 0.8mm fits through printed holes
- 200lb test = safety margin

**Ordering Options:**

1️⃣ **PRIMARY: Amazon**
   - Search: "0.8mm braided fishing line 200lb"
   - Price: $9-13 per spool (50+ meters)
   - Link: https://www.amazon.com/s?k=0.8mm+braided+fishing+line+200lb
   - Recommendation: Buy 1-2 spools (can use extras for arm tendons)

2️⃣ **ALTERNATIVE: eBay**
   - Search: "0.8mm braided fishing line"
   - Price: $9-17
   - Link: https://www.ebay.com/sch/i.html?_nkw=0.8mm+braided+fishing+line

3️⃣ **SPORTING GOODS STORE (Local)**
   - Check local fishing shops
   - Price: $5.50-11
   - Advantage: Immediate pickup, no shipping

**Quantity Needed: 1 spool**

**Shopping Notes:**
- Buy slightly more than needed (test failures, restringing)
- Avoid monofilament (stretches, not suitable)
- Must be "braided" type (no elasticity)

---

#### Extension Springs (Finger Return)

**Specification**: 0.51mm diameter, 1cm length (13/64" x 13/16")

**Why?**
- Return fingers to open position after servo release
- Must match exact specifications for calibration
- 10 springs total (one per finger)

**Ordering Options:**

1️⃣ **PRIMARY: AliExpress** (Best for exact springs)
   - Search: "extension spring 0.51mm 1cm"
   - Price: $3.60-9.70 for pack of 10-20
   - Link: https://www.aliexpress.com/wholesale?SearchText=extension+spring+0.51mm
   - Shipping: 2-4 weeks

2️⃣ **QUICK OPTION: Amazon** (Faster)
   - Search: "extension springs 0.51mm"
   - Price: $9-16.50 for assorted pack
   - Link: https://www.amazon.com/s?k=extension+springs+0.51mm

3️⃣ **HARDWARE STORE** (If exact match unavailable)
   - Local spring supplier
   - Get assorted pack, select nearest match
   - May need to test multiple springs

**Quantity Needed: 10 springs**

**Shopping Notes:**
- These are small, easy to lose
- If exact 1cm length unavailable, 0.8-1.2cm acceptable (calibrate in software)
- **IMPORTANT**: Spring constant affects finger response; may need to test

---

### 🎯 TIER 3: HARDWARE (Order Third or Local)

#### Fasteners: Allen Countersunk M3x20 Bolts (~50)

**Why?**
- Mounting servo horns to 3D-printed parts
- Countersunk head (fits flush in prints)
- M3 size standard for InMoov

**Ordering:**

1️⃣ **CHEAPEST: Local Hardware Store**
   - Any DIY store (Home Depot, Leroy Merlin, B&Q)
   - ~$5.50-9 for 50+ piece pack
   - Pick up same day

2️⃣ **ONLINE: Amazon / eBay**
   - Search: "M3x20 countersunk bolt"
   - $9-13 for 50-piece pack
   - Link: https://www.amazon.com/s?k=M3x20+countersunk+bolt

3️⃣ **BULK: AliExpress**
   - $3.30-6.60 for large assorted pack
   - Shipping: 2-3 weeks

**Quantity Needed: 50 bolts** (overstock acceptable)

---

#### Fasteners: Phillips M3x12 Wood Screws (~100)

**Why?**
- Secure servo horns and small components
- M3 threads match printed hole inserts
- 12mm length perfect for servo mounting

**Ordering:**

1️⃣ **LOCAL: Hardware Store** ⭐ RECOMMENDED
   - $5.50-9 for 100-pack
   - Pick up same day
   - No shipping delay

2️⃣ **ONLINE: Amazon**
   - Search: "M3x12 wood screws"
   - $9-13 for 100-pack
   - Link: https://www.amazon.com/s?k=M3x12+wood+screw

**Quantity Needed: 100 screws** (overstock acceptable)

---

#### Miscellaneous Bolts & Hardware

**What You Need:**
- Assorted M3, M4 bolts, nuts, washers
- Total spend: $11-17
- Get from local hardware store

**Ordering:**
- Visit any hardware store
- Get mixed pack or ask for "M3/M4 assorted fasteners"
- $11-17 buys plenty

---

### 🎯 TIER 4: 3D PRINTING MATERIAL (Order Early!)

#### ABS Filament - 1.5kg, Natural Color

**Specification:**
- Material: ABS (not PLA - InMoov standard)
- Color: Natural (white/off-white)
- Diameter: 1.75mm
- Quality: Standard 3D printer filament

**Why ABS?**
- Stronger under servo vibration
- Better heat resistance
- Standard for InMoov (proven)
- PLA will crack under stress

**Recommended Suppliers:**

1️⃣ **BEST VALUE: OVERTURE ABS Filament** ⭐ RECOMMENDED (Amazon)
   - Website: https://www.amazon.com/s?k=OVERTURE+ABS+Filament+1.75mm
   - Price: $20-31/kg (~$66 for 1.5kg)
   - Quality: Highest rated on Amazon, excellent reviews
   - Specifications: High strength, low warping, ±0.02mm precision
   - Shipping: 1-2 days (Prime eligible)
   - **Why This?**: Amazon's "Overall Pick" for ABS filament, most reliable value option

2️⃣ **GOOD: Orbi-Tech** (Original BOM source)
   - Website: https://www.orbitech.de/
   - Price: $22-28/kg ($33-44 for 1.5kg)
   - Quality: Good, tested with InMoov
   - Shipping: 2-4 days (EU)

3️⃣ **PREMIUM: Prusament** (EU)
   - Website: https://shop.prusa3d.com/
   - Price: $28-39/kg ($42-58 for 1.5kg)
   - Quality: Excellent, consistent
   - Shipping: 3-5 days (EU)

4️⃣ **CHEAPEST: AliExpress**
   - Price: $13-22/kg
   - Shipping: 2-4 weeks
   - ⚠️ Quality variable; check reviews

**Quantity Needed: 1.5kg**

**Shopping Notes:**
- Buy 1-2kg to allow for failed prints/learning
- Make sure your printer supports ABS (needs heated bed ~100°C)
- Store in dry location (ABS absorbs moisture)
- Consider spare spool for arm printing (Phase 1b)

---

### 🎯 TIER 5: OPTIONAL BUT RECOMMENDED

#### Servo Tester ($16.50-22)

**Why?**
- Test each servo individually before assembly
- Verify servo operation
- No Arduino needed

**Ordering:**
- AliExpress: "servo tester manual"
- https://www.aliexpress.com/wholesale?SearchText=servo+tester
- Price: $13-20
- Or get simple PWM module ($9)

---

#### Digital Multimeter ($11-17)

**Why?**
- Check servo power draw
- Verify electrical connections
- Essential for troubleshooting

**Ordering:**
- Amazon or local electronics store
- ~$13
- Any basic model sufficient

---

## 📋 COMPLETE SHOPPING SUMMARY

### Quick Order Template (Copy & Check Off)

```
FINGER MECHANISM PARTS ORDER
============================

☐ 10x HK15298B servos ($198)
   Supplier: Hobbyking / eBay
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 2x MG996R servos ($24)
   Supplier: eBay / Amazon
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 1x Braided fishing line 0.8mm 200lb ($11)
   Supplier: Amazon / Local sporting goods
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 10x Extension springs 0.51mm ($5.50-9)
   Supplier: AliExpress / Amazon
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 50x M3x20 Allen bolts ($5.50-9)
   Supplier: Local hardware store
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 100x M3x12 wood screws ($5.50-9)
   Supplier: Local hardware store
   Link: ________________
   Order Date: __________ Tracking: __________

☐ Misc M3/M4 hardware ($11-17)
   Supplier: Local hardware store
   Link: ________________
   Order Date: __________ Tracking: __________

☐ 1.5kg ABS filament natural ($66)
   Supplier: OVERTURE (Amazon - recommended)
   Link: ________________
   Order Date: __________ Tracking: __________

☐ [OPTIONAL] Servo tester ($16.50)
   Supplier: AliExpress
   Link: ________________
   Order Date: __________ Tracking: __________

========================================
ESTIMATED TOTAL COST: $385-440
ESTIMATED DELIVERY: 5-14 days (faster parts arrive first)
========================================
```

---

## 🚚 RECOMMENDED ORDERING STRATEGY

### Week 1: FAST PARTS (Order Today!)

**Priority 1 (Next-Day if Possible):**
- ✅ **Local Hardware Store** → Bolts, screws, springs (if local has them)
- ✅ **Amazon Prime** → ABS filament (1-2 day delivery)
- ✅ **eBay** → MG996R servos (3-7 day delivery, EU seller)

**Priority 2 (This Week):**
- ✅ **Hobbyking** → HK15298B servos (5-7 day delivery)
- ✅ **Amazon** → Fishing line (2-3 day delivery)

**Subtotal Time**: ~1 week for critical parts

### Week 2-3: SLOW PARTS (Order if Local Unavailable)

- ✅ **AliExpress** → Springs, backup fishing line (2-4 weeks)
- ✅ **AliExpress** → Servo tester (optional, 2-4 weeks)

---

---

## ⚠️ SERVO AVAILABILITY UPDATE (April 2026)

### HK15298B Shortage & Alternatives

**Status**: HK15298B is difficult to source in April 2026. Community members report stock issues.

**Recommended Action**:
1. Check AliExpress for HK15298B (multiple sellers may have inventory)
2. If unavailable, substitute with **JX PDI-6221MG** (higher quality alternative)
3. **DO NOT use large-scale servos** like HK4140MG (wrong application)

### Why NOT HK4140MG?

| Criterion | HK15298B (Correct) | HK4140MG (Wrong) | Problem |
|-----------|------------------|------------------|---------|
| **Torque** | 20kg | 40kg | 2x overkill; fingers don't need this |
| **Size** | Small (fits finger) | **Large** | **Won't fit in finger housing** |
| **Rotation** | 90° (ideal for fingers) | 180° | Wrong motion range |
| **Weight** | ~50g | **~200g+** | 4x heavier; stresses servo horn |
| **Application** | Robot fingers | RC crawler/aircraft | Completely different purpose |
| **Power Draw** | ~0.5A stall | ~1.2A stall | Heating & power issues |
| **Result** | ✅ Works perfectly | ❌ Mechanically incompatible | **DO NOT USE** |

**HK4140MG is designed for 1/5-1/6 scale RC crawlers, NOT robot fingers.**

### Servo Substitute Options (If HK15298B Unavailable)

**Ranked by Suitability:**

| Rank | Model | Torque | Size | Price | Source | Status |
|------|-------|--------|------|-------|--------|--------|
| 1️⃣ | **JX PDI-6221MG** | 20-36kg | Medium | $28-33 | AliExpress | ✅ Available |
| 2️⃣ | Savöx SV-0235MG | 13.5kg | Medium | $22 | Amazon/eBay | ✅ Available |
| 3️⃣ | MG996R | 10kg | Small | $13 | eBay | ✅ Available |
| 4️⃣ | FS6535M | 33kg | Large | $33 | AliExpress | ✅ Available |
| 5️⃣ | HK15338 | 25kg | Medium | $20 | AliExpress | ✅ Available |

**BEST CHOICE: JX PDI-6221MG** ⭐
- Torque range: 20-36kg (covers HK15298B performance)
- More modern, higher quality
- Better reliability rating
- Slightly more expensive but worth it
- Minor housing adjustment may be needed

### Shopping Decision Tree

```
Need finger servos?
    │
    ├─ Can find HK15298B on AliExpress?
    │   YES → Order it! ($13-20 each, 2-4 weeks)
    │   NO → Go to next step
    │
    ├─ Budget is flexible?
    │   YES → Order JX PDI-6221MG ($28-33 each, better quality)
    │   NO → Go to next step
    │
    ├─ Want cheapest option?
    │   YES → Use 10x MG996R ($13 each, but slower)
    │   NO → Order JX PDI-6221MG anyway
    │
    └─ NO servos work?
        → Ask community: https://github.com/InMoov/InMoov/discussions
```

---
   - Verify servo specifications before printing mounting holes
   - Different servo models have different hole patterns

2. **Buy Extra Springs & Fishing Line**
   - These break easily during setup
   - You'll need spares for learning

3. **Check Servo Specs Carefully**
   - ❌ DON'T buy HK15298 (old version, noisier)
   - ✅ DO buy HK15298B (current, better)
   - ❌ DON'T buy MG995 (burns out easily)
   - ✅ DO buy MG996R (proven reliable)

4. **Verify Servo Quantity**
   - Fingers: 10 servos
   - Wrist: 2 servos
   - **Total: 12 servos** (for one hand; multiply by 2 for both)

5. **ABS Filament Temperature**
   - Requires heated bed ~100°C
   - Check your printer supports ABS
   - If not, use PLA (less ideal but works)

---

## 📞 SUPPORT & REFERENCES

### Official InMoov Resources
- **GitHub Discussions**: https://github.com/InMoov/InMoov/discussions
- **Official Website**: https://inmoov.fr/
- **Community Forums**: Check GitHub for build logs and tips

### Supplier Quality Ratings (as of April 2026)

| Supplier | Reliability | Speed | Price | Recommendation |
|----------|------------|-------|-------|-----------------|
| Hobbyking | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | Best for HK servos |
| eBay (EU Sellers) | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Fast shipping |
| Amazon | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐ | Premium price |
| AliExpress | ⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ | Slow but cheap |
| Local Hardware | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | No shipping delay |

---

## 📅 NEXT STEPS

1. ✅ **TODAY**: Copy this checklist and start ordering fast parts
2. ✅ **Week 1**: Collect all parts as they arrive
3. ✅ **Week 2**: Download InMoov finger CAD files
4. ✅ **Week 3**: Begin 3D printing hand parts
5. ✅ **Week 4**: Test servos individually
6. ✅ **Week 5**: Assemble and calibrate finger mechanism

---

**Created**: April 15, 2026  
**Status**: Ready to Order  
**Last Updated**: April 15, 2026
