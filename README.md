Here's your updated README with explanations on why precision, accuracy, F1-score, and recall were chosen as evaluation metrics.  

---

# Starbucks Capstone Project  

## Blog Post  

Check out my detailed blog post about this project on Medium: [Udacity Starbucks Project](https://medium.com/@tshepisomokoena20/udacity-starbucks-project-7f955aabf1d6)  

## Project Overview  

This project analyzes customer interactions with Starbucks' personalized rewards program and builds a predictive model to determine offer completions. The goal is to identify key factors that drive engagement, optimize promotional strategies, and enhance the effectiveness of Starbucks' targeted marketing efforts.  

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
- Identified key drivers of offer completion, such as age, income, tenure, and offer type.  
- Examined communication channels to understand their impact on offer engagement.  

### 2. **Feature Engineering**  

- Created **tenure** (days since joining the program) from `became_member_on`.  
- One-hot encoded categorical variables (`gender`, `offer_type`, `offer_id`).  
- Removed features that could cause data leakage, such as time-related columns.  

### 3. **Data Preprocessing and Modeling**  

- **StandardScaler** was used to normalize numerical features.  
- Built a **RandomForestClassifier** using a machine learning pipeline.  
- Hyperparameter tuning was done using **GridSearchCV** with 4-fold cross-validation.  
- The model was evaluated using **classification metrics** such as accuracy, precision, recall, and F1-score.  

### 4. **Model Evaluation and Insights**  

- The best-performing model achieved an accuracy of **78%**.  
- **Key influencing factors:** **income, tenure, difficulty, reward amount, and offer type**.  
- Older, higher-income customers completed more offers compared to younger, lower-income groups.  
- Different communication channels were more effective for different customer segments.  

## **Evaluation Metrics and Why They Were Chosen**  

- **Accuracy**: Measures the proportion of correctly classified instances. Useful when the dataset is balanced.  
- **Precision**: Indicates how many of the offers predicted as "completed" were actually completed. Important to avoid false positives when making marketing decisions.  
- **Recall**: Measures how many actual completed offers were correctly identified. Critical for ensuring that Starbucks does not miss potential completions.  
- **F1-score**: Balances precision and recall, making it a better metric when there is a tradeoff between the two.  

Given the business context, recall is especially important, as failing to identify customers who are likely to complete offers could result in lost engagement opportunities. However, precision is also necessary to avoid misallocating marketing resources to customers unlikely to complete offers.  

## Recommendations  

### **Increasing Offer Completions**  

- **Personalized Offers**: Since income, tenure, and reward amount strongly influence offer completion, Starbucks should **personalize offers based on spending habits**. High-income, long-tenure customers may respond better to high-difficulty offers, while newer or lower-income customers may need simpler, more attractive rewards.  
- **Optimized Communication Strategies**: Different customer groups prefer different communication channels (e.g., email, mobile, social media). Starbucks should **target offers through the most effective channels** for each segment.  
- **Reminder and Incentive Programs**: Customers who engage but do not complete offers should receive **reminders or limited-time follow-ups** to encourage conversion.  

### **Future Improvements and Testing**  

- **A/B Testing**: Experiment with different offer structures, communication strategies, and incentives to validate model predictions and optimize engagement.  
- **Additional Features**: Include real-time behavioral data, seasonal trends, and preferred product categories to improve predictions.  
- **Segmented Models**: Instead of a single model, create specialized models for **new vs. returning customers** and **low vs. high spenders** for better targeting.  
- **Advanced ML Models**: While Random Forest performed well, testing **XGBoost, LightGBM, or deep learning** could improve predictive accuracy.  

## Conclusion  

This project successfully built a predictive model to determine offer completions and provided actionable insights for Starbucks to optimize its rewards program. With targeted marketing strategies, optimized promotions, and continuous testing, Starbucks can **increase offer completions and customer engagement**. Future improvements such as **A/B testing, advanced segmentation, and incorporating additional customer insights** will enhance the model’s effectiveness and drive long-term customer loyalty.
