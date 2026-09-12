# SLS (SELLAS Life Sciences) — Due Diligence

Bear/short-leaning options thesis on **SELLAS Life Sciences (NASDAQ: SLS)**, centered on
the binary **REGAL Phase 3 readout**. This repo holds the due-diligence workbook
(`SLS.xlsx`) and this readout of where things stand.

**Status as of 2026-09-11: pre-readout.** REGAL has not reported topline. All figures
below decay fast — re-verify price, cash, and event count before relying on this.

> Not financial advice. A research artifact for sizing a defined-risk position, not a
> prediction of the outcome.

## TL;DR

The market is pricing GPS (galinpepimut-S) to work. The bear case says it probably
doesn't, and the WT1-vaccine base rate agrees. If REGAL misses, the stock's fundamental
floor — cash plus a discounted credit for the second asset, SLS009 — is **$0.75–$1.59/
share** against a spot price of **$11.55**, i.e. 86–94% downside. That floor, not a
prediction of the readout, is what a long-put strike gets set against. See
[`REGAL Failure Floor` tab](#regal-failure-floor-headline-output) below.

## The Company

Late-stage oncology microcap, two assets:

- **Galinpepimut-S (GPS)** — tetravalent, heteroclitic WT1 peptide vaccine licensed from
  Memorial Sloan Kettering. In pivotal Phase 3 **REGAL** (NCT04229979) as maintenance
  therapy for AML patients in second complete remission (CR2/CRp2) who are
  transplant-ineligible. Primary endpoint: overall survival.
- **SLS009 (tambiciclib)** — CDK9 inhibitor, Phase 2 front-line AML.

## The Bear Case

1. **Trial duration tells you nothing about who's winning.** REGAL is event-driven
   (needs 80 deaths) and has run far longer than modeled. A slow event pace is equally
   explained by the blinded control arm outliving the company's ~8-month baseline
   estimate (blinded pooled median OS was disclosed at ≥13.5 months) as by "the drug
   works." You cannot tell the difference from outside the blind.
2. **Cancer-vaccine base rate is poor; WT1 is a hard single-antigen target.** The closest
   analog, **OCV-501** (WT1 vaccine, AML maintenance), failed its randomized Phase 2 (DFS
   12.1 vs 8.4 mo, p=0.77). NeuVax, rindopepimut, and tecemotide all failed despite
   immunogenicity. Provenge is the only approved cancer vaccine, and its efficacy is
   debated.
3. **Mechanistic doubt.** WT1 is a self-antigen (central tolerance → weak T-cell
   response); the heteroclitic design that boosts immunogenicity can reduce recognition
   of the native tumor epitope. Immunogenicity ≠ tumor kill. AML in CR2 has already
   escaped one line of therapy and can downregulate MHC/WT1.
4. **Selection bias.** Exclusion criteria and enrollment of healthier, favorable-risk
   patients can inflate pooled survival independent of any drug effect.

### Steelman (counter-points, kept honest)

GPS's science is real (MSK provenance, inventor David Scheinberg on the board); CR2
maintenance in a low-disease-burden setting is where vaccines have their best shot;
REGAL has passed IDMC futility/interim review without modification; the one randomized
GPS dataset (mesothelioma, small, underpowered) showed a numerical trend (OS 22.8 vs
18.3 mo, HR 0.79). This is a probability-weighted tilt toward failure, not a certainty —
and the market disagrees hard (stock ~6x'd over 12 months; analyst targets $30–35).

### Source-quality note

Part of the public bear narrative traces to Martin Shkreli — a sharp biotech analyst
*and* a convicted securities fraudster talking his own book, who has also recently missed
publicly on another call (Capricor). There is independent corroboration (a Seeking Alpha
"Sell" thesis makes the same selection-bias/NeuVax-precedent argument). Weight the
analysis, discount the confidence.

## Current Key Facts (as of 2026-09-11 — re-verify before use)

| Item | Value | Source / date |
|---|---|---|
| REGAL events (company-confirmed) | 78 of 80 required | Reaffirmed via 3D Medicines, 8/18/26 |
| Unconfirmed 3rd-party report | Claims event 80 hit; **not confirmed by SELLAS** | AktienCheck, ~8/23/26 — treat as rumor |
| REGAL topline guidance | Q4 2026 (real risk of slipping to Q1 2027) | Company |
| SLS009 front-line Ph2 topline | Also guided Q4 2026 (28/80 enrolled) | Q2'26 update, 8/11/26 |
| Price | $11.55 (-14.4% same day, no company news) | Close, 9/11/26 |
| Shares outstanding | 201,945,709 | 10-Q cover page, 8/10/26 |
| Market cap | ~$2.33B | Derived |
| Cash | $138.3M | 10-Q balance sheet, 6/30/26 |
| Debt | $737K (operating lease liabilities only) | 10-Q balance sheet, 6/30/26 |
| H1'26 operating cash burn | $16.4M (~$8.2M/quarter) | 10-Q cash flow statement |
| ATM facility | $150M shelf via TD Cowen, unused | Established 3/26, confirmed unused as of Q2'26 |
| Enterprise value | ~$2.19B | Derived (`Main` tab) |

Full sourcing (SEC EDGAR links, exact filing language) is in the cell comments on the
`Main` and `REGAL Failure Floor` tabs.

## What's in `SLS.xlsx`

| Tab | Contents |
|---|---|
| `Main` | Cap table (price, shares, cash, debt → MC, EV via formula). Refreshed 9/11/26 from Q3'24 vintage. |
| `galinpepimut-S` | Clinical-trial notes + WT1-vaccine literature review (OCV-501, mesothelioma OS by CR line, etc.). |
| `WT1` / `Literature` | Supporting mechanism and literature notes. |
| `Trial` | Month-by-month REGAL enrollment/deaths tracker (2020→). |
| `Patients` | Patient-level survival simulation (live `RANDBETWEEN`), no assumed arm separation. |
| `18mo Scenario` / `24mo Scenario` | Frozen simulation runs testing whether the observed event pace is reproducible under 18/24-month median OS with **no drug effect** — the quantitative core of bear point #1. |
| `REGAL Failure Floor` | Per-share SOTP floor conditional on GPS failing. See below. |

### `REGAL Failure Floor` — headline output

Net cash at readout (current cash less burn through the guided readout window) plus a
scenario-based credit for SLS009, divided by current shares:

| Scenario | SLS009 risk-adj. value | Implied floor ($/share) | Downside from $11.55 spot |
|---|---|---|---|
| Low | $30M | **$0.75** | −93.5% |
| Mid | $100M | **$1.10** | −90.5% |
| High | $200M | **$1.59** | −86.2% |

This is a **conditional-on-failure floor**, not an expected value or a price target — it's
the reference level a long-put strike gets set against. A shocking miss can gap the stock
below this floor intraday before any mean-reversion.

## Conventions

- Blue font = hardcoded input; black = formula; yellow fill = key assumption to revisit.
- Every hardcoded number carries a dated, sourced cell comment.
- Formulas only, never pasted results — the sheet recalculates when inputs change.
- Formulas are verified via a GitHub Actions workflow (`.github/workflows/recalc.yml`)
  that runs headless LibreOffice on a disposable runner and fails on any Excel error
  value, since this machine doesn't have LibreOffice installed locally.

## Sources

- Company IR: [ir.sellaslifesciences.com](https://ir.sellaslifesciences.com)
- SEC EDGAR, Q2'26 10-Q: [sls-20260630.htm](https://www.sec.gov/Archives/edgar/data/0001390478/000139047826000012/sls-20260630.htm)
- Trial registry: [NCT04229979](https://clinicaltrials.gov/study/NCT04229979) (REGAL)
- 3D Medicines (Greater China licensee, "3D189") disclosures — event-count corroboration
- Seeking Alpha, "Sellas Life Sciences: REGAL Trial's Delayed Events Signal Selection
  Bias" (Jul 2026, Sell)
- Comparator: OCV-501 Phase 2 (WT1 vaccine, AML) — PubMed/Springer
- Original workbook source: [martinshkreli/models/SLS.xlsx](https://github.com/martinshkreli/models/blob/main/SLS.xlsx)

## Standing Caveats

- Every figure here is dated and moves; re-pull before acting.
- This is a **binary** event. The model informs position sizing; it does not predict the
  outcome. The steelman case above is real — keep it in view.
- Not financial advice.
