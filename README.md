# econ3916-lab04-anomaly-detection-
Lab 04 Submission

# Robust Statistics -- Automated Anomaly Detection

## Objective
I wanted to see how outliers affect different summary statistics, and whether a simple rule-based method or a machine learning method does a better job finding them in California housing data.

## Methodology
- Calculated the mean, median, trimmed mean, standard deviation, IQR, and MAD on the California Housing dataset (20,640 observations).
- Wrote my own Tukey Fences function to flag price outliers using Q1, Q3, and the IQR.
- Ran Isolation Forest on the full set of features to find unusual observations across all columns at once, not just price.
- Compared the two methods and found they didn't always flag the same rows.
- Added 5% corrupted values to the data and checked how much each statistic moved.

## Key Findings
- After adding 5% corrupted values, the mean shifted by [YOUR VALUE]%, while the median only shifted by [YOUR VALUE]%.
- The statistics built to resist outliers (median, trimmed mean, IQR, MAD) held steady even with corrupted data, while the mean and standard deviation moved more.
- Tukey Fences and Isolation Forest didn't flag the same observations. Tukey only looks at one column, so it can miss unusual combinations across multiple features that Isolation Forest catches.
- Some of the flagged "outliers" turned out to be a known data limit ($500,001 price cap), not real extreme values, which shows why I need to check what's behind a flag before deciding what to do with it.
