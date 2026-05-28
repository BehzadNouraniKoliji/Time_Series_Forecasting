# I am going to elaborate on some advanced points in time series forecasting within the context of this dataset.


### On Data Leakage during cross-validation.

A truly leakage-free process would do this inside each rolling fold:

1. split train/validation
2. fit scaler only on train
3. transform train
4. transform validation using train scaler
5. train model
6. predict
7. compute RMSE

That is the production-realistic evaluation pipeline. This ensures the validation fold is always treated as "unseen future data," with no statistical information (mean, variance) leaking from it into the preprocessing step, perfectly mirroring how the model would behave on truly new data in production.
