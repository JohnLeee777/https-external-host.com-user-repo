1. Pricing & Trading: EUR Interest Rate Swap
Scenario: Client requests 5-year €50M swap (receive fixed)
Process:
Benchmarking:
Check Bloomberg SWPM: 5Y mid-market rate = 2.85%
Review interdealer broker screens (ICAP/Tullett): 2.84-2.86%
Adjustments:
Credit charge (CVA): +3bps (client CDS = 120bps)
Liquidity premium: +2bps (month-end balance sheet constraints)
Final Quote:
"We'd pay 2.80% fixed vs 6M EURIBOR, or receive 2.90%. Current executable size: €50M."
Execution:
Hedge with €50M offsetting swap at 2.87% (capturing 3bps spread)
Confirm trade via DTCC SI portal for EMIR reporting
--------------------------------------------------------------------------
2. Structuring: Callable Step-Up Corporate Bond
Client Need: Municipality seeking callable 7-year funding
Structure:
Base Terms:
Bullet bond @ 4.0% (vs 7Y Bund + 180bps)
Call Option Pricing:
Black-76 model: σ=15%, forward rates = 3.7%
Call premium = 110bps (calculated via PDE solver)
Final Product:
Years 1-3: Coupon 5.1% (4.0% + 1.1%)
Year 4+: Coupon steps to 6.0% if not called
Callable annually after Year 3 at 102, 101, 100
Yield Advantage: Saves issuer 35bps vs straight bond
---------------------------------------------------------------------------
3. Position Management: Bund Futures Portfolio
Portfolio:
Long 500x 10Y Bund futures (DV01 = €8,500/contract)
Short 300x 5Y Bobl futures (DV01 = €4,200/contract)
Action:
Calculate Net DV01:
(500 × 8,500) - (300 × 4,200) = €2.99M
Hedge Ratio:
ECB speech expected → estimated 10bp move
Required hedge: 2,990,000/8,500 ≈ 352 contracts
Execution:
Sell 350x 10Y futures via block trade (avoiding market impact)
Result: Reduced VaR from €299K to €42K
-----------------------------------------------------------------------------------
4. Market Analysis: ECB Policy Shift
Observation: ECB signals pause after June 2024 cut
Analysis:
Forward Rates:
Dec-24 ESTR futures imply 3.15% vs current 3.25%
1Y1Y forward swap rate = 2.90%
Strategy:
Buy 2Y Schatz futures (benefits from delayed cuts)
Sell 10Y Bund futures (curve steepener)
Validation:
PCA analysis shows 2Y rates have 92% correlation to ECB speeches
--------------------------------------------------------------------------------------
5. Hedge Management: Bank NII Protection
Challenge: Protect €200M deposit book from falling rates
Solution:
Calculate Sensitivity:
Deposits duration = 0.5Y → €200M × 0.5 = €100M DV01
Hedge Instrument:
2Y EONIA swaps (DV01 = €1,950 per €1M)
Notional = 100,000/1,950 ≈ €51.3M
Execution:
Receive fixed on €51M 2Y swap @ 3.10%
Tested effectiveness: 89% per IFRS 9
--------------------------------------------------------------------------------------
6. Data & Reporting: VaR Backtesting
Daily Process:
Inputs:
500 historical scenarios
Portfolio: €80M IRS, €45M futures
Calculation:
Report:

Metric	Value	Limit
1D 95% VaR	€142K	€200K
Max Drawdown	€89K	€150K
Action: Flag 2 outlier trades exceeding stress thresholds
----------------------------------------------------------------
7. Cross-Departmental Project: FRTB Implementation
Initiative: Adopt Fundamental Review of Trading Book standards
Contributions:
Trading Desk Input:
Mapped 1200 positions to liquidity horizons (LH1-LH4)
Validated ES model parameters for rates book
IT Collaboration:
Developed Python script to reconcile SMM vs. DRC calculations:
python
Copy
def check_drc():
    if capital_charge > limit:
        alert_risk_team()
Result: Reduced capital charge by 18% through hedge accounting
--------------------
