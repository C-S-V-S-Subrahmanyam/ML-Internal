### **Data Pre-processing in Machine Learning (Short & Precise Guide)**  

**Why is Data Pre-processing Needed?**  
Real-world data is often noisy, incomplete, or in an unusable format. Pre-processing ensures data is clean, structured, and suitable for machine learning, improving accuracy and efficiency.

### **Steps of Data Pre-processing:**

1. **Getting the Dataset**  
   - Data is collected in formats like CSV, XLSX, or HTML.  
   - CSV (Comma-Separated Values) is commonly used for large datasets.

2. **Importing Libraries**  
   - `numpy (nm)`: Handles mathematical operations.  
   - `matplotlib.pyplot (mpt)`: Plots graphs/charts.  
   - `pandas (pd)`: Handles datasets and data manipulation.  

3. **Importing Dataset**  
   - `pd.read_csv('file.csv')` loads the dataset.  
   - **Extracting Independent & Dependent Variables**  
     ```python
     x = data_set.iloc[:, :-1].values  # Independent variables  
     y = data_set.iloc[:, -1].values   # Dependent variable  
     ```

4. **Handling Missing Data**  
   - Replacing missing values with the **mean** using `SimpleImputer`:  
     ```python
     from sklearn.impute import SimpleImputer  
     imputer = SimpleImputer(strategy='mean')  
     x[:, 1:3] = imputer.fit_transform(x[:, 1:3])  
     ```

5. **Encoding Categorical Data**  
   - Convert text data (e.g., Country, Purchased) into numbers:  
     ```python
     from sklearn.preprocessing import LabelEncoder, OneHotEncoder
     label_encoder = LabelEncoder()
     x[:, 0] = label_encoder.fit_transform(x[:, 0])  # Label encoding  
     ```
   - **Dummy Variables (OneHot Encoding) for multiple categories**  
     ```python
     from sklearn.preprocessing import OneHotEncoder
     onehot_encoder = OneHotEncoder()
     x = onehot_encoder.fit_transform(x).toarray()
     ```

6. **Splitting Dataset into Training & Test Set**  
   - Ensures better model generalization.  
     ```python
     from sklearn.model_selection import train_test_split  
     x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=0)  
     ```

7. **Feature Scaling**  
   - Standardizes data so no feature dominates others.  
     ```python
     from sklearn.preprocessing import StandardScaler  
     scaler = StandardScaler()  
     x_train = scaler.fit_transform(x_train)  
     x_test = scaler.transform(x_test)  # Only transform, no fitting on test set  
     ```


### **Summary**  
Data pre-processing ensures that raw data is clean and structured before feeding it into a machine learning model. It involves handling missing values, encoding categorical data, splitting the dataset, and feature scaling to improve model performance.

