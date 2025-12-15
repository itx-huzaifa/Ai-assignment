# Ai-assignment

# MNIST Handwritten Digit Recognition using Keras

This repository contains a solution for training a neural network on the MNIST dataset to recognize handwritten digits. The project is implemented using **TensorFlow/Keras** in a Google Colab notebook (`.ipynb`).

## Project Overview
The goal of this project is to build a neural network to classify 28x28 pixel grayscale images of handwritten digits (0-9). The dataset consists of 60,000 training images and 10,000 test images.

### Key Specifications
* **Dataset:** MNIST
* **Input Shape:** 28x28 pixels (Flattened to 784 features)
* **Hidden Layers:** 1 hidden layer with 10 neurons
* **Activation Functions:** 'ReLU' (hidden), 'Softmax' (output)
* **Optimizer:** Adam
* **Loss Function:** Sparse Categorical Crossentropy
* **Evaluation Metric:** Accuracy

---

##  Model Architecture
The model is designed with a specific constraint of using a small hidden layer to observe its impact on learning and overfitting.

1.  **Input Layer:** Flattens the 28x28 image into a vector of 784 neurons.
2.  **Hidden Layer:** Dense layer with **10 neurons** using `ReLU` activation.
3.  **Output Layer:** Dense layer with **10 neurons** (representing digits 0-9) using `Softmax` activation.

---

##  Results & Analysis (Part a)

### Accuracy Plots
The model was trained for 15 epochs. Below is the analysis of the Training vs. Validation (Test) accuracy curves.

*(Note: Please refer to the plot image generated in the notebook)*

### Conceptual Analysis: Is the model overfitting?
**Conclusion: No, the model is NOT overfitting.**

**Reasoning:**
1.  **Small Generalization Gap:** The gap between the **Training Accuracy** and **Test (Validation) Accuracy** is very small throughout the training process. In overfitting scenarios, the training accuracy continues to rise (memorizing noise) while test accuracy drops or plateaus significantly lower.
2.  **Stable Test Performance:** The test accuracy curve increases and stabilizes (plateaus) along with the training curve. It does not show a downward trend, which indicates the model has learned generalizable patterns rather than memorizing specific training examples.
3.  **Architecture Constraint:** By limiting the hidden layer to only 10 neurons, we introduced an "information bottleneck." This forces the model to learn only the most dominant features of the digits, naturally preventing it from having enough capacity to overfit/memorize the data.

---

##  Theoretical Discussion on Overfitting (Part c)

### Scenario
**Question:** IF the model were overfitting (e.g., Training Accuracy 99%, Test Accuracy 80%), how would you remove it?

### Proposed Solution
If the model was overfitting, it means it is too complex for the amount of data available and is "memorizing" the answers. To fix this, I would use **Dropout**.

#### Method: Dropout
* **What it is:** Dropout is a regularization technique where randomly selected neurons are ignored (dropped out) during the training process. For example, a dropout rate of 0.2 means 20% of neurons are randomly deactivated in each update.
* **Why use it?** This prevents neurons from co-adapting too much. It forces the network to learn more robust features because it cannot rely on any single specific neuron to make a prediction. This essentially simulates training a large number of different neural networks and averaging their predictions, which drastically reduces variance and overfitting.

#### Alternative Methods
* **Early Stopping:** Stop training as soon as the validation loss starts to increase.
* **L1/L2 Regularization:** Add a penalty to the loss function for large weights, preventing the model from assigning too much importance to specific features.

---
