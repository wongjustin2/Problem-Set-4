# Problem Set 4 -- The Model That Fit Too Well

I rebuilt a store revenue model that reported an R-squared of 0.94 but kept over-forecasting the biggest stores, and this is the handover note for the honest version.

This model predicts each store's monthly revenue from floor area, foot traffic, local median income and years open, and it adds floor area squared and cubed so revenue can grow more slowly for the biggest stores. Its honest expected error is about \$17,200 a month (95% CI \$15,800 to \$18,900) from nested 5-fold CV, which is about 5% of the average store's \$373,000 a month.

It will fail in two cases, first for the biggest stores because their revenue is more spread out so their forecasts miss by more than the average error, and second for any store outside 8,000 to 45,000 square feet or with a new store format because the curve can bend the wrong way outside the sizes it learned from.

Next I'd build a version that gives each store its own error range that grows with store size, and I'd look for new predictors like local competition instead of collecting more stores because the learning curve shows more stores won't lower the error much. I'd also check the error every month on new data the model hasn't seen so the stated error stays honest.
