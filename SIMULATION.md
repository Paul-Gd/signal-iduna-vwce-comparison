# Simulation — €1,000/month: VWCE vs. SIGNAL 101 Invest

Where should €1,000/month (€12,000/yr) go — a low-cost index ETF (VWCE) in a brokerage account, or the OVB-proposed SIGNAL *101 Invest* insurance contract? This models both, month by month, across return and horizon assumptions.

## Assumptions

- **Contribution:** €1,000 at the start of each month, compounded monthly.
- **VWCE:** net return = gross − **0.19%** TER. Tax-deferred while held; **16% Romanian income tax applied once** to the cumulative gain at exit (self-declared, foreign broker).
- **101 Invest:** net return = gross − all-in cost. Gains assumed **tax-free at exit** (the proposal's own claim — see caveats). Modeled at two cost levels:
  - **0.90%/yr** — the offer's headline RIY, which covers only the wrapper and **ignores the underlying active funds' TER**.
  - **2.40%/yr** — realistic all-in: wrapper (~0.9%) **+ active-fund TER (~1.5%)**, consistent with the product KID's structure (its "−0.38% other recurring" line excludes the funds' charges).
- Both vehicles are given the **same gross return** — the most charitable assumption for the product (historically its active funds *trailed* VWCE; see `FINDINGS.md` §3).

> Surrender value is €0 for the product's first 3 years and below account value until ~year 11; these horizons (10y+) are past that, so exit value ≈ account value. Early exit would be far worse for the product.

---

## Central scenario — 7% gross, realistic product cost (2.4%/yr)

| Year | Paid in | VWCE (pre-tax) | **VWCE (after 16% tax)** | **101 Invest** | VWCE advantage |
|---:|---:|---:|---:|---:|---:|
| 1 | €12,000 | €12,438 | €12,368 | €12,297 | +€71 |
| 2 | €24,000 | €25,723 | €25,448 | €25,160 | +€288 |
| 3 | €36,000 | €39,913 | €39,287 | €38,614 | +€673 |
| 5 | €60,000 | €71,258 | €69,457 | €67,408 | +€2,049 |
| 10 | €120,000 | €170,317 | €162,266 | €151,812 | +€10,454 |
| 15 | €180,000 | €308,023 | €287,540 | €257,500 | +€30,039 |
| 20 | €240,000 | €499,455 | €457,942 | €389,838 | **+€68,104** |
| 25 | €300,000 | €765,572 | €691,080 | €555,546 | +€135,535 |
| 30 | €360,000 | €1,135,513 | €1,011,431 | €763,037 | **+€248,393** |

VWCE leads from year 1 and the gap compounds — **+€68k at 20 years, +€248k at 30 years**, even after paying the full 16% exit tax that the product avoids.

---

## Sensitivity matrix — final value by gross return × horizon

### If the product really costs only 0.90%/yr (offer's figure, fund TER ignored)
| Gross | Horizon | VWCE (net) | 101 Invest | Winner |
|---:|---:|---:|---:|:--|
| 5% | 10y | €148,117 | €147,938 | VWCE +0% |
| 5% | 20y | €373,540 | €369,037 | VWCE +1% |
| 5% | 30y | €722,627 | €699,478 | VWCE +3% |
| 7% | 10y | €162,266 | €164,118 | product −1% |
| 7% | 20y | €457,942 | €460,812 | product −1% |
| 7% | 30y | €1,011,431 | €997,180 | VWCE +1% |
| 10% | 10y | €186,731 | €192,097 | product −3% |
| 10% | 20y | €633,016 | €651,050 | product −3% |
| 10% | 30y | €1,740,979 | €1,747,568 | ~tie |

→ The product only ever "wins" here, and only barely, when you **both** ignore its fund TER **and** assume high returns at mid horizons. At low returns or very long horizons, VWCE still wins.

### Realistic — product costs 2.40%/yr (wrapper + fund TER)
| Gross | Horizon | VWCE (net) | 101 Invest | VWCE advantage |
|---:|---:|---:|---:|---:|
| 5% | 10y | €148,117 | €136,954 | **+8%** |
| 5% | 20y | €373,540 | €313,984 | **+19%** |
| 5% | 30y | €722,627 | €542,818 | **+33%** |
| 7% | 10y | €162,266 | €151,812 | +7% |
| 7% | 20y | €457,942 | €389,838 | +17% |
| 7% | 30y | €1,011,431 | €763,037 | +33% |
| 10% | 10y | €186,731 | €177,514 | +5% |
| 10% | 20y | €633,016 | €546,795 | +16% |
| 10% | 30y | €1,740,979 | €1,315,004 | **+32%** |

→ Once the active-fund TER is included, **VWCE wins in every cell**, by 5–33%, and the margin grows with the horizon.

---

## What this shows

**The entire investment case for the product rests on one hidden number: the underlying funds' TER.** Give the product the index's gross return *and* pretend its funds are free (0.9% only), and it can scrape a ~1–3% edge at mid horizons — the basis of the offer's "overtakes at year 11" pitch. Include the ~1.5% fund TER that the documents never disclose, and the product loses at every return and every horizon.

And this is still the *charitable* setup: it assumes the active funds match VWCE's gross return, which they have not (FINDINGS §3), and that the product's gains are genuinely tax-exempt (unverified — see the advisor questions in FINDINGS §8).

**Conclusion:** for a €1,000/month, long-horizon investor, keep the money in VWCE. The one-time 16% exit tax is a small, deferred cost; the product's recurring all-in fee is a large, compounding one — and compounding wins.

---

*Reproducible model; figures are illustrative, not guaranteed. See `FINDINGS.md` for data sources, the cost evidence, and limitations. Not investment, tax, or legal advice.*
