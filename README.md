
---

# **Starbucks Offer Completion Prediction**

## **Project Overview**
Starbucks' personalized rewards program provides targeted promotional offers to customers. However, not all offers are completed, making it crucial to understand **which factors drive offer completion** and how **customer demographics, transactions, and offer characteristics impact engagement**.  

This project **analyzes customer behavior, extracts key insights, and builds a machine learning model** to predict whether an offer will be completed. The results will help Starbucks optimize its marketing strategies, improve customer engagement, and enhance the efficiency of promotions.

---

## **Installation and Setup**

### **Prerequisites**
Ensure you have the following installed:
- Python 3.x  
- Jupyter Notebook or any Python IDE  
- Required libraries:
  ```bash
  pip install pandas numpy matplotlib seaborn scikit-learn
  ```

### **Repository Structure**
This project consists of the **main Jupyter Notebook** and **JSON data files**:

```plaintext
📂 Starbucks_Offer_Prediction
│── Starbucks_Capstone_notebook.ipynb  # Main analysis and modeling notebook
│── portfolio.json                     # Offer details (types, rewards, duration, difficulty)
│── profile.json                        # Customer demographic data
│── transcript.json                     # Customer transactions and interactions with offers
│── README.md                           # Project documentation
│── requirements.txt                     # Dependencies
```

---

## **Data Files and Attributes**

The dataset is provided in **JSON format**, containing three key files:

### **1. portfolio.json** (Offers dataset)
- Contains **10 promotional offers** with attributes:
  - **id**: Unique identifier for each offer  
  - **reward**: Reward amount for completing the offer  
  - **channels**: Communication channels used (email, web, mobile, social)  
  - **difficulty**: Minimum spending required to complete the offer  
  - **duration**: Offer validity in days  
  - **offer_type**: Type of offer (bogo, discount, informational)

### **2. profile.json** (Customer demographic data)
- Contains **customer attributes**:
  - **id**: Unique customer identifier  
  - **age**: Customer's age  
  - **became_member_on**: Date customer joined the Starbucks rewards program  
  - **gender**: Gender (M, F, O, or missing values)  
  - **income**: Annual income in USD  

### **3. transcript.json** (Customer transactions & offer interactions)
- Tracks how customers **interact with offers** over time:
  - **person**: Customer ID  
  - **event**: Type of event (offer received, viewed, completed, or transaction)  
  - **time**: Time in hours since the start of the dataset  
  - **value**: Contains transaction amount, offer ID, or reward amount  

---

## **Data Preprocessing and Feature Engineering**

### **Data Cleaning and Merging**
- **Merged portfolio, profile, and transcript datasets** to create a unified dataset.
- **Handled missing values** (e.g., some users had no recorded income or gender).
- **Filtered out transactions unrelated to offer completion** to focus on promotional interactions.

### **Feature Engineering**
- **Created `tenure`**: Days since the customer joined the rewards program.
- **Extracted offer interaction times**: `offer_received_time` and `offer_viewed_time` for each transaction.
- **Summed `transaction amounts before completion`** to measure spending before an offer was completed.
- **Encoded categorical features**: Applied **one-hot encoding** to offer type, gender, and offer ID.

---

## **Exploratory Data Analysis (EDA)**

### **Key Findings**
1. **Spending and Offer Completion Trends**
   - **Older, high-income customers** complete offers at the highest rates.
   - **Younger, low-income customers** have lower transaction amounts and completion rates.

2. **Offer Type & Communication Channels**
   - **BOGO and discount offers** had the highest completion rates.
   - **Different age and income groups responded better to different communication channels.**

3. **Feature Importance for Offer Completion**
   - **Income, tenure, offer difficulty, reward, and offer type were the most influential factors.**
   - **Personalization** plays a major role in increasing engagement.

---

## **Machine Learning Model**

### **Pipeline for Model Training**
We built a **Random Forest Classifier** using a structured machine learning pipeline:

1. **Feature Selection**: Used engineered and relevant customer attributes.
2. **Data Preprocessing**:
   - **Standard scaling for numerical features.**
   - **One-hot encoding for categorical variables.**
3. **Train-Test Split**: 80% training, 20% testing.
4. **Hyperparameter Tuning**:
   - Used **GridSearchCV** with **4-fold cross-validation** to optimize performance.
   - Tuned parameters:
     ```python
     param_grid = {
         'classifier__n_estimators': [50, 100, 200],
         'classifier__max_depth': [None, 10, 20, 30],
         'classifier__min_samples_split': [2, 5, 10]
     }
     ```
5. **Evaluation Metrics**:
   - **Accuracy: 78%**
   - **Precision, Recall, F1-Score** for completed vs. not completed offers.
   - **Confusion Matrix** to visualize classification performance.
   - **Feature Importance Analysis** to identify key predictors.

---

## **Results and Key Takeaways**

### **Model Performance**
- The **Random Forest Classifier achieved 78% accuracy**.
- **Income, tenure, difficulty, reward, and offer type were the strongest predictors of offer completion.**
- **Confusion Matrix Analysis**:
  - The model correctly predicted **4,694 non-completed offers** and **3,888 completed offers**.
  - Some misclassification occurred, suggesting possible improvements in feature selection.

### **Customer Segmentation Insights**
- **Older, high-income customers complete offers at higher rates** and tend to spend more.
- **Lower-income customers, regardless of age, have lower transaction amounts and completion rates.**
- **Offer completion rates rise with age and income**, suggesting **personalized promotions** can boost engagement.

---

## **Recommendations to Improve Offer Completion**

### **Personalized Offer Structuring**
- Tailor **offer difficulty and reward amounts** to individual spending behavior.
- **High-income, long-tenure customers** respond well to **more complex, high-reward offers**.
- **New or budget-conscious customers** prefer **easier, more frequent rewards**.

### **Refining Communication Strategies**
- **Different customer groups respond better to different communication channels**.
- Target **email and mobile notifications for high-income customers**.
- Engage **younger customers via social media and app-based offers**.

### **Implementing A/B Testing**
- Conduct **experiments to test different offer structures**.
- Measure **conversion rates based on segmentation** (age, income, tenure).

### **Future Model Enhancements**
- Integrate **real-time transaction data and seasonal trends**.
- Develop **segmented machine learning models** for different customer groups.
- Test advanced models like **XGBoost or LightGBM** for better predictions.

---

## **How to Run the Model**

### **Using Jupyter Notebook**
To run the analysis step-by-step, open:
```bash
jupyter notebook Starbucks_Capstone_notebook.ipynb
```

---

## **Final Thoughts**

This project successfully demonstrated how **machine learning can enhance Starbucks' promotional campaigns** by predicting offer completion likelihood. Our findings suggest that **income, tenure, offer type, difficulty, and rewards are crucial factors influencing engagement**. By implementing **personalized offers, optimized communication strategies, and targeted incentives**, Starbucks can improve customer participation and maximize the effectiveness of its rewards program.

Future improvements include **advanced segmentation, real-time data integration, and continuous A/B testing** to further refine promotional strategies.

---

This README provides an overview of the project, guiding users on **data processing, analysis, modeling, and key insights** to optimize offer completion rates in Starbucks' rewards program.
