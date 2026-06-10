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
- **Fund risk/scenario data & product costs:** the 8 fund PRIIP KIDs plus the **product KID** (`KID-...-SIGNAL-101-Invest.pdf`) in `signal iduna performance/signal iduna prospects/`.
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

## 4. Finding 2 — The hidden cost layer (confirmed by the product KID)

The product's own PRIIP KID (`...SIGNAL-101-Invest.pdf`, €500/yr example, 20-yr term) gives the authoritative reduction-in-yield (RIY) — and it is **heavily front-loaded**:

| Exit at | Cumulative cost | RIY/yr |
|---|---|---|
| 1 year | €500 (100% — surrender value is zero) | 100% |
| 5 years | €697.66 | 11.08% |
| 10 years | €895.30 | 3.87% |
| 20 years | €1,011.58 | **1.17%** |

The offer's headline **0.90%** is roughly defensible *only* at the €12,000/yr premium (fixed costs dilute); the authoritative figure at the example premium is **1.17%**, and the front-loading (11% at 5y) is the real story — you pay the most when you have the least, and **surrender value is €0 for the first 3 full years**.

**The hidden-TER problem is now proven, not inferred.** The KID's cost composition lists *"Alte costuri recurente: −0.38%/an"* — implausibly low for actively managed funds. The underlying funds' ~1.5% TER is evidently **not** included, while each fund KID points *back* to this document for costs (*"compoziția costurilor regăsiți în KID-ul produsului 101 Invest"*). Nowhere is the combined figure disclosed. Realistic all-in drag is therefore **~2.4%/yr** (front-loaded wrapper + fund TER), versus **0.19%** for VWCE — matching the Scenario B assumption below.

**The insurer's own "moderate" 20-year scenario is a loss:** €8,025.97 returned vs €9,970.20 paid in = **−0.95%/yr** (at the €500/yr example, where front-loaded costs bite hardest; less severe at €12k/yr, but a *negative central estimate over 20 years* is damning). The favorable scenario is +12.43%/yr, so the proposal's "10% gross" sits near the optimistic end. The funds' own KID moderate 5-year scenarios are likewise low single digits (e.g. SI BestSelect **4.7%/yr**) — far below the 10% the projection assumes.

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

- **No capital protection.** The product KID states plainly: *"Acest produs nu include nicio protecție împotriva performanței viitoare a pieței… puteți pierde toată investiția dumneavoastră sau o parte din aceasta."* The cited "FGA guarantee" (Legea 213/2015) covers **insurer insolvency, not market loss** — irrelevant to a unit-linked product's investment risk.
- **Lock-in / front-loaded fees.** Surrender value is **€0 for the first 3 years**; RIY is 11% at year 5, falling to ~1.2% only by year 20. Recommended holding period is **20 years**. The heaviest charges hit first.
- **Currency risk.** The KID flags *"Atenție la riscul valutar! Randamentul final… depinde de cursul RON/EUR."*
- **Bundled life cover you may not need.** It is a death-benefit policy; a mortality premium is deducted from each contribution, and exiting early forfeits the cover. The KID warns the product *"nu este simplu și poate fi dificil de înțeles."*
- **Conflict of interest.** OVB is commission-based; the KID confirms its figures *include* distributor/advisor costs — the front-loaded fees fund the commission.
- **Inheritance** is achievable via a brokerage beneficiary designation / will, and **diversification / factor tilts** (value, quality, momentum, regional) are achievable inside IBKR with cheap ETFs — neither requires the insurance wrapper.

---

## 8. Conclusion & recommendation

**Keep the full €2,000/month in VWCE via the brokerage account.** The insurance product trades a cheap, transparent, better-performing index fund for an expensive, opaque, worse-performing active wrapper whose only structural edge — deferred tax on exit — is far smaller than the recurring cost it imposes.

If broader factor exposure is desired (consistent with Fama-French), a low-cost small-cap-value / quality / momentum ETF inside the existing brokerage account delivers a *genuine* factor premium for a few basis points — the opposite of paying insurance-product cost for closet-active funds.

### If engaging the advisor further, request in writing:
1. The **TER of each underlying fund** and confirmation of whether it is *additional* to the product KID's 1.17% RIY (the −0.38% "other recurring" figure suggests it is not included).
2. Written confirmation that surrender gains are **exempt** from the 16% income tax + CASS under the current Fiscal Code (the entire tax case depends on this).
3. The **total commission/acquisition cost** taken from contributions, and its amortization period.
4. The **death-benefit (sum assured)** and the annual mortality premium deducted — i.e., how much of each contribution is *not* invested.

---

## 9. Repository contents & references

- `offer/index.html` — the AI-generated OVB proposal page (archived; personal data scrubbed).
- `signal iduna performance/*.har` — captured fund NAV data feed.
- `signal iduna performance/signal iduna prospects/*.pdf` — the 8 fund PRIIP KIDs **and the product KID** (`KID-...-SIGNAL-101-Invest.pdf`, the authoritative cost/scenario document).
- **SIGNAL IDUNA fund NAV (EUR):** https://www.signal-iduna.ro/ro/evolutie-fonduri-eur
- **VWCE (FTSE All-World) performance:** https://www.justetf.com/en/etf-profile.html?isin=IE00BK5BQT80#performance

## 10. Limitations & disclaimer
Historical metrics cover a single 6-year window and are not predictive. Fund TER (~1.5%) is an estimate pending the product KID. Tax treatment is per the Romanian Fiscal Code as understood in June 2026 and may change. **This document is an independent personal analysis, not investment, tax, or legal advice.**
