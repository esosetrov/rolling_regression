# rolling-regression
This project implements rolling regression analysis using the Fama-French Three-Factor Model and industry portfolio returns to analyze time-varying relationships in financial data. The analysis is performed using Python, leveraging libraries such as pandas, statsmodels, matplotlib, and seaborn.

# Rolling Regression Analysis with Fama-French Factors
A comprehensive implementation of rolling regression analysis using the Fama-French three-factor model and industry portfolio returns. This project demonstrates how to model time-varying relationships in financial data, analyze risk factor exposures, and apply rolling regression techniques for dynamic portfolio management.

## Project Overview

This repository contains a complete analysis pipeline for:
- **Rolling CAPM** - Dynamic estimation of market betas
- **Fama-French Three-Factor Model** - Time-varying exposure to market, size, and value factors
- **Industry Portfolio Analysis** - Comparative risk analysis across 10 industry sectors
- **Structural Break Detection** - Identifying significant changes in market relationships
- **Dynamic Hedging Strategies** - Implementing rolling beta-based portfolio hedging

## Features

- **Data Acquisition**: Automated download of Fama-French factors and industry portfolios
- **Rolling Regression**: Implementation using `statsmodels.RollingOLS`
- **Visualization**: Comprehensive plots for parameter trajectories, confidence intervals, and distributions
- **Multi-Factor Analysis**: Extending beyond CAPM to include size and value factors
- **Comparative Analysis**: Cross-industry beta comparison and correlation analysis
- **Sensitivity Analysis**: Window size impact on parameter estimates
- **Practical Applications**: Dynamic hedging strategy implementation

## Repository Structure

rolling_regression/
├── rolling_regression.ipynb                                  # Main analysis notebook
├── requirements.txt                                          # Python dependencies
├── README.md                                                 # Project documentation
├── LICENSE                                                   # MIT License
└── .gitignore                                                # Version control settings


## Installation & Setup

### Prerequisites
- Python 3.8+
- pip package manager

### Installation
1. Clone the repository:
```bash
git clone https://github.com/yourusername/rolling-regression-analysis.git
cd rolling-regression-analysis
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

# Install dependencies
```bash
pip install matplotlib numpy pandas pandas_datareader seaborn statsmodels
```

### Dependencies
Key packages include:
- `pandas` & `numpy` - Data manipulation
- `statsmodels` - Rolling regression implementation
- `matplotlib` & `seaborn` - Visualization
- `pandas-datareader` - Financial data acquisition
- `scipy` - Statistical functions

## Data Sources

The analysis uses publicly available data from **Kenneth French's Data Library**:
- **Fama-French Three Factors**: Market excess return (Mkt-RF), Size factor (SMB), Value factor (HML)
- **10 Industry Portfolios**: Monthly returns for 10 industry sectors (1926-2025)
- **Frequency**: Monthly data
- **Time Period**: July 1926 - October 2025

## Key Analyses

### 1. Rolling CAPM Analysis
- Dynamic beta estimation for technology sector
- Confidence interval analysis
- Parameter stability assessment

### 2. Fama-French Three-Factor Model
- Time-varying exposure to market, size, and value factors
- Factor significance analysis
- Model explanatory power (R-squared)

### 3. Industry Comparison
- Cross-sectional beta analysis across 10 industries
- Risk ranking and classification
- Diversification potential assessment

### 4. Structural Break Detection
- Z-score based breakpoint identification
- Analysis of changing market regimes

### 5. Dynamic Hedging Strategy
- Rolling beta-based hedge ratio calculation
- Performance comparison: hedged vs. unhedged portfolios
- Trading signal generation

## Key Findings

### Technology Sector Insights:
- **Average Beta**: 1.21 (consistently above market)
- **Beta Volatility**: 0.21 (significant time variation)
- **Factor Exposures**: 
  - Market: 1.14 (significant positive)
  - Size: 0.10 (moderate positive)
  - Value: -0.47 (significant negative - growth characteristics)

### Model Performance:
- **CAPM R²**: 50.1% - 96.6%
- **3-Factor R²**: 61.8% - 97.0%
- **Improvement**: +5.6% average explanatory power

### Industry Risk Rankings:
1. **Highest Beta**: HiTec (1.21), Durbl (1.20), Other (1.11)
2. **Lowest Beta**: Utils (0.64), Telcm (0.69), NoDur (0.78)

## Practical Applications

1. **Dynamic Risk Management**: Time-varying beta estimation for portfolio hedging
2. **Factor Timing**: Identifying periods of factor significance
3. **Portfolio Construction**: Industry selection based on rolling risk characteristics
4. **Market Regime Detection**: Structural break identification for strategy adjustment

## Usage Examples

### Basic Rolling Regression
```python
from src.rolling_regression import perform_rolling_regression

# Load data
factors, industries = load_famafrench_data()

# Perform rolling CAPM for technology sector
results = perform_rolling_regression(
    returns=industries['HiTec'],
    factors=factors[['Mkt-RF']],
    window=60
)
```

### Industry Comparison
```python
from src.analysis import compare_industry_betas

# Compare beta distributions across industries
beta_comparison = compare_industry_betas(
    industries=industries,
    factors=factors,
    window=60
)
```

## Configuration

Key parameters can be adjusted in the configuration:
- `window_size`: Rolling window length (default: 60 months)
- `confidence_level`: For parameter intervals (default: 95%)
- `selected_industries`: Subset for analysis (default: ['HiTec', 'Hlth', 'Utils', 'NoDur'])

## Future Extensions

Potential enhancements include:
1. **Additional Factors**: Momentum, quality, low volatility factors
2. **Non-linear Models**: Quantile regression for tail risk
3. **Machine Learning**: Advanced regime detection algorithms
4. **International Data**: Cross-market comparison
5. **High-Frequency Analysis**: Daily or weekly rolling regressions

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## References
1. Fama, E. F., & French, K. R. (1993). Common risk factors in the returns on stocks and bonds.
2. French, K. R. Data Library. https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html
3. Statsmodels Documentation: RollingOLS

## Acknowledgments

- Kenneth French for maintaining the Fama-French data library
- The statsmodels development team for the RollingOLS implementation
- All contributors to the open-source data science ecosystem

**Note**: This is an educational/research tool. Not financial advice. Always conduct your own due diligence before making investment decisions.