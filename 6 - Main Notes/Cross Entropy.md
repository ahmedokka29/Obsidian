2024-07-20 - 23:50
Status: 
Tags: [[losses]] [[keras]]
# Cross Entropy

The terms "categorical cross entropy," "sparse categorical cross entropy," and "cross entropy" are often used in the context of neural networks and classification tasks. Here’s a detailed breakdown of the differences:

## Categorical Cross Entropy

- **Target Labels Format**: One-hot encoded vectors.
  - Example for 3 classes: Class 1 -> `[1, 0, 0]`, Class 2 -> `[0, 1, 0]`, Class 3 -> `[0, 0, 1]`.
- **Usage**: Used when the number of classes is relatively small, and the target labels are already in one-hot encoded form.
- **Computation**: 
  - Formula: $\sum_{i} y_i \log(\hat{y}_i)$ , where $y_i$ is the one-hot encoded true label and ( $\hat{y}_i)$ is the predicted probability for class $i$ .
  - In code (e.g., TensorFlow/Keras): `categorical_crossentropy`.

## Sparse Categorical Cross Entropy

- **Target Labels Format**: Integer labels representing the class indices.
  - Example for 3 classes: Class 1 -> `0`, Class 2 -> `1`, Class 3 -> `2`.
- **Usage**: Useful when the number of classes is large, or when working with datasets where target labels are in integer form (sparse representation).
- **Computation**: 
  - Formula: $-\log(\hat{y}_{true\_label})$ , where $\hat{y}_{true\_label}$  is the predicted probability for the true class label.
  - In code (e.g., TensorFlow/Keras): `sparse_categorical_crossentropy`.

## Cross Entropy

- **General Definition**: Cross entropy is a measure of the difference between two probability distributions. It is a broader term and can refer to different specific forms, including binary cross entropy and categorical cross entropy.
- **Binary Cross Entropy**: Used for binary classification problems.
  - **Target Labels Format**: Binary labels (0 or 1).
  - **Computation**: 
    - Formula: $\text{Loss}_{\text{binary}} = -[y \log(\hat{y}) + (1 - y) \log(1 - \hat{y})]$ , where ( y ) is the true label and $(\hat{y})$  is the predicted probability.
    - In code (e.g., TensorFlow/Keras): `binary_crossentropy`.
- **Categorical Cross Entropy (Detailed Above)**: A specific case of cross entropy used for multi-class classification problems with one-hot encoded labels.
- **Sparse Categorical Cross Entropy (Detailed Above)**: Another specific case of cross entropy used for multi-class classification problems with integer labels.

## Summary

- **Cross Entropy**: A general term for a family of loss functions that measure the difference between probability distributions.
  - Includes both binary cross entropy and categorical cross entropy.
- **Categorical Cross Entropy**: A specific type of cross entropy used for multi-class classification with one-hot encoded labels.
- **Sparse Categorical Cross Entropy**: A specific type of cross entropy used for multi-class classification with integer labels.

## Example in Keras

```python
from tensorflow.keras.losses import CategoricalCrossentropy, SparseCategoricalCrossentropy, BinaryCrossentropy

# Example usage for categorical cross entropy
categorical_loss = CategoricalCrossentropy()

# Example usage for sparse categorical cross entropy
sparse_categorical_loss = SparseCategoricalCrossentropy()

# Example usage for binary cross entropy
binary_loss = BinaryCrossentropy()
```

In practice, you choose the appropriate loss function based on the format of your target labels and the nature of your classification problem (binary vs. multi-class).


# Reference