# Sciqus-AI-ML-Tasks
AI Task 1 – Industrial Machine Failure Prediction

1. Understanding of the Data
The dataset represents industrial machine operations, where each row corresponds to a single operation
performed by a machine. The objective is to predict whether an operation results in a machine failure.
The dataset includes:
• Unique identifiers (UDI, Product ID) to identify operations and products
• Machine type (Type), a categorical feature indicating the type of machine
• Process measurements, including:
o Air temperature
o Process temperature
o Rotational speed
o Torque
o Tool wear time
• Target variable (Machine failure), a binary indicator where:
o 0 = No failure
o 1 = Failure
• Failure Type, a text column describing the failure in words
This is a binary classification problem commonly seen in predictive maintenance systems, where the goal
is to detect potential failures using sensor data.

2. Data Preprocessing and Feature Handling
Before modeling, the dataset was inspected for structure, data types, and missing values. No missing values
were observed.
Feature handling decisions were made as follows:
• Identifier columns (UDI, Product ID) were removed because they do not carry predictive
information and only serve as unique references.
• Failure Type was dropped because it is a textual description directly related to the target variable
and could lead to data leakage if used as a feature.
• Machine Type (Type) is a categorical feature and was encoded using one-hot encoding to make it
suitable for machine learning models.
• Numerical sensor features were standardized to ensure consistent scaling across features, which is
especially important for models like Logistic Regression.
A preprocessing pipeline was created using ColumnTransformer to ensure that categorical encoding and
numerical scaling are applied correctly and consistently.

3. Model Selection
Logistic Regression was selected as the machine learning model for this task.
The reasons for choosing Logistic Regression are:
• It is well-suited for binary classification problems
• It is simple and interpretable, making it easier to understand feature influence
• It aligns with the task requirement to avoid complex or black-box models
• It produces probability outputs that are useful in real-world failure prediction systems
The focus of this task is correctness and reasoning rather than maximizing performance, which makes
Logistic Regression an appropriate choice.

4. Model Training and Evaluation
The dataset was split into training and testing sets using an 80–20 stratified split. Stratification was applied
to preserve the distribution of failure and non-failure cases in both sets.
The model was trained only on the training data to avoid data leakage.
For evaluation, multiple metrics were used:
• Accuracy
• Confusion Matrix
• Precision, Recall, and F1-Score
Relying only on accuracy can be misleading in failure prediction problems because failures typically occur
less frequently. Therefore, recall for the failure class is especially important, as missing a failure can be more
costly than raising a false alarm.
The confusion matrix and classification report provided a clear understanding of how well the model
identifies failure and non-failure cases.

5. Results Interpretation
The model achieved reasonable performance while maintaining simplicity and interpretability.
The evaluation metrics showed that the model is able to distinguish between failure and non-failure
operations, though some failures are still missed, which is expected in real-world industrial datasets with
class imbalance.
This result demonstrates a correct and realistic machine learning approach rather than an over-fitted or
misleadingly high-accuracy solution.

6. Limitations and Future Improvements
If more time and resources were available, the following improvements could be explored:
• Feature engineering based on trends or interactions between sensor values
• Cost-sensitive learning to penalize missed failures more heavily
• Threshold tuning to improve recall for failure cases
• Cross-validation for more robust performance estimation
• Incorporating temporal or sequential patterns if historical machine data is available
These improvements were not implemented in order to keep the solution simple, explainable, and aligned
with the task constraints.

Conclusion
This task was approached with a focus on correct machine learning practices, clear reasoning, and
realistic evaluation. The solution avoids unnecessary complexity while demonstrating a strong
understanding of data preprocessing, model selection, and evaluation techniques relevant to real-world
industrial machine failure prediction.