# Fair Value Method — Semantic Shorthand Log
// reconstruct: study-guide //
// Status: active, v0.2 //
// Date: 2026-09-26 //
// Owner: KingofNothing //

:Log, title Fair Value Method (Steven)
:Status active
:Purpose durable inheritance log for the FVP/M valuation method; evolves by approved Delta only
:Version v0.2
// reconstruct: study-guide //

## 1. Locked equations
:FVP, formula M((Mc + NR) / (S + S*s)), note cash/debt OUT of floor; short interest inflates share count as apparent dilution
:MFVP, formula M(FVP * (1 + M_qtr)), horizon <=6 months (this quarter + next)
:LMFVP, formula M(FVP * (1 + M_long)), type future curve NOT a hold-to target
// LMFVP::v1 — treated as 52w target to hold to; superseded by v0.2 curve addendum //

## 2. Rating rule (P vs FVP only, 2% band)
:Rating, rule (|P - FVP| / FVP <= 2% -> fair; P < FVP-2% -> undervalued; P > FVP+2% -> overvalued)
:Rating, note M never redefines fair; M only builds targets above the floor

## 3. M law
:M_qtr, stack M_op + M_sent + M_asset + M_eps + M_lev + M_growth_qtr + mandatory subs
:M_6m, stack M_qtr with M_growth_6m
:M_long, more conservative booked stack + M_growth_52w + persistent sent
:M_contributor, rule each listed with reason; 0.00-0.02 stated but dropped from sum; no hard cap; user may retune any line
:M_lev, rule net cash positive / net debt negative as trader willingness-to-pay, separate from M_asset
:M_asset, rule 0 to negative only; high-upkeep assets (airlines, rails, miners); asset-light = 0
:TrendScore, rule T = r * 0.30 * (1 + a), r = 20d return, a = 20d ATR%; soft rail +/-0.12; vol multiplier scales Trend only
:M_interaction, rule |M_op| > |M_sent| -> M_sent += 0.05*sign(M_op); |M_sent| > |M_op| -> M_sent *= 0.95
:M_decay, rule news >30d old *= 0.5
:M_growth, rule split by clock: qtr / 6m / 52w; never copy QoQ G into 52w stack

## 4. Exit ladder (approved 2026-09-26)
:ExitLadder, H(1: FVP first take-profit if undervalued, 2: MFVP working swing exit or revaluation point, 3: LMFVP future curve advisory only)
:ShortSwing, rule look for FVP as first take-profit when undervalued
:Swing, rule MFVP is the target for exit OR revaluation with new data; recalculate rolling through quarter + next
:LMFVP, rule future curve: where MFVP points if extended 52w from current/historical data; NOT a hold-to target; rebuild on every major catalyst and print; direction signal only
// ExitLadder::v1 — LMFVP as 52w hold-to target; FVP/MFVP not ordered as ladder; superseded //

## 5. Modes
:AutoScout, no params -> aggregator triggers (insider, news+reaction, indicators) -> score/prune -> top 5 bull / 5 bear -> full method on survivors
:FilterScout, user params -> screen (e.g. Finviz) -> short list -> full method -> rank by chosen clock (FVP/MFVP/LMFVP gap), cap 10 undervalued, all three gaps shown
:SingleEval, one ticker -> full work doc: floor, M stack, targets, actuals, recommendation, optional back-test curve section

## 6. Evidence so far (tentative, not all promoted)
:AAPL, snap 2026-05-01, P 280.14, FVP 280.14, MFVP 321.19, LMFVP 332.39, 6m high 345.34 (ran +7.5% past MFVP), dilution kept Trend sane
:TSLA, snap 2026-04-23, P 373.72, FVP 366.06, MFVP 385.63, LMFVP 411.25, 6m high 453.40 then low 297.40; flatten-on-DeltaM is the trade
:TRANSCORP, snap 2026-09-25, FVP 39.68 vs old 30.24 (floor finally diverges), M_qtr -0.064
// Evidence::v1 — pre-dilution / pre-ladder tests; superseded in scoring by v0.2 rules //

## 7. Open / not locked
:Open, Trend knob 0.30 discussable; M_lev/M_asset exact maps; LMEFVP slope x4 unused; mid-cap NR/Mc>=3% test pending; crypto pair pending
:Open, EPIC indicator deferred entirely unless user raises it
