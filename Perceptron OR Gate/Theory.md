## **Perceptron-OR Rule using the Perceptron Training Algorithm**:  

---

### **AIM**  
**IMPLEMENT PERCEPTRON-OR RULE USING OR GATE USING PERCEPTRON TRAINING RULE**  

---

### **DESCRIPTION**  

#### **Perceptron:**  
A **Perceptron** is an artificial neuron that performs binary classification. It was introduced by **Frank Rosenblatt** in **1957** and operates using weighted inputs and a threshold-based activation function. The Perceptron algorithm is a fundamental **supervised learning** technique used for **binary classification**.  

#### **Perceptron Learning Rule:**  
- Start with **random weights**.  
- Iteratively update weights using training examples.  
- If misclassification occurs, modify the weights using the **Perceptron Training Rule**:  

\[
w_i = w_i + \Delta w_i
\]

Where:  
\[
\Delta w_i = \text{Learning Rate} \times (t - o) \times x_i
\]
- Here, **t** is the **target output**, and **o** is the **actual output**.

---

### **Algorithm**  

1. **Import Required Libraries**  
```python
import numpy as np
```

2. **Initialize Input and Output Variables**  

**Truth Table of OR Gate:**  
\[
\begin{array}{|c|c||c|}
\hline
x_1 & x_2 & Output \\
\hline
0 & 0 & 0 \\
0 & 1 & 1 \\
1 & 0 & 1 \\
1 & 1 & 1 \\
\hline
\end{array}
\]

```python
features = np.array([
    [0,0],
    [0,1],
    [1,0],
    [1,1]
])
labels = np.array([0, 1, 1, 1])  # OR Gate
```

3. **Initialize Network Parameters**  
- **Epochs** (number of training iterations)  
- **Threshold** (decision boundary)  
- **Learning Rate**  
- **Weights** (random initialization)  

```python
epochs = int(input('Enter the number of Epochs: '))
threshold = float(input('Enter the Threshold: '))
learning_rate = float(input('Enter the Learning Rate: '))

# Initialize weights randomly
weights = np.array([
    float(input('Enter initial weight for x1: ')),
    float(input('Enter initial weight for x2: '))
])
```

4. **Training the Perceptron**  

```python
for epoch in range(epochs):
    print(f"Epoch {epoch+1}")
    global_error = 0

    for i in range(features.shape[0]):
        x1, x2 = features[i]
        actual_output = labels[i]

        # Compute Weighted Sum
        weighted_sum = x1 * weights[0] + x2 * weights[1]

        # Activation Function (Thresholding)
        predicted_output = 1 if weighted_sum >= threshold else 0

        # Calculate Error
        error = actual_output - predicted_output
        global_error += abs(error)

        # Print Predictions
        print(f"Input: {x1, x2}, Predicted: {predicted_output}, Actual: {actual_output}, Error: {error}")

        # Update Weights using Perceptron Learning Rule
        weights[0] += learning_rate * error * x1
        weights[1] += learning_rate * error * x2

    print("---------------------------")

    # Stop training if no errors
    if global_error == 0:
        break

print("Final Weights:", weights)
```

---

### **INPUT/OUTPUT EXAMPLE**  

#### **User Inputs:**  
```
Enter the number of Epochs: 10
Enter the Threshold: 0.5
Enter the Learning Rate: 0.1
Enter initial weight for x1: 0.2
Enter initial weight for x2: 0.3
```

#### **Training Output (Example Output for OR Gate)**  
```
Epoch 1
Input: (0, 0), Predicted: 0, Actual: 0, Error: 0
Input: (0, 1), Predicted: 0, Actual: 1, Error: 1
Input: (1, 0), Predicted: 0, Actual: 1, Error: 1
Input: (1, 1), Predicted: 1, Actual: 1, Error: 0
---------------------------
Epoch 2
Input: (0, 0), Predicted: 0, Actual: 0, Error: 0
Input: (0, 1), Predicted: 1, Actual: 1, Error: 0
Input: (1, 0), Predicted: 1, Actual: 1, Error: 0
Input: (1, 1), Predicted: 1, Actual: 1, Error: 0
---------------------------
Final Weights: [0.3 0.4]
```

---

### **Conclusion**  
- **Perceptron successfully learns the OR function** after training.  
- **Final weights** indicate how the Perceptron has adapted to classify the OR gate correctly.  
- The training stops **once all inputs are classified correctly**.  

---

