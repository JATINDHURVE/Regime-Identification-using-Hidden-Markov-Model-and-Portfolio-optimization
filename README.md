# 📈 Regime-Based Portfolio Optimization Project

A comprehensive implementation of Hidden Markov Model (HMM) regime identification and regime-aware portfolio optimization strategies for enhanced risk-adjusted returns.

## 🎯 Project Overview

This project implements a sophisticated approach to portfolio management by:
1. **Identifying economic regimes** using Hidden Markov Models with leading economic indicators
2. **Optimizing portfolio allocations** dynamically based on the current economic regime
3. **Comparing performance** against traditional static portfolio optimization approaches

## 📊 Key Features

- **HMM Regime Identification**: 4-state economic regime classification (Expansion, Recovery, Downturn, Slowdown)
- **Dynamic Portfolio Optimization**: Regime-specific Mean Variance Optimization (MVO)
- **Comprehensive Validation**: Statistical and economic validation of regime models
- **Performance Analysis**: Detailed comparison of regime-based vs. traditional approaches
- **Real Economic Events**: Validation against known recession periods (1990s, Dot-com, Great Recession, COVID-19)

## 🏗️ Project Structure

```
Regime_Portfolio_project/
├── Data/
│   ├── leading_indicators.xlsx      # VIX, PMI, Yield Curve data (1990-2025)
│   ├── portfolio_data.xlsx          # Asset returns (Equities, Bonds, Commodities, REITs)
├── Regime_identification/
│   ├── hmm_regime_identification.ipynb    # Core HMM implementation
│   ├── hmm_validation.ipynb              # Model validation & testing
│   ├── hmm_model_validation_positive_only.py  # Validation script
│   └── hmm_regime_identification.xlsx    # Generated regime classifications
├── full_period_mvo/
│   ├── mvo_normal.ipynb             # Traditional static MVO baseline
│   ├── hmm_regime_mvo.ipynb         # Regime-based dynamic MVO
├── Traditional_mvo_train_test/
│   ├── mvo_static.ipynb             # Static optimization with train/test split
│   ├── hmm_regime_mvo.ipynb         # Regime-based with train/test split
│   └── probabilities_regime.ipynb   # Regime probability analysis
├── HMM_Regime_Report_Comprehensive.ipynb  # Complete analysis report
└── HMM_Validation_Report_Comprehensive.ipynb  # Validation summary
```

## 🔬 Methodology

### 1. Economic Regime Identification

**Input Features:**
- **VIX**: Market volatility index (fear gauge)
- **PMI**: Purchasing Managers' Index (economic activity)
- **Yield Curve**: 10Y-2Y Treasury spread (economic outlook)

**HMM Configuration:**
- 4 hidden states (optimal by BIC criteria)
- Gaussian emissions with full covariance
- Standardized features for numerical stability

**Regime Classification Logic:**
- **Expansion**: Highest PMI, lowest VIX (strong growth, low volatility)
- **Recovery**: High yield curve, moderate VIX (economic recovery phase)
- **Downturn**: Lowest PMI, highest VIX (recession/crisis periods)
- **Slowdown**: Moderate indicators (economic deceleration)

### 2. Portfolio Assets

**Asset Classes:**
- **EQU**: S&P 500 (Equities)
- **GOVT**: Treasury Bonds (Government bonds)
- **CORP**: Corporate Bonds
- **COMM**: Commodity Index
- **REITs**: Real Estate Investment Trusts

### 3. Optimization Framework

**Mean Variance Optimization (MVO):**
- Utility function: `U = μ'w - (λ/2)w'Σw`
- Risk aversion parameter: λ ∈ [1, 10]
- Dynamic bounds based on inverse volatility
- Regime-specific expected returns and covariance matrices

## 📈 Key Results

### Model Validation
- ✅ **Optimal Model Selection**: 4-state model chosen by BIC criteria
- ✅ **High Regime Persistence**: 93.5% average persistence rate
- ✅ **Economic Validity**: 100% recession detection success rate
- ✅ **Realistic Duration**: Average regime length of 19.4 months

### Economic Event Validation
| Event | Period | Detected Regime | Accuracy |
|-------|--------|-----------------|----------|
| Early 1990s Recession | 1990-1991 | Downturn (87.5%) | ✅ |
| Dot-com Recession | 2001 | Downturn (100%) | ✅ |
| Great Recession | 2007-2009 | Downturn (100%) | ✅ |
| COVID Recession | 2020 | Slowdown (100%) | ✅ |

### Regime Distribution (1990-2025)
- **Recovery**: 34.3% (12.1 years)
- **Expansion**: 31.9% (11.3 years)
- **Downturn**: 22.9% (8.1 years)
- **Slowdown**: 10.9% (3.8 years)

## 🚀 Getting Started

### Prerequisites
```python
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=1.0.0
hmmlearn>=0.2.7
scipy>=1.7.0
matplotlib>=3.4.0
seaborn>=0.11.0
```

### Installation
```bash
git clone https://github.com/yourusername/regime-portfolio-optimization.git
cd regime-portfolio-optimization
pip install -r requirements.txt
```

### Usage

1. **Run Regime Identification:**
```python
# Execute the HMM regime identification
jupyter notebook Regime_identification/hmm_regime_identification.ipynb
```

2. **Validate Model:**
```python
# Run comprehensive validation
jupyter notebook Regime_identification/hmm_validation.ipynb
```

3. **Portfolio Optimization:**
```python
# Compare regime-based vs traditional approaches
jupyter notebook full_period_mvo/hmm_regime_mvo.ipynb
jupyter notebook full_period_mvo/mvo_normal.ipynb
```

## 📋 Notebooks Description

### Core Analysis
- **`hmm_regime_identification.ipynb`**: Main HMM implementation with regime classification
- **`hmm_validation.ipynb`**: Comprehensive model validation and statistical tests
- **`mvo_normal.ipynb`**: Baseline traditional portfolio optimization
- **`hmm_regime_mvo.ipynb`**: Dynamic regime-based portfolio optimization

### Validation & Testing
- **`mvo_static.ipynb`**: Static optimization with train/test methodology
- **`probabilities_regime.ipynb`**: Regime probability analysis and transitions

### Reports
- **`HMM_Regime_Report_Comprehensive.ipynb`**: Complete project analysis
- **`HMM_Validation_Report_Comprehensive.ipynb`**: Detailed validation results

## 🔍 Key Findings

### Regime Characteristics
1. **Expansion Regime**: Low volatility (VIX), high economic activity (PMI)
2. **Recovery Regime**: Steep yield curve, moderate volatility
3. **Downturn Regime**: High volatility, low economic activity
4. **Slowdown Regime**: Moderate indicators, economic uncertainty

### Portfolio Implications
- **Dynamic allocation** based on economic conditions
- **Risk management** through regime-aware positioning
- **Enhanced returns** via tactical asset allocation
- **Reduced drawdowns** during crisis periods

## 📊 Performance Metrics

The regime-based approach demonstrates:
- Improved risk-adjusted returns
- Better downside protection during recessions
- More responsive allocation to economic conditions
- Enhanced portfolio diversification benefits

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📚 References

- Hamilton, J.D. (1989). "A New Approach to the Economic Analysis of Nonstationary Time Series and the Business Cycle"
- Markowitz, H. (1952). "Portfolio Selection"
- Ang, A. & Bekaert, G. (2002). "Regime Switches in Interest Rates"

## 📧 Contact

For questions or collaboration opportunities, please reach out via [GitHub Issues](https://github.com/yourusername/regime-portfolio-optimization/issues).

---

**Note**: This project is for educational and research purposes. Past performance does not guarantee future results. Always consult with financial professionals before making investment decisions.
