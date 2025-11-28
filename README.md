# 🏦 Italian Financial Data Challenge

Italian corporate financial statements dataset for Machine Learning and Data Mining projects.

## 📋 Project Description

This repository contains an economic-financial dataset of Italian companies built entirely from public open data sources. It is designed for university ML/DL projects focusing on:

- **Corporate bankruptcy prediction** (binary classification)
- **Credit scoring** and reliability assessment
- **Clustering** of financial profiles
- **Anomaly detection** on financial indicators
- **Time series forecasting** of performance

## 🎯 Learning Objectives

Students will learn to:
1. Work with real financial data (not toy datasets)
2. Handle imbalanced data (bankruptcies are rare)
3. Feature engineering from financial statements
4. Model interpretability in a regulated context
5. Temporal validation (no data leakage)

## 📊 Dataset Structure

### Data Sources
- **MovImprese** (InfoCamere): company demographics, bankruptcies
- **ISTAT**: aggregated sectoral data
- **Business Registry** (sample): public financial statements in XBRL format

### Available Features
```
- company_id (anonymized)
- fiscal_year
- ateco_sector (2-digit)
- province, region
- legal_form
- years_in_business

# Balance Sheet
- total_fixed_assets
- current_assets
- shareholders_equity
- total_debt
- short_term_debt
- long_term_debt

# Income Statement
- production_value
- production_costs
- operating_income (EBIT)
- net_profit_loss

# Calculated Indicators
- roe (Return on Equity)
- roi (Return on Investment)
- leverage (Debt/Equity)
- current_ratio (liquidity)
- quick_ratio
- debt_to_assets

# Target Variables
- bankruptcy_next_year (0/1)
- revenue_change (%)
- financial_health_class (A/B/C/D)
```

## 🗂️ Repository Structure

```
italian-financial-challenge/
├── README.md
├── requirements.txt
├── environment.yml
│
├── data/
│   ├── raw/                    # Original data (don't commit if large)
│   ├── interim/                # Data being processed
│   ├── processed/              # Final datasets ready for ML
│   └── external/               # External data (ISTAT, ATECO codes)
│
├── notebooks/
│   ├── 01_data_collection.ipynb       # Web scraping and data collection
│   ├── 02_data_exploration.ipynb      # Complete EDA
│   ├── 03_feature_engineering.ipynb   # Feature creation
│   ├── 04_baseline_models.ipynb       # Baseline models
│   ├── 05_deep_learning.ipynb         # Neural networks
│   └── 06_results_analysis.ipynb      # Results analysis
│
├── src/
│   ├── __init__.py
│   ├── data/
│   │   ├── scraper.py          # Ethical web scraping
│   │   ├── preprocessor.py     # Data cleaning
│   │   └── feature_builder.py  # Feature engineering
│   ├── models/
│   │   ├── baseline.py         # Logistic, RF, XGBoost
│   │   ├── neural_nets.py      # MLP, embeddings
│   │   └── evaluation.py       # Metrics, validation
│   └── utils/
│       ├── financial_ratios.py # Financial indicators calculation
│       └── visualization.py    # Plot utilities
│
├── configs/
│   ├── scraping_config.yaml
│   └── model_config.yaml
│
├── tests/
│   ├── test_data_quality.py
│   └── test_feature_engineering.py
│
└── docs/
    ├── challenge_description.md    # Challenge description for students
    ├── data_dictionary.md          # Complete data dictionary
    ├── legal_considerations.md     # Legal notes on scraping
    └── modeling_guidelines.md      # Modeling guidelines
```

## 🚀 Quick Start

### Installation

```bash
# Clone repository
git clone https://github.com/your-username/italian-financial-challenge.git
cd italian-financial-challenge

# Setup environment (option 1: venv)
python -m venv venv
source venv/bin/activate  # on Windows: venv\Scripts\activate
pip install -r requirements.txt

# Setup environment (option 2: conda)
conda env create -f environment.yml
conda activate financial-challenge
```

### Data Download

```bash
# Option A: Download pre-processed dataset (recommended for students)
python src/data/download_dataset.py

# Option B: Regenerate dataset from public sources (time-consuming)
python src/data/scraper.py --config configs/scraping_config.yaml
python src/data/preprocessor.py
```

### Data Exploration

```bash
jupyter notebook notebooks/02_data_exploration.ipynb
```

## 📖 Proposed Challenges

### Challenge 1: Bankruptcy Prediction 🎯
**Difficulty**: Medium
**Objective**: Predict if a company will go bankrupt within 12 months
**Metric**: F1-Score, AUC-ROC
**Constraints**:
- Handle class imbalance
- No data leakage (temporal validation)
- Interpretability required

### Challenge 2: Financial Health Classification 📊
**Difficulty**: Medium-High
**Objective**: Classify companies into 4 financial health classes
**Metric**: Weighted F1-Score
**Constraints**:
- Multi-class imbalanced
- Feature engineering required

### Challenge 3: Revenue Forecasting 📈
**Difficulty**: High
**Objective**: Predict next year's revenue change
**Metric**: RMSE, MAPE
**Constraints**:
- Time series aware validation
- Consider sectoral trends

## 🛠️ Technologies

- **Data Processing**: pandas, numpy, scipy
- **ML Models**: scikit-learn, xgboost, lightgbm
- **Deep Learning**: tensorflow/keras, pytorch
- **Feature Engineering**: feature-engine, category_encoders
- **Visualization**: matplotlib, seaborn, plotly
- **Web Scraping**: requests, beautifulsoup4, selenium (if needed)
- **Imbalanced Learning**: imbalanced-learn

## 📚 Useful Resources

### Public Datasets
- [MovImprese](https://www.unioncamere.gov.it/download/9154.html) - Company demographics
- [ISTAT - Companies](http://dati.istat.it/) - Sectoral statistics
- [Business Registry](https://www.registroimprese.it/) - Public financial statements

### Reference Papers
- Altman, E. (1968). "Financial Ratios, Discriminant Analysis and the Prediction of Corporate Bankruptcy"
- Ohlson, J. (1980). "Financial Ratios and the Probabilistic Prediction of Bankruptcy"
- Recent deep learning approaches for credit scoring

### Tutorials
- Imbalanced classification techniques
- Time series cross-validation
- Financial feature engineering

## ⚖️ Legal Considerations

Business Registry data is **public** and accessible to all citizens. Scraping must be:
- **Respectful**: rate limiting, identifying user-agent
- **Proportionate**: only data necessary for research/education
- **Cited**: always indicate the source

See `docs/legal_considerations.md` for details.

## 🎓 For Students

### Required Deliverables
1. **Complete notebook** with EDA, feature engineering, modeling
2. ** Live Presentation** 

### Evaluation Criteria
- **Technical quality** (40%): approach soundness, imbalance handling, validation
- **Creativity** (20%): original feature engineering, innovative approaches
- **Interpretability** (20%): feature importance analysis, error analysis
- **Communication** (20%): clarity of report and code

## 🤝 Contributions

This is an educational project. For suggestions or bugs:
1. Open an Issue
2. Submit a Pull Request with improvements

## 📄 License

- **Code**: MIT License
- **Data**: CC-BY 4.0 (cite source: Chamber of Commerce / ISTAT)

## 👥 Authors

Project created for the LUISS
Academic Year 2024/2025

## 🙏 Acknowledgments

- InfoCamere for the public Business Registry data
- ISTAT for economic statistics
- Unioncamere for MovImprese data

---

**Note**: This dataset is for **educational and research purposes only**. Do not use for real financial decisions.
# italian-financial-challenge
