# AttriSense – Employee Attrition Risk Prediction and Explanation

**Predict → Explain → Simulate**

AttriSense is a Deep Learning project that predicts employee attrition risk using an Artificial Neural Network (ANN). It combines prediction, explainable AI using SHAP, and what-if simulations to help understand factors associated with employee attrition.

The project was developed as part of the **Deep Learning (DSE3120)** course at Manipal University Jaipur.

## Project Overview

Employee attrition refers to employees leaving an organization. Identifying potential attrition risks can help organizations better understand employee-related patterns and explore possible retention strategies.

AttriSense uses historical HR data to estimate the probability of an employee leaving. It also provides explanations of the model's predictions and allows hypothetical changes to selected features to be explored.

## Key Features

- **Employee Attrition Prediction:** Predicts whether an employee is likely to stay or leave.
- **Artificial Neural Network:** Uses a feedforward ANN for binary classification.
- **Class Imbalance Handling:** Uses class weights to improve detection of the less frequent Leave class.
- **Model Evaluation:** Evaluates performance using accuracy, precision, recall, F1-score, and a confusion matrix.
- **SHAP Explainability:** Identifies influential features globally and explains individual predictions.
- **What-If Analysis:** Explores how hypothetical changes in employee attributes affect predicted attrition risk.
- **Risk Classification:** Groups predictions into Low, Medium, and High risk categories.
- **Visual Analysis:** Includes training and validation plots, confusion matrices, SHAP plots, and risk distribution charts in the Jupyter notebook.

## Dataset

The project uses the Employee Attrition and HR Analytics 2026 dataset.

- **Dataset size:** 5,000 employee records
- **Original columns:** 29
- **Target variable:** `attrition`
- **Target classes:** Stay (`No`) and Leave (`Yes`)
- **Target distribution:** 4,105 Stay records and 895 Leave records

**Dataset source:** [Employee Attrition and HR Analytics 2026 – Kaggle](https://www.kaggle.com/datasets/uditjain13/employee-attrition-and-hr-analytics-2026)

The dataset includes employee demographics, job information, compensation, work conditions, performance, engagement, burnout, and other HR-related attributes.

## Methodology

### 1. Data Preprocessing

- Loaded the dataset using Pandas.
- Removed the `employee_id` column from the input features.
- Separated the target variable from the input features.
- Encoded categorical variables.
- Scaled numerical features.
- Split the dataset into training, validation, and test sets.

### 2. Train, Validation, and Test Split

| Dataset | Records | Percentage |
|---|---:|---:|
| Training | 3,500 | 70% |
| Validation | 750 | 15% |
| Testing | 750 | 15% |
| **Total** | **5,000** | **100%** |

After preprocessing, the model uses 69 input features.

### 3. ANN Model Architecture

The project uses a feedforward Artificial Neural Network for binary classification.

| Layer | Configuration |
|---|---|
| Input layer | 69 features |
| Hidden layer 1 | 64 neurons, ReLU activation |
| Dropout | 30% |
| Hidden layer 2 | 32 neurons, ReLU activation |
| Output layer | 1 neuron, Sigmoid activation |

**Training configuration:**

- Optimizer: Adam
- Loss function: Binary Cross-Entropy
- Early stopping: Enabled
- Maximum epochs: 100
- Batch size: 32
- Class weighting: Enabled

The sigmoid output produces a probability that is used to classify an employee as Stay or Leave at the selected classification threshold.

### 4. Model Evaluation

The model is evaluated on the held-out test set. Since the dataset contains fewer Leave cases than Stay cases, the project pays particular attention to recall for the Leave class.

The notebook includes the classification report, confusion matrix, and training and validation performance plots.

## Results

The weighted ANN was evaluated on a test set of 750 employee records.

### Model Performance

| Metric | Result |
|---|---:|
| Accuracy | 70.67% |
| Leave Precision | 33.96% |
| Leave Recall | 67.91% |
| Leave F1-Score | 45.27% |

### Confusion Matrix

| Actual / Predicted | Stay | Leave |
|---|---:|---:|
| Stay | 439 | 177 |
| Leave | 43 | 91 |

The model correctly identified 91 of the 134 actual Leave cases in the test set.

### Why Recall Matters

The project prioritizes **Leave-class recall** because identifying employees who may leave is the primary objective of an early-warning system. Higher recall helps reduce the number of potential leavers missed by the model.

However, the relatively low Leave precision indicates that some employees predicted to leave actually belong to the Stay class. The model's predictions should therefore be treated as indicators for further investigation, not definitive conclusions.

## Explainable AI with SHAP

SHAP (SHapley Additive exPlanations) is used to understand how input features contribute to model predictions.

The notebook includes:

- **Global feature importance:** Highlights features that influence predictions across the evaluated data.
- **SHAP summary plot:** Shows how feature values relate to their contributions to model output.
- **Individual explanation:** Explains the contributions of features for a selected employee.
- **Waterfall plot:** Visualizes how feature contributions move a prediction away from the model's baseline output.

Features examined include burnout score, engagement score, manager support, salary hike percentage, work-life balance, performance rating, perceived AI job risk, and last review score.

SHAP explains the behavior of the trained model; it does not establish that a feature causes employee attrition.

## What-If Analysis

The what-if analysis allows hypothetical changes to selected employee attributes to be evaluated using the trained model.

Examples explored in the project include:

| Scenario | Original Value | Hypothetical Value | Predicted Risk Change |
|---|---:|---:|---:|
| Reduce overtime hours per week | 10.5 | 5 | 24.92% → 24.07% |
| Increase engagement score | 8.8 | 9.5 | 24.92% → 23.34% |

These examples demonstrate how predicted risk can change when selected inputs are modified while other inputs are held constant.

**Important:** These are hypothetical model outputs, not evidence that changing these factors will cause an actual reduction in attrition.

## Risk Classification

Predicted attrition probabilities are grouped into three categories:

| Risk Level | Predicted Probability |
|---|---|
| Low | Below 30% |
| Medium | 30% to below 60% |
| High | 60% or higher |

The notebook visualizes the distribution of employees across these risk levels.

These thresholds are project-defined categories and should not be interpreted as validated organizational risk standards.

## Technologies Used

- Python
- TensorFlow / Keras
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- SHAP
- OpenPyXL
- Google Colab / Jupyter Notebook

## Project Structure

```text
AttriSense/
├── AttriSense.ipynb
├── AttriSense.ipynb - Colab.pdf
├── AttriSense.pptx
├── AttriSense_Project_Report.pdf
├── README.md
├── requirements.txt
└── employee_attrition_hr_2026.xlsx
```

The Jupyter notebook contains the preprocessing workflow, model training, evaluation, visualizations, SHAP explanations, and what-if simulations.

## How to Run the Project

### Option 1: Google Colab

1. Open `AttriSense.ipynb` in Google Colab.
2. Upload the dataset file `employee_attrition_hr_2026.xlsx` when prompted by the notebook, if it is not already available.
3. Run the notebook cells in order.
4. Review the model evaluation, plots, SHAP explanations, and what-if analysis.

### Option 2: Run Locally

1. Clone the repository:

   ```bash
   git clone https://github.com/divyanshu-agwekar/AttriSense.git
   ```

2. Navigate to the project folder:

   ```bash
   cd AttriSense
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `AttriSense.ipynb` and run the cells in order.

Ensure the dataset is available at the path expected by the notebook.

## Limitations

- The model learns patterns from the available dataset and may not generalize to every organization.
- The lower Leave precision means some predictions may incorrectly flag employees as potential leavers.
- SHAP explanations describe model behavior and do not prove causation.
- What-if simulations are hypothetical and do not establish real-world outcomes.
- Attrition predictions should not be used as the sole basis for employment decisions.

The project is an educational prototype intended to demonstrate predictive modeling and explainability. Real-world use would require additional validation, privacy safeguards, fairness assessment, and appropriate human oversight.

## Future Improvements

- Tune the classification threshold to balance Leave recall and precision.
- Evaluate performance on additional datasets.
- Improve calibration of predicted probabilities.
- Assess model fairness across relevant employee groups.
- Develop a user-friendly interface for exploring predictions and explanations.

## Team

**Course:** Deep Learning (DSE3120)  
**Institution:** Manipal University Jaipur  
**Section:** VB

- **Divyanshu Agwekar** — Registration No. 2430010132
- **Puru Bansal** — Registration No. 2430010153

---

*AttriSense — Predict → Explain → Simulate*
