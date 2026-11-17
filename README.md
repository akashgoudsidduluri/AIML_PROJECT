# Student Performance Prediction

This project applies machine learning to predict whether a student will achieve low or high academic performance based on demographic, family, school, and behavioral factors. The implementation is centered on the final notebook in `code/AIML_PROJECT_FINAL_IMPLEMENTATION.ipynb`, and the supporting research paper is available at `docs/research_paper.pdf`.

## Project overview

The goal is to classify students into two categories based on their final grade (`G3`):

- Low performance: `G3 < 10`
- High performance: `G3 >= 10`

The dataset contains student attributes such as age, sex, school, guardian, study time, family support, alcohol consumption, absences, and prior grades (`G1`, `G2`). These features are used to estimate the final academic outcome.

## Dataset

The project uses the well-known Student Performance dataset, with the math course data stored in:

- `student+performance/datasets/student-mat.csv`
- `student+performance/datasets/student-por.csv`

Supporting metadata and dataset documentation are provided in:

- `student+performance/datasets/student.txt`
- `student+performance/datasets/student-merge.R`

### Dataset characteristics

- 395 records in the math dataset
- 33 columns
- 17 categorical and 16 numerical features
- Target variable: `G3` final grade

## Methodology

The notebook follows a full machine learning workflow:

1. Data loading and inspection
2. Exploratory data analysis
3. Feature engineering and preprocessing
4. Train/test split (80/20)
5. Model training and comparison
6. Hyperparameter tuning using `GridSearchCV`
7. Class imbalance handling with resampling methods
8. Model evaluation using accuracy, precision, recall, F1-score, and confusion matrices

### Preprocessing

The pipeline combines:

- `ColumnTransformer`
- `OneHotEncoder` for categorical variables
- `StandardScaler` for numerical variables

This allows both categorical and numeric data to be handled in a consistent way before model training.

## Models evaluated

The project compares several supervised learning models, including:

- K-Nearest Neighbors (KNN)
- Decision Tree
- Random Forest
- Logistic Regression
- Support Vector Machine (SVM)
- Naive Bayes
- Neural Network

Additional imbalance-aware experiments were also tested using:

- Random Oversampling
- SMOTE
- class-weight balancing for SVM

## Key results

The final tuned comparison shows that the SVM model delivered the strongest performance.

| Model | Accuracy | Macro Precision | Macro Recall | Macro F1 |
|---|---:|---:|---:|---:|
| KNN | 0.797 | 0.776 | 0.751 | 0.761 |
| Decision Tree | 0.873 | 0.854 | 0.886 | 0.864 |
| Random Forest | 0.873 | 0.854 | 0.886 | 0.864 |
| Logistic Regression | 0.873 | 0.854 | 0.886 | 0.864 |
| SVM | 0.899 | 0.880 | 0.905 | 0.889 |
| Naive Bayes | 0.747 | 0.712 | 0.704 | 0.707 |
| Neural Network | 0.873 | 0.857 | 0.857 | 0.857 |

### Best model summary

The best-performing model was the tuned SVM, with:

- Accuracy: 89.9%
- Macro precision: 0.880
- Macro recall: 0.905
- Macro F1-score: 0.889

This model correctly classified most students in both the low and high performance groups and was selected as the final recommendation for prediction.

## Repository structure

```text
AIML_PROJECT/
├── code/
│   └── AIML_PROJECT_FINAL_IMPLEMENTATION.ipynb
├── docs/
│   └── research_paper.pdf
├── student+performance/
│   └── datasets/
│       ├── student-mat.csv
│       ├── student-por.csv
│       ├── student-merge.R
│       └── student.txt
├── README.md
└── .gitignore (if present in the repo)
```

## How to run

This project is implemented primarily in a Jupyter notebook, so the recommended workflow is:

1. Open the notebook in Jupyter or VS Code.
2. Ensure the required Python libraries are installed.
3. Run the cells in order.

### Required Python libraries

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- imbalanced-learn

Install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
```

Then open:

```bash
code/AIML_PROJECT_FINAL_IMPLEMENTATION.ipynb
```

## Conclusion

The project demonstrates that student academic performance can be predicted with strong accuracy using a combination of school, demographic, and behavioral attributes. Among the tested models, SVM provided the best predictive power, making it the most suitable final model for the classification task.

This repository serves as both a reproducible research implementation and a practical machine-learning case study for educational performance prediction.
