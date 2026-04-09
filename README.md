# IPL 2022 Match Winner Predictor

A beginner-friendly Machine Learning project that predicts the winner of an IPL match based on pre-match conditions such as teams, venue, toss result, and tournament stage.

> Built during the **live IPL 2025 season** as my first ML project.

---

## Project Overview

Can we predict who wins an IPL match before it starts? This project attempts to answer that question using historical IPL 2022 match data and two classification algorithms — Random Forest and K-Nearest Neighbors (KNN).

The model only uses **pre-match information** (information available before the match starts) to make predictions — ensuring there is no data leakage.

---

## Dataset

- **File:** `Book_ipl22_ver_33.csv`
- **Season:** IPL 2022
- **Total Matches:** 74
- **Features Used:**

| Feature | Description |
|---------|-------------|
| team1 | First playing team |
| team2 | Second playing team |
| venue | Stadium where match is played |
| toss_winner | Team that won the toss |
| toss_decision | Decision made by toss winner (Bat/Field) |
| stage | Stage of tournament (Group/Playoff/Final) |
| match_winner | Target variable — who won the match |

---

## Exploratory Data Analysis

Four key insights were derived from the data:

1. **Team Win Counts** — Some teams dominate wins historically in IPL 2022
2. **Toss Impact** — Contrary to popular belief, winning the toss does not significantly improve chances of winning the match
3. **Venue Distribution** — Certain venues hosted significantly more matches than others
4. **Toss Decision Impact** — Choosing to field after winning the toss was slightly more common but did not guarantee a win

All visualizations were built using **Plotly Express** for interactive exploration.

---

## ML Pipeline

```
Raw Data
   ↓
Data Cleaning (checked for nulls & inconsistencies)
   ↓
Feature Selection (removed post-match/leakage columns)
   ↓
Label Encoding (converted categorical text to numbers)
   ↓
Train/Test Split (80% train, 20% test)
   ↓
Model Training (Random Forest & KNN)
   ↓
Evaluation (Accuracy Score & Confusion Matrix)
   ↓
Prediction on New Match Data
```

---

## Models Used

### 1. Random Forest Classifier
- `n_estimators = 100`
- `random_state = 42`
- **Accuracy: 33%**

### 2. K-Nearest Neighbors (KNN)  Best Model
- `n_neighbors = 3`
- Hyperparameter tuning performed on K values (1, 3, 5, 7)
- **Accuracy: 40%**

### Accuracy Comparison

| Model | Accuracy |
|-------|----------|
| Random Guessing (baseline) | ~10% |
| Random Forest | 33% |
| KNN (n=3) | **40%**  |

> The KNN model performs **4x better than random guessing** across 10 possible team outcomes.

---

## Why Not Higher Accuracy?

The dataset contains only **74 matches** from IPL 2022. With 10 teams to predict between, a small dataset limits the model's ability to learn strong patterns. Potential improvements include:

- Adding multiple IPL seasons for more training data
- Engineering features like team win rate and head-to-head records
- Addressing team ordering asymmetry (team1 vs team2 sensitivity)

---

## Project Structure

```
IPL-Match-Predictor/
│
├── Book_ipl22_ver_33.csv      # Dataset
├── IPLprediction.ipynb        # Main notebook
└── README.md                  # Project documentation
```

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/KrishJariwala678/IPL-Match-Predictor.git
```

2. Install required libraries
```bash
pip install pandas numpy scikit-learn plotly
```

3. Open the notebook
```bash
jupyter notebook IPLprediction.ipynb
```

4. Run all cells in order

---

## Feature Encoding Reference

| Team | Encoded Value |
|------|--------------|
| Bangalore | 0 |
| Chennai | 1 |
| Delhi | 2 |
| Gujarat | 3 |
| Hyderabad | 4 |
| Kolkata | 5 |
| Lucknow | 6 |
| Mumbai | 7 |
| Punjab | 8 |
| Rajasthan | 9 |

| Toss Decision | Encoded Value |
|---------------|--------------|
| Bat | 0 |
| Field | 1 |

| Stage | Encoded Value |
|-------|--------------|
| Final | 0 |
| Group | 1 |
| Playoff | 2 |

---

## Libraries Used

- `pandas` — Data manipulation
- `numpy` — Numerical operations
- `scikit-learn` — ML models, encoding, evaluation
- `plotly` — Interactive visualizations

---

## Key Learnings

- Understood the difference between **pre-match and post-match features** (data leakage)
- Applied **Label Encoding** consistently across related columns
- Compared two ML algorithms and performed **hyperparameter tuning**
- Learned that **model accuracy depends heavily on dataset size**
- Built and interpreted a **Confusion Matrix**

---

## Author

**Krish Jariwala**  
GitHub: [@KrishJariwala678](https://github.com/KrishJariwala678)

---

*Built with ❤️ during IPL 2026 season*
