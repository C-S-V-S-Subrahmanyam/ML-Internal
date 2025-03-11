### **Naïve Bayes Classifier – Theory**  

**Naïve Bayes** is a supervised learning algorithm based on **Bayes' Theorem**, which calculates conditional probability. It assumes that the presence of a particular feature is independent of other features, making it efficient for classification tasks.  

### **Bayes' Theorem**  
Bayes' theorem calculates the probability of an event occurring based on prior knowledge of related events. The formula involves:  
- **P(A | B)**: Probability of event A occurring given event B has occurred.  
- **P(B | A)**: Probability of event B occurring given event A has occurred.  
- **P(A) and P(B)**: Independent probabilities of A and B occurring.  

### **Advantages of Naïve Bayes**  
- Simple and easy to implement.  
- Works well with large datasets.  
- Performs well even with small amounts of training data.  
- Suitable for text classification, spam filtering, sentiment analysis, and medical diagnosis.  

### **Implementation Steps**  

#### **1. Install Required Libraries**  
To implement Naïve Bayes, essential Python libraries such as NumPy (for mathematical operations), Pandas (for data handling), Matplotlib & Seaborn (for visualization) are required.  

#### **2. Import Dataset**  
A dataset is imported (usually in CSV format), which contains independent variables (features) and a dependent variable (target class).  

#### **3. Separate Independent & Dependent Variables**  
It is necessary to distinguish between **features (input variables)** and **target labels (output variables)** in the dataset.  

#### **4. Split Dataset into Training & Testing Sets**  
The dataset is divided into **training (75%)** and **testing (25%)** subsets.  
- **Training Set**: Used to train the model.  
- **Test Set**: Used to evaluate the model’s performance.  

#### **5. Train the Naïve Bayes Model**  
The **Gaussian Naïve Bayes classifier**, a popular type of Naïve Bayes, is used to train the model using the training data.  

#### **6. Evaluate Model Performance**  
The trained model is tested using various performance metrics:  
- **Accuracy Score**: Measures the proportion of correct predictions.  
- **Confusion Matrix**: A table that shows the number of correct and incorrect predictions for each class. It helps visualize classification performance.  
- **Classification Report**: Provides precision, recall, and F1-score, which help assess the effectiveness of the model.  

### **Conclusion**  
Naïve Bayes is a **fast and effective** classification algorithm, particularly useful for text classification and medical diagnosis. Despite its assumption of feature independence, it delivers **high accuracy** and is widely used in various real-world applications. 🚀
