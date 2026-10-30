## **Reasons for selecting the models I did:**

The context of the project directly influenced model selection. A single “best” model does not exist for all targets; instead, different weather variables require different modeling assumptions.



#### Gradient Boosting (classification tasks)

Used for:

* Rain (binary classification)
* Snow (binary classification)
* High visibility (binary classification)

**Why Gradient Boosting was chosen**

Gradient Boosting classifiers were selected because weather events such as rain, snow, and low visibility are:

* Rare but impactful
* Driven by interacting variables (e.g., humidity × pressure × temperature)
* Highly non‑linear
* Poorly modeled by simple thresholds

**Gradient Boosting excels in this setting because it:**

* Incrementally corrects its own errors (boosting principle)
* Captures feature interactions automatically
* Handles imbalanced datasets better than most alternatives
* Is robust to outliers without needing explicit removal



Crucially, gradient boosting trains many shallow decision rules, which aligns well with meteorological logic



#### Temperature (Gradient Boosting Regressor)

**Temperature is influenced by:**

* Seasonality
* Time of day
* Atmospheric pressure
* Humidity interactions

These relationships are non‑linear, but relatively smooth.

**A Gradient Boosting Regressor was used because:**

* Linear models could not capture seasonal interactions adequately
* Tree ensembles model non‑linear trends without explicit polynomial terms
* The model remains stable across extreme winter and summer conditions



#### Random Forest models 

Used for:

* Wind speed regression
* Pressure regression



**Why Random Forest was chosen**

**Random Forest models were ultimately selected because they offer an excellent balance between expressiveness and stability for meteorological data:**



**Non‑linear modeling capability**

&#x09;Atmospheric variables interact in complex, non‑linear ways (e.g., pressure–humidity-temperature coupling). Random Forests capture these interactions naturally without requiring manual feature engineering.



**Robustness to outliers and extremes**

&#x09;Weather datasets legitimately contain extreme values (storms, sudden pressure drops, very high 	winds). Unlike linear models, Random Forests do not extrapolate aggressively and remain stable 	in these regimes.



**Low sensitivity to feature scaling and distributions**

&#x09;Given the mix of standardized numeric variables and one‑hot encoded categorical indicators, Random Forests operate reliably without fragile preprocessing pipelines.



**Strong and consistent empirical performance**

&#x09;During experimentation, Random Forest regressors consistently yielded lower MAE and more stable predictions than simpler models, particularly during volatile weather conditions.





## 

## **Alternative Models that were Considered** 

#### **Linear Regression / Logistic Regression (Rejected as final models)**

**Why they were considered:**

* Simple
* Interpretable
* Extremely lightweight
* Why they were not chosen:
* Strong assumptions of linearity
* Poor performance on interaction‑driven phenomena (e.g. precipitation)
* Inability to model threshold effects naturally



**While linear models were evaluated as baselines, they consistently underperformed for:**



* Rain prediction
* Snow prediction
* Visibility classification



They were therefore unsuitable as final models where accuracy under complex atmospheric conditions mattered.



#### **k‑Nearest Neighbors (Rejected)**

**Why it was rejected outright:**

* Extremely sensitive to outliers (common in weather)
* Performance degrades in high‑dimensional feature space
* Memory grows with dataset size
* Computationally expensive at inference time



Given the combination of scaled numeric data, many binary indicators, and rare events, k‑NN was fundamentally incompatible with the dataset structure.



#### **Support Vector Machines (Rejected)**

**Why it was considered:**

* Strong theoretical grounding
* Effective in high‑dimensional spaces



**Why it was rejected:**

* Difficult to tune for large datasets
* High inference cost
* No native probability outputs (problematic for weather risk estimation)
* Poor interpretability for stakeholders



In applied forecasting systems, ease of deployment and interpretability are as important as accuracy; SVMs performed well but failed these practical criteria.



#### **Neural Networks (Rejected)**

**Why they were considered:**

* Capable of modeling complex non‑linear relationships



**Why they were rejected:**

* Require significantly more data to generalize reliably
* Sensitive to feature scaling and hyperparameters
* Difficult to interpret
* Overkill for structured tabular meteorological data



In practice, tree‑based ensemble methods consistently outperform neural networks on tabular datasets like this one.



#### **ARIMA / pure time‑series models (Rejected)**

**Why they were considered:**

* Common in forecasting literature



**Why they were rejected:**

* Require explicit sequential modeling
* Not well‑suited to multi‑input causal features (humidity, pressure, weather state)
* Difficult to extend across multiple targets simultaneously



Because this system forecasts conditional on atmospheric state, not solely on historical values, classical time‑series models were not appropriate.



















