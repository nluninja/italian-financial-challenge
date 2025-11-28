# 🏦 Italian Financial Data Challenge - Student Guide

## 📋 Overview

Welcome to the Italian Financial Data Challenge! In this project, you will work with real-world financial data from Italian companies to build machine learning models that solve critical business problems.

You will choose **ONE** of the three challenges below and develop a complete solution including data exploration, feature engineering, model development, and results analysis.

## 🎯 Available Challenges

### Challenge 1: Bankruptcy Prediction 🎯
**Difficulty**: Medium
**Type**: Binary Classification
**Business Context**: Predict whether a company will go bankrupt within the next 12 months based on its financial statements and business characteristics.

**Objective**: Build a model to predict `bankruptcy_next_year` (0 = healthy, 1 = bankruptcy)

**Key Challenges**:
- Severe class imbalance (bankruptcies are rare events, ~2-5% of cases)
- Temporal data leakage must be avoided
- Model interpretability is crucial (financial institutions need explainable decisions)
- Feature engineering from raw financial statements

**Evaluation Metrics**:
- **Primary**: F1-Score (balance between precision and recall)
- **Secondary**: AUC-ROC, Precision, Recall
- **Business Metric**: Cost-sensitive evaluation (false negatives are more expensive than false positives)

**Success Criteria**:
- F1-Score > 0.60 on test set
- AUC-ROC > 0.75
- Clear interpretation of top risk factors

---

### Challenge 2: Financial Health Classification 📊
**Difficulty**: Medium-High
**Type**: Multi-class Classification
**Business Context**: Classify companies into financial health categories (similar to credit ratings) to help investors and lenders assess risk levels.

**Objective**: Predict `financial_health_class` with 4 categories:
- **A**: Excellent financial health
- **B**: Good financial health
- **C**: Moderate risk
- **D**: High risk / distressed

**Key Challenges**:
- Multi-class imbalanced classification
- Ordinal relationship between classes (A > B > C > D)
- Feature engineering to capture financial stability
- Interpretability for different stakeholder groups

**Evaluation Metrics**:
- **Primary**: Weighted F1-Score
- **Secondary**: Confusion Matrix analysis, Per-class Precision/Recall
- **Business Metric**: Ordinal classification metrics (penalize A→D errors more than A→B)

**Success Criteria**:
- Weighted F1-Score > 0.65
- No severe misclassifications (A classified as D or vice versa)
- Clear feature importance for each class

---

### Challenge 3: Revenue Forecasting 📈
**Difficulty**: High
**Type**: Regression / Time Series
**Business Context**: Forecast the percentage change in revenue for the next fiscal year to help companies with budget planning and investors with valuation.

**Objective**: Predict `revenue_change` (percentage change in production value)

**Key Challenges**:
- Time series aware validation (no future information leakage)
- Incorporate sectoral trends and macroeconomic factors
- Handle outliers (mergers, acquisitions, extraordinary events)
- Feature engineering from historical financial data
- Consider seasonality and business cycles

**Evaluation Metrics**:
- **Primary**: RMSE (Root Mean Squared Error)
- **Secondary**: MAPE (Mean Absolute Percentage Error), MAE
- **Business Metric**: Directional accuracy (correctly predict growth vs. decline)

**Success Criteria**:
- MAPE < 15%
- Directional accuracy > 70%
- Robust to outliers

---

## 📊 Dataset Description

You will work with a dataset containing financial and operational data from Italian companies spanning multiple years.

### Available Features

**Company Information**:
- `company_id`: Anonymized company identifier
- `fiscal_year`: Year of financial statement (2018-2023)
- `ateco_sector`: Economic sector code (2-digit ATECO classification)
- `province`, `region`: Geographic location
- `legal_form`: Legal structure (SRL, SPA, etc.)
- `years_in_business`: Company age

**Balance Sheet Items**:
- `total_fixed_assets`: Property, equipment, intangible assets
- `current_assets`: Cash, inventory, receivables
- `shareholders_equity`: Net worth
- `total_debt`: All liabilities
- `short_term_debt`: Due within 1 year
- `long_term_debt`: Due after 1 year

**Income Statement Items**:
- `production_value`: Total revenue
- `production_costs`: Operating costs
- `operating_income`: EBIT (Earnings Before Interest and Taxes)
- `net_profit_loss`: Bottom line profit/loss

**Pre-calculated Financial Ratios**:
- `roe`: Return on Equity (net_profit / equity)
- `roi`: Return on Investment (operating_income / total_assets)
- `leverage`: Debt to Equity ratio
- `current_ratio`: Current assets / current liabilities
- `quick_ratio`: (Current assets - inventory) / current liabilities
- `debt_to_assets`: Total debt / total assets

**Target Variables** (choose based on your challenge):
- `bankruptcy_next_year`: Binary (0/1) - for Challenge 1
- `financial_health_class`: Categorical (A/B/C/D) - for Challenge 2
- `revenue_change`: Continuous (%) - for Challenge 3

### Dataset Size
- **Training set**: ~15,000 companies × 5 years = ~75,000 observations
- **Test set**: ~5,000 companies × 2 years = ~10,000 observations
- **Features**: 25+ raw features + unlimited engineered features

---

## 🛠️ Required Deliverables

### 1. Jupyter Notebook (60% of grade)
A complete, well-documented notebook containing:

**A. Exploratory Data Analysis (15%)**
- Dataset overview and statistics
- Missing values analysis
- Distribution analysis of key variables
- Correlation analysis
- Target variable analysis (class distribution, trends)
- Visualizations with clear insights

**B. Data Preprocessing (15%)**
- Missing value handling with justification
- Outlier detection and treatment
- Feature scaling/normalization strategy
- Encoding categorical variables
- Temporal train/test split (no data leakage!)

**C. Feature Engineering (20%)**
- Creation of new financial indicators
- Temporal features (trends, year-over-year changes)
- Interaction features
- Domain knowledge application
- Feature selection methodology

**D. Model Development (30%)**
- Baseline model(s)
- At least 3 different model types (e.g., Logistic Regression, Random Forest, XGBoost, Neural Networks)
- Hyperparameter tuning strategy
- Cross-validation approach (time-aware if applicable)
- Imbalance handling techniques (for classification challenges)
- Final model selection with justification

**E. Results Analysis (20%)**
- Performance metrics on test set
- Feature importance analysis
- Error analysis (what types of cases does the model misclassify?)
- Model interpretation (SHAP values, partial dependence plots, etc.)
- Business insights and recommendations

### 2. Presentation (40% of grade)
**Duration**: 10-15 minutes + 5 minutes Q&A

**Structure**:
1. Problem definition and business impact (2 min)
2. Data exploration key findings (3 min)
3. Modeling approach and innovations (5 min)
4. Results and interpretation (3 min)
5. Limitations and future work (2 min)

**Requirements**:
- Clear, professional slides
- Focus on insights, not just technical details
- Business-oriented language (imagine presenting to executives)
- Demonstration of critical thinking

---

## 📝 Evaluation Criteria

| Criterion | Weight | Description |
|-----------|--------|-------------|
| **Technical Quality** | 40% | Sound methodology, proper validation, appropriate techniques for imbalance/temporal issues |
| **Creativity** | 20% | Original feature engineering, innovative approaches, going beyond baseline |
| **Interpretability** | 20% | Feature importance, error analysis, business insights, model explanation |
| **Communication** | 20% | Code clarity, documentation, presentation quality, storytelling |

### Specific Grading Elements

**Technical Quality** includes:
- Correct train/test split (temporal awareness)
- Appropriate handling of class imbalance (if applicable)
- Proper cross-validation strategy
- Sound hyperparameter tuning
- No data leakage
- Correct metric calculation

**Creativity** includes:
- Novel feature engineering
- Domain knowledge application
- Ensemble methods or hybrid approaches
- Advanced techniques (SHAP, calibration, stacking, etc.)

**Interpretability** includes:
- Feature importance analysis
- Error analysis and insights
- Model explanation techniques
- Business recommendations
- Understanding of model limitations

**Communication** includes:
- Clean, well-commented code
- Clear markdown explanations
- Professional visualizations
- Logical flow in notebook
- Effective presentation

---

## 🚀 Getting Started

### 1. Setup Environment

```bash
# Clone repository
cd italian-financial-challenge

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

### 2. Load the Data

```python
import pandas as pd

# Load training data
train_df = pd.read_csv('data/processed/train_data.csv')

# Load test data (no target leakage)
test_df = pd.read_csv('data/processed/test_data.csv')

# Load data dictionary
data_dict = pd.read_csv('data/processed/data_dictionary.csv')
```

### 3. Choose Your Challenge

Open the starter notebook template:
- `notebooks/challenge1_bankruptcy_starter.ipynb` (Challenge 1)
- `notebooks/challenge2_health_class_starter.ipynb` (Challenge 2)
- `notebooks/challenge3_revenue_forecast_starter.ipynb` (Challenge 3)

### 4. Work Through the Sections

Follow the structure in the starter notebook, completing each section:
1. Data Loading and Exploration
2. Preprocessing
3. Feature Engineering
4. Model Development
5. Evaluation
6. Interpretation

---

## 💡 Tips for Success

### General Tips
1. **Start early**: Data exploration takes time
2. **Focus on one challenge**: Don't try to solve all three
3. **Read the data carefully**: Understand what each feature represents
4. **Document your thought process**: Explain your decisions in markdown cells
5. **Iterate**: First build a simple baseline, then improve incrementally

### Technical Tips
1. **Avoid data leakage**:
   - Use only past data to predict future (temporal split)
   - Don't use target-derived features
   - Be careful with imputation and scaling (fit on train, transform on test)

2. **Handle imbalance properly**:
   - Use stratified sampling
   - Try SMOTE, class weights, or threshold tuning
   - Evaluate with appropriate metrics (F1, AUC, not just accuracy)

3. **Feature engineering is key**:
   - Financial ratios and trends
   - Year-over-year changes
   - Industry benchmarks
   - Temporal aggregations

4. **Validate properly**:
   - Use time-aware cross-validation
   - Reserve a true holdout test set
   - Check for overfitting

### Interpretability Tips
1. Use feature importance (built-in or SHAP)
2. Analyze misclassified examples
3. Create partial dependence plots
4. Explain in business terms (not just "accuracy is 0.85")

---

## 📚 Recommended Resources

### Financial Domain Knowledge
- [Investopedia - Financial Ratios](https://www.investopedia.com/financial-ratios-4689817)
- Understanding bankruptcy indicators (Altman Z-Score)
- Italian economic sectors (ATECO codes)

### Machine Learning
- Scikit-learn documentation
- Imbalanced-learn for handling class imbalance
- SHAP for model interpretation
- Time series cross-validation

### Python Libraries
- `pandas`, `numpy` for data manipulation
- `scikit-learn` for ML models
- `xgboost`, `lightgbm` for gradient boosting
- `imbalanced-learn` for SMOTE and other techniques
- `shap` for model interpretation
- `matplotlib`, `seaborn`, `plotly` for visualization

---

## ⚠️ Important Notes

### Academic Integrity
- This is an **individual project**
- You may discuss concepts with peers, but code and analysis must be your own
- Cite any external code or resources you use
- Plagiarism will result in severe penalties

### Data Ethics
- This data is for **educational purposes only**
- Do not use for real financial decisions
- Respect company privacy (data is anonymized)
- Always cite data sources

### Submission
- Submit your complete notebook (.ipynb file)
- Include a PDF export of your notebook
- Ensure all cells execute without errors
- Include your presentation slides (PDF or PPTX)

---

## 🆘 Getting Help

1. **Office Hours**: Check the course calendar
2. **Discussion Forum**: Post questions (no code solutions)
3. **Documentation**: Read the data dictionary and modeling guidelines
4. **Debugging**: Start with a small subset of data first

---

## 📅 Timeline

| Milestone | Deadline |
|-----------|----------|
| Challenge selection | Week 1 |
| EDA completion | Week 2 |
| Baseline model | Week 3 |
| Feature engineering | Week 4 |
| Final model | Week 5 |
| Notebook submission | Week 6 |
| Presentations | Week 7 |

---

**Good luck with your challenge! Remember: the goal is to learn, experiment, and develop your skills in applied machine learning. Focus on understanding over performance, and interpretation over complexity.**
