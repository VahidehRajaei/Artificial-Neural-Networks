### MLP Classifier and XAI Analysis on Breast Cancer Dataset
#### Project Overview
This repository contains the solution for the Üsküdar University Artificial Neural Networks (Yapay Sinir Ağları) Midterm Project. 


The goal was to develop, optimize, and thoroughly interpret a Multilayer Perceptron (MLP) classification model on a biomedical dataset.
This project emphasizes not only achieving high performance but also explaining why the model makes its decisions using Explainable AI (XAI) techniques, specifically SHAP (SHapley Additive exPlanations) analysis.

#### Dataset
##### Name: Breast Cancer Wisconsin (Diagnostic) Dataset

##### Task: Binary Classification (Malignant vs. Benign)

#### 1. Project Structure and Content
<img width="1321" height="155" alt="image" src="https://github.com/user-attachments/assets/d44dff57-bd86-4192-9974-f5326cd6e3a7" />

#### 2. Setup and Installation
To run the notebook, you need Python and the following key libraries.

* **Prerequisites:** Ensure you have Python 3.8+ installed.

* **Dependencies:** Install the required packages using pip.
  
*pip install pandas numpy scikit-learn matplotlib seaborn optuna shap*

#### 3. Key Steps and Methodology
##### 3.1 Data Preparation (Steps 1-5)
* **Preprocessing:** Data was confirmed to have no missing values. Outliers were handled using IQR-based Capping to preserve data integrity.

* **Scaling:** All features were scaled using StandardScaler for optimal MLP convergence.

* **Splitting:** Data was strictly split into Training (70%), Validation (10%), and Test (20%).
##### 3.2 Model Training and Optimization (Steps 6, 7, 9)
 * **Manual Comparison:** 5 distinct MLP architectures (Simple, Medium, Wide, Deep) were trained and compared on the Validation Set metrics (Accuracy, F1-Score, ROC-AUC).
 * **Hyperparameter Optimization:** Optuna was used to maximize Validation Accuracy over 150 trials, searching the optimal combination of layer sizes, learning rate, regularization ($\alpha$), and activation functions.
##### 3.3 Final Evaluation (Step 8)
The final selected model was rigorously evaluated on the unseen Test Set, generating the Confusion Matrix and ROC Curve.
#### 4. Core Findings and XAI Interpretation (Step 10)
##### High Performance Metrics
The model achieved near-perfect discriminative power:
ROC-AUC: $\approx 0.992$
F1-Score: $> 0.97$
Feature Sensitivity (SHAP Analysis)
##### The SHAP analysis revealed the true biological reliance of the model:
* **Dominant Features (Global Importance):** The model is overwhelmingly sensitive to size and irregularity metrics, primarily worst area, mean area, mean texture, and mean radius.
* **Directional Impact:** High values in these dominant features consistently push the prediction toward the Malignant class.
* **Architectural Comparison:** SHAP confirmed that both the manual and Optuna models learned the same underlying feature hierarchy, although Optuna refined parameters to achieve peak stability and performance.
#### 5. Usage Example (Running the Notebook)
##### To run the notebook and generate all analyses:
* ###### 1. Open the file in Jupyter/Colab.
* ###### 2. Ensure all dependencies are installed.
* ###### 3. Run all cells in sequence (Run All).

*The SHAP calculation for the PermutationExplainer may take a few minutes.*
