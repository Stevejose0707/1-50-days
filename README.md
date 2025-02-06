**Kerala Tourism Data Analysis Documentation**

### **1. Introduction**
This document provides an overview of the Kerala Tourism dataset and its corresponding Jupyter Notebook (**kerala_tourism.ipynb**). The notebook analyzes tourism-related data and makes predictions based on various attributes.

### **2. Dataset Overview**
The dataset used in this project is **Kerala_Tourism_Data_with_recommendation.csv**. It contains various attributes related to tourist destinations in Kerala, including:
- **Location Name**: The name of the tourist spot.
- **Category**: Type of tourism (Beach, Hill Station, Wildlife, etc.).
- **Rating**: Visitor ratings.
- **Weather Conditions**: Typical weather at the location.
- **Recommendation**: Suggested tourism category based on attributes.

### **3. Notebook Contents**
The notebook follows these steps:
1. **Import Libraries**
   - Uses Pandas, NumPy for data handling.
2. **Load Dataset**
   - Reads the dataset using `pd.read_csv()`.
3. **Data Exploration**
   - Displays dataset structure with `.head()`, `.tail()`, and `.dtypes`.
   - Checks column names using `.columns`.
4. **Data Preprocessing**
   - Handles missing values.
   - Encodes categorical features using Label Encoding or One-Hot Encoding.
5. **Model Training & Prediction**
   - Uses a machine learning model to predict tourism recommendations.
   - Converts numerical predictions back to original categories using `inverse_transform()`.

### **4. Converting Predictions Back to Original Categories**
If numerical encoding is used for categorical variables, predictions need to be converted back to their original form:
- **Label Encoding Reversal**:
  ```python
  from sklearn.preprocessing import LabelEncoder
  le = LabelEncoder()
  le.fit(original_category_values)
  original_predictions = le.inverse_transform(numerical_predictions)
  ```
- **One-Hot Encoding Reversal**:
  ```python
  from sklearn.preprocessing import OneHotEncoder
  encoder = OneHotEncoder()
  encoder.fit(original_category_array.reshape(-1, 1))
  original_predictions = encoder.inverse_transform(numerical_predictions)
  ```
- **Mapping Dictionary Approach**:
  ```python
  category_mapping = {0: "Beach", 1: "Hill Station", 2: "Wildlife Sanctuary"}
  original_predictions = [category_mapping[num] for num in numerical_predictions]
  ```

### **5. Conclusion**
The notebook provides an analytical approach to predicting tourism recommendations based on various features. Proper data encoding and decoding methods ensure that numerical predictions can be understood in their original form.


