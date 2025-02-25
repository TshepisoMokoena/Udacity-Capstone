# Starbucks Capstone Project

## Blog Post

Check out my detailed blog post about this project on Medium: [Udacity Starbucks Project](https://medium.com/@tshepisomokoena20/udacity-starbucks-project-7f955aabf1d6)

## Project Overview

This project aims to analyze customer interactions with Starbucks' personalized rewards program and predict offer completions. The goal is to identify key factors that drive customer engagement and optimize promotional strategies.

## Installation

To run the project locally, install the following dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

Ensure you have Jupyter Notebook installed to run the provided notebook file.

## File Structure

```
├── README.md                        # Project documentation
├── Starbucks_Capstone_notebook.ipynb # Main notebook with analysis and modeling
├── portfolio.json                    # Contains information about offers and their attributes
├── profile.json                      # Contains customer demographic and membership details
├── transcript.zip                     # Contains customer interaction data (events, transactions, etc.)
```

## Dataset Details

### **portfolio.json**

- `id`: Unique identifier for each offer
- `reward`: Reward amount for completing the offer
- `channels`: List of channels where the offer was sent (email, web, mobile, social)
- `difficulty`: Amount the customer needs to spend to qualify for the offer
- `duration`: Validity period of the offer in days
- `offer_type`: Type of offer (BOGO, discount, informational)

### **profile.json**

- `id`: Unique customer ID
- `age`: Customer's age
- `gender`: Gender (M, F, O)
- `income`: Annual income of the customer
- `became_member_on`: Date when the customer joined the rewards program

### **transcript.zip**

- `person_id`: Unique customer ID
- `event`: Type of event (offer received, offer viewed, offer completed, transaction)
- `time`: Time elapsed since the start of data collection
- `offer_id`: Corresponding offer ID (if applicable)
- `amount`: Transaction amount (if applicable)

## Steps to Build the Model

### 1. **Exploratory Data Analysis (EDA)**

- Analyzed customer demographics, spending behavior, and offer completion trends.
- Identified factors influencing offer completion rates, such as age, income, and offer type.

### 2. **Feature Engineering**

- Created tenure (days since joining the program) based on `became_member_on`.
- One-hot encoded categorical features (gender, offer type, offer ID).

### 3. **Data Preprocessing and Modeling**

- Used `StandardScaler` to normalize numerical features.
- Built a `RandomForestClassifier` within a pipeline.
- Tuned hyperparameters using `GridSearchCV` with 4-fold cross-validation.
- Evaluated the model using classification metrics (accuracy, precision, recall, F1-score, and AUC-ROC).

### 4. **Model Evaluation and Insights**

- The best model achieved an accuracy of **78%**.
- Key influencing factors: **income, tenure, difficulty, reward amount, and offer type**.
- Older and wealthier customers had higher offer completion rates.
- Different customer segments responded better to different communication channels.

## Recommendations

### **Increasing Offer Completions**

- Personalize offers based on income and tenure to improve engagement.
- Target younger, lower-income customers with more attractive promotions.
- Optimize communication channels to align with customer preferences.
- Implement reminder notifications for incomplete offers.

### **Future Improvements and Testing**

- Conduct A/B testing on different offer structures and communication strategies.
- Incorporate real-time behavioral data for better predictive performance.
- Build segmented models for different customer groups to improve targeting.
- Explore advanced ML models like XGBoost and deep learning for better accuracy.

## Conclusion

This project successfully built a predictive model to determine offer completions and provided actionable insights for Starbucks to improve its rewards program. With targeted marketing strategies, optimized promotions, and continuous testing, Starbucks can drive higher customer engagement and increase offer completions.

