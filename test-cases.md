# KCC Calculator — Test Cases

All monetary values in Indian Rupees (₹). Expected outputs rounded to nearest ₹1,000 for CMPL.

---

## Test Case 1 — RBI Illustration (Full Composite)

**Scenario:** Paddy + Wheat cultivation, Dairy allied activity, Pump Set + Dairy Shed term loan.

### Inputs

**Component A — Crop Cultivation**
| Crop | Season | Area (Acres) | SoF (₹/Acre) |
|------|--------|-------------|--------------|
| Paddy | Kharif | 2 | 15,000 |
| Wheat | Rabi | 2 | 12,000 |

Insurance A: ₹2,000

**Component B — Allied Activities**
| Activity | Units | SoF (₹/Unit) |
|----------|-------|--------------|
| Cross-breed Cows (Dairy) | 2 | 35,000 |

Insurance B: ₹1,500

**Component C — Term Loan**
| Particulars | Year | Units | Cost/Unit (₹) |
|-------------|------|-------|--------------|
| Pump Set | 1 | 1 | 50,000 |
| Dairy Shed & Equipment | 1 | 1 | 1,50,000 |

### Expected Outputs

**Component A Calculation**
| Line | Calculation | Amount (₹) |
|------|-------------|------------|
| Sub-total A (crop base) | 2×15,000 + 2×12,000 | 54,000 |
| 10% post-harvest/consumption | 10% × 54,000 | 5,400 |
| 20% maintenance/tech/GAP | 20% × 54,000 | 10,800 |
| Insurance premium | Actual | 2,000 |
| **Year 1 Limit A** | 54,000 + 18,200 | **72,200** |

**Component A — Year-wise MPL**
| Year | Limit (₹) |
|------|-----------|
| Year 1 | 72,200 |
| Year 2 | 79,420 |
| Year 3 | 87,362 |
| Year 4 | 96,098 |
| Year 5 | 1,05,708 |
| **Year 6 ★** | **1,16,279** |

**Component B Calculation** *(consumption suppressed — Rule 1)*
| Line | Calculation | Amount (₹) |
|------|-------------|------------|
| Base | 2×35,000 | 70,000 |
| 10% consumption | Suppressed (A active) | 0 |
| 20% maintenance/tech | 20% × 70,000 | 14,000 |
| Insurance premium | Actual | 1,500 |
| **Year 1 Limit B** | 70,000 + 15,500 | **85,500** |

**Component B — Year-wise MPL**
| Year | Limit (₹) |
|------|-----------|
| Year 1 | 85,500 |
| Year 2 | 94,050 |
| Year 3 | 1,03,455 |
| Year 4 | 1,13,801 |
| Year 5 | 1,25,181 |
| **Year 6 ★** | **1,37,699** |

**Component C**
| Item | Amount (₹) |
|------|------------|
| Pump Set | 50,000 |
| Dairy Shed & Equipment | 1,50,000 |
| **Term Loan Total** | **2,00,000** |

**CMPL**
| | Amount (₹) |
|---|------------|
| A — Year 6 MPL | 1,16,279 |
| B — Year 6 MPL | 1,37,699 |
| C — Term Loan | 2,00,000 |
| Raw Total | 4,53,978 |
| **CMPL (rounded ₹1,000)** | **₹4,54,000** |

**Expected badge:** ⚡ Collateral required — limit > ₹3 lakh

---

## Test Case 2 — Component A Only (Small Farmer)

**Scenario:** Single crop, no allied activity, no term loan.

### Inputs

**Component A**
| Crop | Season | Area (Acres) | SoF (₹/Acre) |
|------|--------|-------------|--------------|
| Paddy | Kharif | 1 | 18,000 |

Insurance A: ₹1,200

### Expected Outputs

| Line | Calculation | Amount (₹) |
|------|-------------|------------|
| Sub-total A | 1×18,000 | 18,000 |
| 10% consumption | 1,800 | 1,800 |
| 20% maintenance | 3,600 | 3,600 |
| Insurance | 1,200 | 1,200 |
| **Year 1 Limit** | | **24,600** |

**Year-wise MPL**
| Year | Limit (₹) |
|------|-----------|
| Year 1 | 24,600 |
| Year 2 | 27,060 |
| Year 3 | 29,766 |
| Year 4 | 32,743 |
| Year 5 | 36,017 |
| **Year 6 ★** | **39,619** |

**CMPL = ₹40,000** *(rounded to nearest ₹1,000)*

**Expected badge:** ✓ Collateral-free — limit ≤ ₹2 lakh

---

## Test Case 3 — Flexi KCC (Marginal Farmer)

**Scenario:** Farmer with 0.5 hectare landholding; Flexi KCC toggle ON.

### Inputs
- Flexi toggle: **ON**
- Landholding: **0.5 ha**
- Manual limit entered: **₹35,000**

### Expected Output
- Flexi KCC Limit: **₹35,000**
- Components A, B, C: not applied (dimmed)

---

## Test Case 4 — Component A + C (Crop + Term Loan, No Allied)

**Scenario:** 3 crops across seasons, pump set investment. No dairy.

### Inputs

**Component A**
| Crop | Season | Area (Acres) | SoF (₹/Acre) |
|------|--------|-------------|--------------|
| Paddy | Kharif | 3 | 14,000 |
| Wheat | Rabi | 3 | 11,000 |
| Maize | Zaid | 1 | 10,000 |

Insurance A: ₹3,500

**Component C**
| Particulars | Year | Units | Cost/Unit (₹) |
|-------------|------|-------|--------------|
| Drip Irrigation | 1 | 1 | 80,000 |
| Tractor (shared) | 2 | 1 | 3,00,000 |

### Expected Outputs

| Line | Amount (₹) |
|------|------------|
| Sub-total A | 3×14,000 + 3×11,000 + 1×10,000 = 85,000 |
| 10% consumption | 8,500 |
| 20% maintenance | 17,000 |
| Insurance | 3,500 |
| **Year 1 Limit A** | **1,14,000** |

**Year-wise MPL A**
| Year | Limit (₹) |
|------|-----------|
| Year 1 | 1,14,000 |
| Year 2 | 1,25,400 |
| Year 3 | 1,37,940 |
| Year 4 | 1,51,734 |
| Year 5 | 1,66,907 |
| **Year 6 ★** | **1,83,598** |

| Component C | Amount (₹) |
|-------------|------------|
| Drip Irrigation | 80,000 |
| Tractor | 3,00,000 |
| **Term Loan Total** | **3,80,000** |

**CMPL = 1,83,598 + 0 + 3,80,000 = 5,63,598 → ₹5,64,000**

**Expected badge:** ⚡ Collateral required — limit > ₹3 lakh

---

## Test Case 5 — Component B Only (Allied, No Crop)

**Scenario:** Fisheries unit — no crop cultivation, no term loan.

### Inputs

**Component B**
| Activity | Units | SoF (₹/Unit) |
|----------|-------|--------------|
| Fish Culture (Pond) | 1 | 1,00,000 |

Insurance B: ₹2,500

### Expected Outputs

*(Since A is not active, 10% consumption is applied to B)*

| Line | Calculation | Amount (₹) |
|------|-------------|------------|
| Base B | 1×1,00,000 | 1,00,000 |
| 10% consumption | 10,000 | 10,000 |
| 20% maintenance | 20,000 | 20,000 |
| Insurance | 2,500 | 2,500 |
| **Year 1 Limit B** | | **1,32,500** |

**Year 6 MPL B ≈ ₹2,13,919**

**CMPL = ₹2,14,000**

**Expected badge:** ↑ Up to ₹3 lakh — tie-up / hypothecation applicable

---

## Test Case 6 — Insurance Double-Count Warning

**Scenario:** Both A and B active, both with insurance entered.

### Inputs
- Component A: any valid crop with insurance ₹1,000
- Component B: any valid activity with insurance ₹1,500

### Expected Behaviour
- ⚠️ Warning note appears in Component B section:
  > *"Insurance double-count check (Rule 2): Both A and B carry insurance. Verify these are distinct policies..."*
- ℹ️ Info note appears in both A and B:
  > *"No-double-counting (Rule 1): The 10% post-harvest / consumption add-on is applied in Component A only — suppressed in B."*

---

## Rounding Verification

| Raw Total (₹) | Expected CMPL (₹) |
|--------------|-------------------|
| 99,499 | 99,000 |
| 99,500 | 1,00,000 |
| 4,53,978 | 4,54,000 |
| 2,00,001 | 2,00,000 |
| 3,00,499 | 3,00,000 |
| 3,00,500 | 3,01,000 |
