# Player_retention_analysis
Cohort retention, LTV, and responsible gambling analysis on real payment transaction data using Python
Overview 

Analysis of real payment transaction data from a US-based online casino and 

sportsbook platform, examining player retention, lifetime value by vertical, and 

behavioral signals relevant to responsible gambling, using cohort analysis and statistical 

testing in Python. 

Business Question 

Which players are truly valuable to the business, not just by total deposit volume, but by 

how long they stay engaged, and which behavioral patterns should be monitored from a 

responsible gambling standpoint? 

Dataset 

Real, public data: Raw payments transaction data from online casino players and online 

sports bettors  

https://data.mendeley.com/datasets/9j5gcygnwg/1  

586,781 transactions across two brands: a casino-focused brand and a sports-focused brand 

~7,900 unique players, transaction-level data (deposits and withdrawals), with 

timestamp, amount, status, and an anonymized customer ID 

This dataset supports retention,LTV, and payment-pattern analysis 

Tools & Methodology 

Python (pandas, matplotlib/seaborn, scipy) in Google Colab. 

1. Cohort analysis: players were grouped by the month of their first deposit, then 

tracked for what percentage of each cohort remained active (made a deposit) in 

each subsequent month, visualized as a retention heatmap 

2. LTV comparison: total deposits per player were aggregated by brand (casino vs. 

sports) and compared with an independent-samples t-test 

3. Net position analysis: deposits minus withdrawals per player, to identify players the 

operator is net-negative on 

4. Escalation proxy: compared each player’s deposit total in their first 3 months vs the 

following 3 months, flagging those with 2x or greater growth as a simple, transparent proxy for responsible-gambling monitoring 

Key Findings 

1. Retention weakens in later cohorts Players who joined in mid-2019 were retained 

noticeably better than those who joined in late 2019 / early 2020. For example, the 

November 2019 cohort lost roughly 90% of players within just 4 months, a steeper 

drop-off than earlier cohorts. This suggests traffic quality or product experience may 

have degraded over the period studied, however, the data can’t say why, but it flags where to 

investigate further. 

2. Sports players have higher average LTV, but both distributions are highly skewed 

Brand Mean deposit/player Median 

Casino $5,262.69 / $400 

Sports $8,408.43 / $1,382.68 

The difference is statistically significant (t = -5.56, p < 0.001). However, the large gap 

between mean and median in both brands shows a small number of high-value players drive most of the volume; mean LTV alone overstates what a “typical” player is worth. 

3. A small share of players are net-negative for the operator 2.2% of players (126 

of ~5,700 with both deposit and withdrawal activity) withdrew more than they 

deposited, some by over $100,000, likely reflecting large one-off wins. 

4. About 19% of players show a strong deposit escalation signal Comparing each 

player’s first 3 months of activity to their next 3 months, 586 players (19%) showed 2x 

or greater growth in deposit volume, with the most extreme cases showing 100x+growth. This is a simple, transparent proxy, not a clinical diagnosis, but it mirrors the type of early-warning signal regulated operators are expected to monitor for player protection. 

Limitations 

Escalation proxy is simplistic: it flags deposit growth only; real responsible-gambling systems also weigh session frequency, time-of-day patterns, loss-chasing behavior, and self-exclusion signals. This should be read as a starting screen, not a diagnostic tool. 

Highly skewed distributions: mean-based comparisons (e.g., the t-test on LTV) are statistically valid but should be read alongside median values given the influence of high-value outliers. 

Repository Contents 

File Description 

Online_casino_DIB.csv, 

Online_sports_DIB.csv - Raw source data (Mendeley) 

igaming_analysis.ipynb - Full Python analysis (Google Colab notebook) 

retention_heatmap.png - Cohort retention visualization 

How to Explore 

Open igaming_analysis.ipynb in Google Colab, the notebook runs top to bottom on the two source CSVs. 

Author 

Maria M., Business Analytics student 

 
