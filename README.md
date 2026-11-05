# AttriSense – Employee Attrition Risk Prediction and Explanation

**Predict → Explain → Simulate**

AttriSense is a Deep Learning project that uses an Artificial Neural Network (ANN) to predict employee attrition risk. It combines prediction, explainability using SHAP, and What-If analysis to help understand the factors influencing employee attrition predictions.

## Project Overview

Employee attrition occurs when employees leave an organization. Identifying employees who may be at risk of leaving can help organizations consider appropriate support and retention strategies.

AttriSense follows three main steps:

- **Predict:** Uses an Artificial Neural Network to estimate the probability of an employee leaving.
- **Explain:** Uses SHAP to understand which employee features influence the model's predictions.
- **Simulate:** Uses What-If analysis to observe how hypothetical changes in employee features affect predicted attrition risk.

## Key Features

- Employee attrition prediction using an ANN.
- Data preprocessing using StandardScaler and OneHotEncoder.
- Class weighting to address class imbalance.
- Low, Medium, and High attrition risk classification.
- Model evaluation using accuracy, precision, recall, F1-score, and a confusion matrix.
- Global and individual model explanations using SHAP.
- What-If analysis for hypothetical employee scenarios.

## Dataset

- **Dataset:** Employee Attrition & HR Analytics 2026
- **Source:** [Kaggle – Employee Attrition & HR Analytics 2026](https://www.kaggle.com/datasets/uditjain13/employee-attrition-and-hr-analytics-2026)
- **Records:** 5,000 employees
- **Original Features:** 29 columns
- **Target Variable:** `attrition`
- **License:** CC0 – Public Domain

## Model Architecture

The project uses a Feed-Forward Artificial Neural Network with the following architecture:

| Layer | Configuration |
|---|---|
| Input Layer | 69 features |
| Hidden Layer 1 | 64 neurons, ReLU |
| Dropout | 0.3 |
| Hidden Layer 2 | 32 neurons, ReLU |
| Dropout | 0.3 |
| Output Layer | 1 neuron, Sigmoid |

**Training configuration:**
- Optimizer: Adam
- Loss Function: Binary Cross-Entropy
- Early Stopping: Enabled
- Maximum Epochs: 100
- Batch Size: 32

## Results

The weighted ANN was evaluated on a test set of 750 employee records.

| Metric | Result |
|---|---:|
| Accuracy | 67.87% |
| Leave Precision | 33.12% |
| Leave Recall | 78.36% |
| Leave F1-Score | 46.56% |

**Why recall matters:** The project prioritizes Leave-class recall because identifying employees who may leave is the primary objective of an early-warning system.

## Technologies Used

- Python
- TensorFlow / Keras
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- SHAP
- Google Colab

## Repository Contents

- `AttriSense.ipynb` – Main project notebook containing preprocessing, model training, evaluation, SHAP explanations, and What-If analysis.
- `AttriSense.ipynb - Colab.pdf` – PDF version of the notebook.
- `AttriSense.pptx` – Project presentation.
- `AttriSense_Project_Report.pdf` – Detailed project report.
- `employee_attrition_hr_2026.xlsx` – Dataset used for the project.

## Project Team

| Name | Registration Number |
|---|---|
| Divyanshu Agwekar | 2430010132 |
| Puru Bansal | 2430010153 |

**Institution:** Manipal University Jaipur  
**Course:** Deep Learning (DSE3120)  
**Section:** VB

## Disclaimer

AttriSense is an academic prototype developed and tested using Google Colab. Its predictions are estimates based on the dataset and should not be treated as confirmed future employee behaviour or used as the sole basis for employment decisions.
