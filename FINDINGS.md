# OVB / SIGNAL IDUNA "101 Invest" vs. DIY VWCE — Independent Analysis

**Verdict: Decline the offer. A low-cost global index fund (VWCE) held directly in a brokerage account beats the proposed insurance product on every leg that matters — risk-adjusted performance, all-in cost, and (correctly modeled) after-tax outcome.**

This is an independent analysis of a personalised investment proposal from an OVB Allfinanz (Romania) advisor. The proposal asks an existing index investor to redirect half of a €2,000/month VWCE contribution into a **SIGNAL IDUNA *101 Invest*** unit-linked life-insurance contract holding actively managed funds. The proposal page was AI-generated, so every figure was treated as a *claim to verify*, not a fact.

---

## 1. The setup

| | DIY (current) | OVB proposal |
|---|---|---|
| Vehicle | VWCE (Vanguard FTSE All-World, IE00BK5BQT80), 0.19% TER | SIGNAL IDUNA *101 Invest*, unit-linked life insurance |
| Access | Interactive Brokers (IBKR Ireland) | Insurance contract; 8-fund menu, switching free |
| Contribution modeled | €1,000/month (€12,000/yr) | €1,000/month (€12,000/yr) |
| Horizon | 15–30 years | 15–30 years |
| Tax (Romania, self-declared) | 16% income tax on gains, paid **once on sale** | Claimed exempt inside the contract |

The proposal's core claim: the insurance product's tax shelter and "0.90% all-in cost" let it **overtake the DIY ETF at ~year 11**.

---

## 2. Methodology & data sources

- **Fund performance:** daily NAV (EUR) for all 8 menu funds, 2020-06-09 → 2026-06-09, from SIGNAL IDUNA's own API (`life.signal-iduna.ro/api/funds/rate`), captured in `signal iduna performance/*.har`. Public page: **https://www.signal-iduna.ro/ro/evolutie-fonduri-eur**. Three single-day feed glitches (NAV briefly dropped to ~€2–3) were corrected by interpolation. Daily data resampled to month-end for the apples-to-apples comparison.
- **VWCE benchmark:** EUR monthly returns from justETF: **https://www.justetf.com/en/etf-profile.html?isin=IE00BK5BQT80#performance**
- **Fund risk/scenario data:** the 8 PRIIP KIDs in `signal iduna performance/signal iduna prospects/*.pdf`.
- **Cost schedule & projection:** the offer page `offer/index.html` (fee structure + the JS `DATA` array driving its charts).
- Metrics computed at monthly frequency, risk-free rate 2.5% EUR, common window **Jul 2020 → May 2026 (71 months)**.

---

## 3. Finding 1 — Performance: VWCE strictly dominates the menu

VWCE figures are **net** (0.19% TER already in price). Fund figures are **gross of the 0.9% insurance wrapper** — i.e., flattering to the product.

| Fund | CAGR | Vol | Sharpe | MaxDD | SRRI |
|---|---|---|---|---|---|
| **VWCE (FTSE All-World)** | **14.92%** | **12.63%** | **0.97** | **−13.3%** | 4 |
| SIFI USA Equity FoF *(only ~21mo data)* | 12.59% | 16.38% | 0.65 | −17.7% | 5 |
| SI BestSelect Class A | 9.12% | 11.32% | 0.61 | −17.8% | 3 |
| NB Aktien Global R | 9.70% | 13.59% | 0.57 | −20.1% | 4 |
| HANSAdynamic Class A | 7.71% | 10.52% | 0.52 | −17.7% | 3 |
| NB Aktien Europa R *(the "diversifier")* | 7.10% | 12.72% | 0.41 | −23.6% | 4 |
| HANSAcentro | 4.51% | 7.30% | 0.30 | −14.0% | 3 |
| HANSAsmart Select E (Class A) | 4.00% | 10.13% | 0.19 | −20.2% | 4 |
| TBF Global Income EUR R *("conservative")* | −1.20% | 7.71% | −0.44 | −18.2% | 3 |

**VWCE delivered the highest return, lower volatility than 6 of 8 funds, the shallowest drawdown of the entire set, and a Sharpe ~60% above the best full-history alternative.** This is strict dominance, not a risk/return trade-off — and it understates VWCE's edge, because the fund column is still gross of the wrapper. The fund pitched as the *diversifier* (NB Aktien Europa) was among the worst risk-adjusted performers; the *conservative* option (TBF) lost money.

*Caveat:* this 6-year window is one regime (US-led bull market). It disproves the proposal's specific "diversify & protect" claim but is not proof that VWCE wins on raw return in every future regime. The cost/structure argument below (Section 5) does not depend on the regime.

---

## 4. Finding 2 — The hidden cost layer

The offer headlines a **0.90% "reduction in yield."** That figure covers only the **insurance wrapper** (0.80% premium fee + 3.00% management charge + 2.5–5% sliding reference fee on each contribution, + 0.30%/yr on total value, + small fixed fees). It **excludes the underlying funds' own ongoing charges (TER)**.

Confirming the omission: each fund KID explicitly defers cost disclosure to the product KID (*"compoziția costurilor regăsiți în documentul cu informații esențiale (KID) pentru produsul 101 Invest"*) — so the fund documents show returns while hiding the fee that produced them. Active fund-of-funds of this type typically run **~1.5–2% TER**. Realistic all-in drag is therefore **~2.4%+ per year** (wrapper + fund TER), versus **0.19%** for VWCE.

The funds' own KID central ("moderate") 5-year scenarios sit in the low-to-mid single digits (e.g. SI BestSelect **4.7%/yr**) — **less than half the 10% gross the proposal's projection assumes for both sides.**

Additional structural costs: **surrender value is €0 in years 1–2** (per the offer's own data) and KIDs recommend a 5-year minimum hold — heavy front-loading and lock-in.

---

## 5. Finding 3 — Tax mechanics, correctly modeled

The proposal's spreadsheet was reconstructed exactly from `offer/index.html`:

- The DIY ETF is grown at **9.81% (10% gross − 0.19% TER) with no annual tax**, and **16% is applied once** to the cumulative gain at the exit year (`gain × 0.84` reproduces their "after-tax" column to the euro at years 10 and 20). So the proposal's tax mechanic is *technically correct*: an accumulating ETF defers tax until sale. It does **not** wrongly tax the ETF every year.

The decisive asymmetry, however, is structural:

- **VWCE's tax cost is a one-time 16% haircut on exit** ≈ only **~0.5–0.8%/yr** amortized over 20–30 years.
- **The product's cost is ~2.4%/yr, every year, compounding.**

A one-time haircut can never catch a recurring compounding drag. Tax deferral plus a cheaper fund wins decisively over the long horizon.

### Where the proposal's model actually misleads
Its "overtakes at year 11" result rests on two false premises:
1. It gives the product the **same 10% gross return as the index**, then charges it only the 0.9% wrapper, **silently omitting the funds' TER**.
2. The active funds **have not earned the index's return** (Section 3) — and even their own KID moderate scenarios are ~4–5%, not 10%.

---

## 6. Finding 4 — Corrected projections (€12,000/yr, contributions start-of-year)

| Horizon | Scenario A — *their* assumption (both 10% gross, wrapper only) | Scenario B — **fair**: equal 7% gross, full costs (1.5% fund TER + 0.9% wrapper) | Scenario C — historical (VWCE 14.9% vs best fund 9.1% NAV) |
|---|---|---|---|
| 10y | product +€5.8k | **VWCE +€11.7k (+7.5%)** | VWCE +€60.8k |
| 20y | product +€18.5k | **VWCE +€72.8k (+18.3%)** | VWCE +€575k |
| 30y | product +€4.1k | **VWCE +€262k (+33.6%)** | VWCE +€3.28M |

VWCE figures are after the one-time 16% exit tax; product figures are tax-free (accepting the proposal's own claim). **Even under the proposal's own doubly-charitable Scenario A, the product's lead is tiny and evaporates by year 30.** Under any fair costing (B) or the real track record (C), VWCE wins and the gap compounds.

---

## 7. Finding 5 — Non-cost claims don't hold up

- **No capital protection.** Every fund KID states plainly: *"Acest produs nu include nicio protecție împotriva evoluțiilor viitoare ale pieței… ați putea pierde integral sau parțial capitalul investit."* The cited "FGA guarantee" covers **insurer insolvency, not market loss** — irrelevant to a unit-linked product's investment risk.
- **Lock-in / front-loaded fees.** €0 surrender value in years 1–2; the heaviest charges hit first.
- **Conflict of interest.** OVB is commission-based; the front-loaded fees fund the commission.
- **Inheritance** is achievable via a brokerage beneficiary designation / will, and **diversification / factor tilts** (value, quality, momentum, regional) are achievable inside IBKR with cheap ETFs — neither requires the insurance wrapper.

---

## 8. Conclusion & recommendation

**Keep the full €2,000/month in VWCE via the brokerage account.** The insurance product trades a cheap, transparent, better-performing index fund for an expensive, opaque, worse-performing active wrapper whose only structural edge — deferred tax on exit — is far smaller than the recurring cost it imposes.

If broader factor exposure is desired (consistent with Fama-French), a low-cost small-cap-value / quality / momentum ETF inside the existing brokerage account delivers a *genuine* factor premium for a few basis points — the opposite of paying insurance-product cost for closet-active funds.

### If engaging the advisor further, request in writing:
1. The **101 Invest product KID** with the full cost table, and the **TER of each underlying fund**.
2. The **exact surrender-value schedule** for years 1–5.
3. Written confirmation that surrender gains are **exempt** from the 16% income tax + CASS under the current Fiscal Code (the entire tax case depends on this).
4. The **total commission/acquisition cost** taken from contributions, and its amortization period.

---

## 9. Repository contents & references

- `offer/index.html` — the AI-generated OVB proposal page (archived; personal data scrubbed).
- `signal iduna performance/*.har` — captured fund NAV data feed.
- `signal iduna performance/signal iduna prospects/*.pdf` — the 8 fund PRIIP KIDs.
- **SIGNAL IDUNA fund NAV (EUR):** https://www.signal-iduna.ro/ro/evolutie-fonduri-eur
- **VWCE (FTSE All-World) performance:** https://www.justetf.com/en/etf-profile.html?isin=IE00BK5BQT80#performance

## 10. Limitations & disclaimer
Historical metrics cover a single 6-year window and are not predictive. Fund TER (~1.5%) is an estimate pending the product KID. Tax treatment is per the Romanian Fiscal Code as understood in June 2026 and may change. **This document is an independent personal analysis, not investment, tax, or legal advice.**
