The UK's Revenue-Maximising Top Tax Rate: A
Diamond-Saez Analysis Using HMRC Data
This project estimates the revenue-maximising top rate of UK income tax using the Diamond-Saez
framework, with every parameter derived from official HMRC statistics rather than assumed or
borrowed from a single external study. The exercise also tests, using HMRC's own published time
series, whether a simple do-it-yourself replication of the behavioural elasticity involved can
reproduce the literature's estimates - and finds that it cannot, for an instructive reason.
The Diamond-Saez framework
Diamond and Saez model the top of the income distribution as Pareto-distributed and derive a
closed-form expression for the revenue-maximising top marginal rate:
τ* = 1 / (1 + a·e)
where:
● a is the Pareto (inverse) shape parameter of the income distribution's upper tail — a lower a
means a thicker tail (income is more concentrated among the very highest earners)
● e is the elasticity of taxable income (ETI): the percentage change in reported taxable income
for a 1% change in the net-of-tax rate, (1 − τ)
The intuition is a standard trade-off: raising τ mechanically increases revenue from unchanged
income, but also reduces the reported income base as taxpayers work less, shift income into
non-taxable forms, or emigrate. The formula finds the rate at which these two effects exactly cancel.
Deriving the Pareto parameter from HMRC data
Source: HMRC's "Income Tax liabilities statistics" tables, specifically Table 2.1 (number of Income
Tax payers) and Table 2.4 (income shares and thresholds by percentile group), tax year 2023–24 —
the most recent outturn (non-projected) year in the release.
Two inputs were taken directly from the tables:
● Total Income Tax payers: 36,700,000
● Total income before tax, all taxpayers: £1,530 billion
For each top percentile band, the number of people above the threshold and the total income held
above it were derived as:
n_above = p × N_taxpayers income_above = (share of total income) × total income mean_above =
income_above ÷ n_above
Band Threshold Income
share
n_above mean_abov
e
Pareto a
(direct)
Top
25%
£45,000 53.3% 9,175,00
0
£88,882 2.03
Top
10%
£67,400 34.0% 3,670,00
0
£141,744 1.91
Top
5%
£93,600 24.6% 1,835,00
0
£205,112 1.84
Top
1%
£207,000 12.4% 367,000 £516,948 1.67
The direct estimate uses a = mean_above / (mean_above − threshold). A regression of
log(n_above) on log(threshold) across all four bands gives a second, independent estimate of a =
2.10.
The two methods disagree, and the direct estimate itself falls steadily moving further into the tail
(2.03 → 1.91 → 1.84 → 1.67). This is not an error — it shows the UK income distribution is not
perfectly Pareto-shaped; the very top is fatter-tailed than the rest of the top quartile. The Top 1%
direct estimate (a = 1.67) is used going forward, since it is the band actually affected by a top-rate
change.
A methodological note: an earlier version of this analysis computed mean_above by applying fixed
unit-conversion factors (assuming income and taxpayer-count columns were pre-scaled in millions
and thousands respectively) to a source table. That assumption happened to match a self-test built
to the same convention, which meant the test could not catch a mismatch with real data. The version
above avoids this entirely by deriving n_above and income_above from percentages and totals
directly, with no hidden scaling assumptions.
Estimating the elasticity of taxable income
Unlike the Pareto parameter, the ETI cannot be read directly off a single HMRC table — it requires
observing how income responds to an actual rate change. Two approaches were used.
Approach 1: the published literature
Source ETI estimate
HMRC (2012), Exchequer effect of the
50% additional rate
0.48
Brewer, Saez and Shephard (2008),
Mirrlees Review
0.46
IFS (Browne and Phillips, 2017)
re-analysis
0.31–0.83, depending on
year used
Saez, Slemrod and Giertz (2012),
international survey
0.12–0.40
HMRC's own 0.48 and IFS's 0.31 anchor the range most relevant to a UK top-rate question; the
wider international survey sets the outer bound at 0.12.
Approach 2: a DIY replication using HMRC's own time series
HMRC's Table 2.4 provides a genuine natural experiment: the additional rate fell from 50p to 45p in
April 2013. A difference-in-differences estimate compared the Top 1% (whose rate changed) against
the band immediately below — roughly the 95th–99th percentile — who remained on an unchanged
40% rate throughout:
ETI = [Δlog(mean income, Top 1%) − Δlog(mean income, control)] / Δlog(1 − τ)
Using average income in 2010–11/2011–12 (pre-reform) versus 2013–14/2014–15 (post-reform),
and excluding 2012–13 as a known "forestalling" year in which income was shifted across the
boundary in anticipation of the cut, this gives:
ETI (naive) ≈ 0.92
This is nearly double HMRC's own figure — high enough to warrant a check. Running the identical
method over a period with no rate change at all (2003–04 to 2006–07, before the additional rate
even existed) produced an "excess growth" of the Top 1% over the control group of 0.136 log points,
comparable in size to the 0.087 log points attributed to the actual 2013 reform.
Finding: most of the naive 0.92 estimate reflects a pre-existing tendency for top incomes to grow
faster than the band just below them — for reasons unrelated to tax policy (e.g. globalised
pay-setting, executive compensation trends) — rather than a genuine behavioural response to the
rate cut. A simple two-group comparison cannot separate these two effects; this is precisely why the
academic literature relies on individual-level panel microdata and formal trend controls rather than
aggregate percentile snapshots. The 0.92 figure should be read as an upper bound on what a naive
method can detect, not as a competing point estimate.
Results
Using a = 1.67 (HMRC 2023–24, Top 1% direct estimate) and the literature's credible ETI range:
Elasticity (e) Optimal top rate (τ*) Source
0.31 65.9% IFS (2017)
0.40 60.0% Central working estimate
0.48 55.5% HMRC (2012)
The current UK top rate is 45%. Across the full credible elasticity range, the analysis implies the
revenue-maximising rate sits somewhere in the high-50s to mid-60s percent — notably above the
current rate, though the exact figure is highly sensitive to which elasticity estimate is used, and that
estimate is itself genuinely contested.
Limitations
● Static, partial-equilibrium model. No general equilibrium effects (e.g. wage effects of
large-scale behavioural change), no interaction with other taxes (National Insurance,
dividend tax), no migration response.
● Single-year Pareto snapshot. The distribution's shape is estimated from one tax year; a
time-varying Pareto parameter is not modelled.
● Elasticity uncertainty dominates the result. The Pareto parameter is precisely measured from
administrative data; the elasticity is not, and the optimal-rate estimate inherits that
imprecision directly.
● The DIY elasticity estimate is illustrative, not a finding. Its main value is methodological —
demonstrating why naive replication overstates ETI — rather than as a number to be used in
the headline calculation.
Conclusion
Combining HMRC's administrative income data with the Diamond-Saez framework produces a
Pareto parameter that can be measured with reasonable precision, and an optimal top tax rate that
is highly sensitive to a contested behavioural elasticity. Attempting to estimate that elasticity
independently, directly from HMRC's own published time series, did not resolve the uncertainty — it
demonstrated why the uncertainty exists: aggregate percentile data cannot cleanly separate a
genuine tax response from a pre-existing income trend. The credible range this analysis supports is
an optimal top rate of roughly 55–66%, meaningfully above the current 45%, but the width of that
range is itself the main empirical conclusion.
