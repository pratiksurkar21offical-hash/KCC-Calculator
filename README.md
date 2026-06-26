# 🌾 KCC Composite Limit Calculator

**Kisan Credit Card (KCC) — Composite Maximum Permissible Limit (CMPL) Estimator**  
Built for bank credit managers per **RBI KCC Directions, 2026**

---

## Overview

A single-page, client-side web tool that calculates the **Composite Maximum Permissible Limit (CMPL)** for Kisan Credit Card facilities. No backend required — all calculations run in the browser.

The calculator covers all three components of a composite KCC facility over a **6-year tenure**:

| Component | Description |
|-----------|-------------|
| **A** | Working Capital for Crop Cultivation |
| **B** | Working Capital for Allied Activities |
| **C** | Investment Credit (Term Loan) |

---

## Live Demo

🔗 **[Open Calculator](https://claude.ai/code/artifact/a33b1a1b-8a96-4727-bccb-c46083b6bf29)**

---

## Screenshots

### Main Interface — Empty State
![KCC Calculator Empty State](screenshots/kcc-empty-state.png)

### Sample Data Loaded (RBI Illustration)
![KCC Calculator Sample Loaded](screenshots/kcc-sample-loaded.png)

---

## Features

- **Component A** — Multi-crop input (name, season, area in acres, Scale of Finance ₹/acre)
- **Component B** — Allied activity input (dairy, fisheries, poultry, etc.)
- **Component C** — Term loan line items with year-of-investment
- **6-year MPL escalation table** — 10% compound per year for A and B
- **Automatic add-ons** — 10% post-harvest/consumption + 20% maintenance/tech/GAP
- **Insurance premium** — Entered separately for A and B
- **Flexi KCC mode** — Simplified ₹10,000–₹50,000 limit for marginal farmers (≤ 1 ha)
- **Collateral badges** — Auto-flags collateral-free (≤ ₹2L), tie-up (≤ ₹3L), or collateral required (> ₹3L)
- **Print / Export PDF** — Full print CSS for sanction note output
- **Load Sample** — Pre-fills RBI illustration data for immediate testing

---

## Calculation Method

### Component A — Crop Cultivation

```
Sub-total A  = Σ (SoF/acre × acres) for all crops

Add-ons (Sub-total B):
  + 10% of Sub-total A   → post-harvest + household consumption
  + 20% of Sub-total A   → maintenance, tech, GAP certification
  + Insurance premium    → actual amount entered

Year 1 Limit = Sub-total A + Sub-total B

Year N Limit = Year (N-1) Limit × 1.10   [N = 2 to 6]
```

### Component B — Allied Activities

```
Base = Σ (SoF/unit × units) for all activities

Add-ons:
  + 10% of Base  → consumption (SUPPRESSED if Component A is active)
  + 20% of Base  → maintenance/tech
  + Insurance premium

Year 1–6 escalation: same 10% compound as Component A
```

### Component C — Term Loan

```
Term Loan Total = Σ (units × cost/unit) for all items
No escalation applied.
```

### CMPL

```
Raw Total = A (Year 6 MPL) + B (Year 6 MPL) + C (Term Loan Total)
CMPL      = Round(Raw Total, nearest ₹1,000)
```

---

## Business Rules Implemented

| Rule | Description |
|------|-------------|
| **No double-counting (Rule 1)** | If both A and B are active, the 10% consumption add-on is applied only in A and suppressed in B |
| **Insurance (Rule 2)** | Warning shown when both A and B carry insurance — user must verify distinct policies |
| **Flexi KCC** | Toggle for marginal farmers (≤ 1 ha); bypasses SoF calculation entirely |
| **Rounding** | All drawing limits rounded to nearest ₹1,000 |
| **Collateral-free** | Informational badge: ≤ ₹2 lakh collateral-free; ≤ ₹3 lakh tie-up/hypothecation |

---

## File Structure

```
KCC/
├── kcc-calculator.html     # Main application (single file, no dependencies)
├── README.md               # This file
├── tests/
│   └── test-cases.md       # Sample test scenarios with expected outputs
└── screenshots/
    ├── kcc-empty-state.png
    └── kcc-sample-loaded.png
```

---

## Usage

1. Open `kcc-calculator.html` in any modern browser — no server required
2. Click **⊕ Load Sample** to see the RBI illustration pre-filled
3. Or enter your own data in Components A, B, C
4. Results update live in the right-hand panel
5. Click **⬆ Print / Export PDF** for the sanction note

---

## Sample Output (RBI Illustration)

| Input | Value |
|-------|-------|
| Paddy — 2 acres, Kharif, SoF ₹15,000/acre | ₹30,000 |
| Wheat — 2 acres, Rabi, SoF ₹12,000/acre | ₹24,000 |
| Insurance A | ₹2,000 |
| Cross-breed Cows — 2 units, SoF ₹35,000/unit | ₹70,000 |
| Insurance B | ₹1,500 |
| Pump Set — 1 unit × ₹50,000 | ₹50,000 |
| Dairy Shed & Equipment — 1 unit × ₹1,50,000 | ₹1,50,000 |

| Component | Year 1 | Year 6 MPL |
|-----------|--------|------------|
| A | ₹72,200 | ₹1,16,279 |
| B | ₹85,500 | ₹1,37,699 |
| C | — | ₹2,00,000 |
| **CMPL** | — | **₹4,54,000** |

---

## Tech Stack

- **HTML5** + **Vanilla JavaScript** (ES6+)
- **CSS3** with custom properties (design tokens)
- Zero external dependencies — no npm, no build step
- Works offline after first load

---

## Regulatory Reference

> RBI Master Directions — Kisan Credit Card (KCC) Scheme, 2026  
> Reserve Bank of India, Department of Regulation

---

## License

For internal banking use. Not for commercial redistribution.
