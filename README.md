# 🏦 Italian Financial Challenge - Student Repository

Welcome to the Italian Financial Challenge! This repository contains all the materials you need to complete your machine learning project.

## 📋 Quick Links

- **[Challenge Description](docs/challenge_description.md)** - READ THIS FIRST! Complete guide to all three challenges
- **[Data Dictionary](docs/data_dictionary.md)** - Explanation of all variables in the dataset
- **[Starter Template](notebooks/starter_template.ipynb)** - Jupyter notebook template to get you started

---

## 🎯 Your Task

Choose **ONE** of three challenges:

1. **Bankruptcy Prediction** (Medium) - Predict if a company will go bankrupt
2. **Financial Health Classification** (Medium-High) - Classify companies into health categories (A/B/C/D)
3. **Revenue Forecasting** (High) - Predict next year's revenue change

See [docs/challenge_description.md](docs/challenge_description.md) for full details.

---

## 🚀 Getting Started

### 1. Setup Your Environment

```bash
# Clone this repository (if you haven't already)
git clone <your-repo-url>
cd italian-financial-challenge

# Create a virtual environment
python3 -m venv venv

# Activate it
source venv/bin/activate  # On Linux/Mac
# OR
venv\Scripts\activate     # On Windows

# Install dependencies
pip install -r requirements.txt
```

### 2. Explore the Data

```bash
# Launch Jupyter Notebook
jupyter notebook

# Open notebooks/starter_template.ipynb
# OR create your own notebook
```

```python
# Quick data exploration
import pandas as pd

# Load the training data
train_df = pd.read_csv('data/processed/train_data.csv')

print(f"Shape: {train_df.shape}")
print(f"\nColumns: {train_df.columns.tolist()}")
print(f"\nFirst rows:")
train_df.head()
```

### 3. Read the Documentation

- **[docs/challenge_description.md](docs/challenge_description.md)** - Complete challenge guide with evaluation criteria
- **[docs/data_dictionary.md](docs/data_dictionary.md)** - Detailed explanation of all variables

### 4. Start Your Analysis

Use the provided template or create your own notebook. Make sure to cover:

1. **Exploratory Data Analysis**
2. **Data Preprocessing**
3. **Feature Engineering**
4. **Model Development**
5. **Evaluation**
6. **Interpretation & Business Insights**

---

## 📊 Available Data

### Training Data
- **File**: `data/processed/train_data.csv`
- **Observations**: 11,828 company-year records (2018-2021)
- **Use for**: Model development, cross-validation, feature engineering

### Test Data
- **File**: `data/processed/test_features.csv`
- **Observations**: 5,811 company-year records (2022-2023)
- **Use for**: Final predictions (targets will be used for evaluation)
- **Note**: Test targets are NOT provided to students

### Data Structure

```
Data/
├── processed/
│   ├── train_data.csv        # Training data WITH targets
│   └── test_features.csv     # Test data WITHOUT targets (for final predictions)
```

**Features** (25+ variables):
- Company info: sector, province, region, legal form, age
- Balance sheet: assets, equity, debt
- Income statement: revenue, costs, profit
- Financial ratios: ROE, ROI, leverage, liquidity ratios

**Targets** (choose based on your challenge):
- `bankruptcy_next_year` (0/1) - for Challenge 1
- `financial_health_class` (A/B/C/D) - for Challenge 2
- `revenue_change` (%) - for Challenge 3

See [docs/data_dictionary.md](docs/data_dictionary.md) for complete variable descriptions.

---

## 📝 Deliverables

### Required Submissions

1. **Jupyter Notebook** (.ipynb file)
   - Complete analysis from EDA to final model
   - Well-documented code with markdown explanations
   - Clear visualizations
   - Business insights and interpretation

2. **PDF Export** of your notebook
   - Ensure all cells have been executed
   - All outputs are visible

3. **Presentation Slides** (PDF or PPTX)
   - 10-15 minutes + Q&A
   - Focus on insights, not just technical details

### Evaluation Criteria (100 points)

| Category | Points | What to Focus On |
|----------|--------|------------------|
| **Technical Quality** | 40 | Proper methodology, validation, imbalance handling |
| **Creativity** | 20 | Feature engineering, innovative approaches |
| **Interpretability** | 20 | Feature importance, error analysis, business insights |
| **Communication** | 20 | Clear code, visualizations, presentation |

See [docs/challenge_description.md](docs/challenge_description.md) for detailed rubric.

---

## 💡 Tips for Success

### General Tips

1. **Start Early** - Data exploration takes time
2. **Read Everything** - Challenge description, data dictionary, evaluation criteria
3. **Document Your Thinking** - Explain WHY you made each decision
4. **Visualize Often** - Plots reveal insights that numbers hide
5. **Iterate** - Start simple (baseline), then improve

### Technical Tips

**Avoid Data Leakage:**
- ✅ Use temporal split (earlier years → later years)
- ✅ Fit scalers and imputers on train data only
- ✅ Use only past information to predict future
- ❌ Don't use random train/test split for time series (Challenge 3)
- ❌ Don't use target-derived features

**Handle Imbalance** (Challenges 1 & 2):
- Use appropriate metrics (F1-score, not accuracy)
- Try SMOTE, class weights, or threshold tuning
- Evaluate with stratified cross-validation

**Feature Engineering:**
- Financial domain knowledge (Altman Z-Score, ratios)
- Temporal features (year-over-year changes, trends)
- Interaction features (leverage × profitability)
- Sector benchmarking (company vs industry average)

**Model Interpretation:**
- Feature importance (built-in or SHAP)
- Error analysis (which cases are misclassified?)
- Business translation (explain in non-technical terms)

---

## 📚 Recommended Resources

### Financial Domain
- [Investopedia - Financial Ratios](https://www.investopedia.com/financial-ratios-4689817)
- [Altman Z-Score](https://www.investopedia.com/terms/a/altman.asp)
- Understanding bankruptcy indicators

### Machine Learning
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [Handling Imbalanced Data](https://imbalanced-learn.org/)
- [SHAP for Interpretation](https://shap.readthedocs.io/)
- Time series cross-validation

### Python Libraries
```python
# Data manipulation
import pandas as pd
import numpy as np

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Machine Learning
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.preprocessing import StandardScaler, RobustScaler
from sklearn.ensemble import RandomForestClassifier, RandomForestRegressor
from xgboost import XGBClassifier, XGBRegressor

# Imbalanced learning
from imblearn.over_sampling import SMOTE

# Metrics
from sklearn.metrics import (
    classification_report, confusion_matrix,
    f1_score, roc_auc_score,
    mean_squared_error, mean_absolute_error
)

# Interpretation
import shap
```

---

## 🆘 Common Issues

### "ModuleNotFoundError"
```bash
# Make sure virtual environment is activated
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Install missing package
pip install <package-name>
```

### "File not found"
```bash
# Check you're in the right directory
pwd  # Should show: .../italian-financial-challenge

# Check data files exist
ls data/processed/
# Should show: train_data.csv, test_features.csv
```

### "My model has very low performance"
- Check for data leakage (temporal split correct?)
- For imbalanced data: use F1-score, try SMOTE or class weights
- For regression: check for outliers, try robust methods
- Review feature engineering - domain knowledge is key!

### "My results are too good to be true"
- **Data leakage** is most likely - review your preprocessing!
- Check temporal split (no future data in training)
- Verify scaling is fit on train only, then transform test
- Check you're not using target-derived features

---

## ⚠️ Important Rules

### Academic Integrity

- This is an **INDIVIDUAL** project
- You may **discuss concepts** with peers
- You **MUST write your own code** and analysis
- **Cite all external resources** (code snippets, tutorials, etc.)
- Plagiarism will result in severe penalties

### Data Ethics

- This data is for **educational purposes only**
- Do not use for real financial decisions
- Company data is anonymized - respect privacy
- Always cite data sources in real-world projects

### Submission

- Ensure all code cells execute without errors
- Include both .ipynb and PDF versions
- Submit presentation slides
- Check that all visualizations are visible
- Verify you meet minimum performance targets

---

## 📅 Suggested Timeline

| Week | Milestone | Tasks |
|------|-----------|-------|
| 1 | Challenge Selection | Choose challenge, explore data |
| 2 | EDA Complete | Understand data, identify patterns |
| 3 | Baseline Model | Basic preprocessing, simple model |
| 4 | Feature Engineering | Create domain-informed features |
| 5 | Final Model | Tune hyperparameters, optimize |
| 6 | Interpretation | Feature importance, error analysis, insights |
| 7 | Submission | Final notebook, presentation prep |

---

## 🎯 Performance Targets

### Challenge 1: Bankruptcy Prediction
- **Minimum**: F1 > 0.45, AUC > 0.70
- **Good**: F1 = 0.55-0.65, AUC = 0.75-0.85
- **Excellent**: F1 > 0.65, AUC > 0.85

### Challenge 2: Financial Health Classification
- **Minimum**: Weighted F1 > 0.60
- **Good**: Weighted F1 = 0.65-0.75
- **Excellent**: Weighted F1 > 0.75

### Challenge 3: Revenue Forecasting
- **Minimum**: MAPE < 20%, Directional Accuracy > 65%
- **Good**: MAPE = 12-18%, Directional Accuracy = 70-78%
- **Excellent**: MAPE < 12%, Directional Accuracy > 78%

**Note**: Focus on methodology and interpretation, not just achieving high scores!

---

## 📁 Repository Structure

```
italian-financial-challenge/
├── README.md (this file)
├── requirements.txt          # Python dependencies
│
├── docs/
│   ├── challenge_description.md   # Complete challenge guide
│   └── data_dictionary.md         # Variable descriptions
│
├── data/
│   └── processed/
│       ├── train_data.csv         # Training data with targets
│       └── test_features.csv      # Test features (no targets)
│
├── notebooks/
│   └── starter_template.ipynb     # Starter template (optional)
│
├── src/                      # Your Python modules (optional)
│   ├── data/                 # Data processing scripts
│   ├── models/               # Model definitions
│   └── utils/                # Utility functions
│
└── configs/                  # Configuration files (optional)
```

**Recommended workflow:**
- Do your analysis in `notebooks/`
- Put reusable code in `src/`
- Keep it simple - notebooks are fine for the whole project!

---

## 📧 Getting Help

1. **Read the documentation** - Most questions are answered there
2. **Attend office hours** - Ask specific questions
3. **Check the FAQ** in the challenge description
4. **Discussion forum** - Help each other (concepts only, not solutions!)

**Good question:** "How should I handle the class imbalance in bankruptcy prediction?"
**Bad question:** "Can you tell me what features to engineer?"

---

## 🎓 Learning Objectives

By completing this challenge, you will:

✓ Work with realistic financial data
✓ Handle class imbalance in classification
✓ Perform time series aware validation
✓ Engineer domain-informed features
✓ Interpret machine learning models
✓ Communicate technical findings to business audiences
✓ Write clean, reproducible code

---

## 📄 License

- **Code**: Your code is your own
- **Data**: CC-BY 4.0 (cite the source)
- **Project**: For educational use only

---

**Good luck with your challenge!**

Remember: The goal is to **learn** and develop your skills. Focus on understanding the problem, trying different approaches, and interpreting your results. Don't just chase high scores!

If you have questions, read the documentation first, then ask for help. 🚀

---

**Academic Year**: 2024/2025
**Institution**: LUISS University
