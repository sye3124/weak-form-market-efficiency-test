# Cross-Sectional Asset Pricing Signals: Testing Predictability and Portfolio Performance in Nasdaq Stocks

## Project Category
*Business & Finance Tools* | *Data Analysis & Visualization*

---

### Problem Statement and Motivation  
Recent empirical asset pricing literature shows that many firm charachteristics (size, vlaue, momentum, profitability, investment, volatility, etc.) exhibit **cross-sectional predictability**: differences in characteristics across stocks help explain **differences in expected returns**.
This is distinct from **time-series forecasting**, which focuses on predicting the future return of a single asset.

In this project, I aim to investigate whether **cross-sectional signals derived from firm characteristics and factor exposures** can generate economicaly meaningfull improvements in portfolio formation within the Nasdaq universe.
I will evaluate whether these characteristics contain systematic information about expected returns and whether such information translates into higher out-of-sample Sharpe ratios.

---

### Planned Approach and Technologies  

1. **Data & Features**
- Daily or monthly Nasdaq stock returns
- Firm characteristics (size, momentum, volatility, book-to-market proxy, beta estimates, etc.)
- Factor exposures estimated via rolling regressions (e.g., market beta, SMB, HML loadings)

2. **Cross-Sectional Modeling Approaches**
I will compare several cross-sectional return prediction models, including:
- **Linear models** (e.g., cross-sectional OLS predicting next-period returns using characteristics)
- **Regularised regression** (Lasso/Ridge)
- **Tree-based methods** (Random Forest, Gradient Boosted Trees)

Each model will predict the **cross-sectional ranking** or level of next-period returns, not individual stock time-series returns.

3. **Portfolio Formation**
- From decile portfolios based on predicted returns or predicted risk-adjusted returns.
- Evaluate out-of-sample performance: average returns, volatility, Sharpe, turnover, maximum drawdown.

4. **Model Comparision**
I will implement a **formal model-comparison procedure**, including:
- **Out-of-sample R²** and mean absolute forecast error
- **Diebold-Mariano tests** for significant differences in predictive accuracy
- **Information criteria (AIC/BIC)** where applicable
- **Sharpe ratio significance tests** (e.g., Jobson-Krokie or bootstrap)
This ensures rigorous evaluation of model performance and avoids informal comparisions.

5. **Technologies**
- `pandas`, `NumPy` for data manipulation
- `matplotlib` for visualisations
- `scikit-learn` for ML models
- `statsmodels` for factor regressions
- `Numba` for accelerating repeated portfolio optimisation steps (if needed)

---

### Expected Challenges and Mitigation   

| Challenge | Approach |
|------------|-----------|
| **Overfitting in cross-sectional ML** | Use rolling-window expanding or fixed OOS windows; apply regularisation. |
| **Noisy return data** | Use portfolio aggregation and robust statistical tests. |
| **High turnover in predicted portfolios** | Incorporate simple transaction cost estimates or smoothing. |

---

### Success Criteria  
The project is successful if:
1. The pipeline correctly implements **cross-sectional predictions** instead of time-series forecasting.
2. Models produce statistically measurable differences in predictive accuracy validated via formal model comparison.
3. Portfolio results show **economically interpretable** performance (positive or negative).
4. All results are reproducible with clear code, tests, and configuration files.
5. Findings connect directly to the asset pricing literature and reflect theoretical expectations.

---

### Stretch Goals  
- Compare characteristic-based models to factor models (e.g., Fama–French 5-factor or Q-factor model).
- Test whether prediction errors relate to known anomalies.
- Introduce **cross-sectional clustering** (e.g., industry groups or latent factor structures using PCA).
- Evaluate nonlinear interactions between characteristics using neural networks.
- Add risk adjustments or expected return decomposition (alpha vs factor exposure).