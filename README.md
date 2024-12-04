# **AB Testing Dataset: Synthetic Data for Analysis**  

## **Overview**  
The **AB Testing Dataset** is a self-generated synthetic dataset designed using **Random Sampling techniques** provided by the Numpy library. This dataset mimics user behavior on an **imaginary retail website** across the United Kingdom. It enables data practitioners to explore and practice **A/B Testing**, a fundamental technique for analyzing the impact of changes in user behavior.  

The dataset represents a scenario where a retail company wants to determine the effect of changing the website's **background color** on **user engagement**.  

### **Scenario**  
- **Group A (Control Group)**: Users experience the default website background color **White**.  
- **Group B (Treatment Group)**: Users experience the new website background color **Black**.  

The main **objective** is to test whether there is a **statistically significant improvement** in metrics like **time spent on the website** or **conversion rates** (desired user actions) when the background color is changed to Black.  

---

## **Dataset Features**  

| Column Name   | Description                                                                                  |  
|---------------|----------------------------------------------------------------------------------------------|  
| **User ID**   | A unique identifier for each user.                                                          |  
| **Group**     | Indicates whether the user belongs to the **Control (A)** or **Treatment (B)** group.       |  
| **Page Views**| The number of pages the user viewed during their session.                                   |  
| **Time Spent**| The total time (in seconds) spent by the user on the site during the session.               |  
| **Conversion**| Indicates whether the user completed a desired action (Yes/No).                            |  
| **Device**    | The type of device used to access the website (**Desktop** or **Mobile**).                  |  
| **Location**  | The user's location within the United Kingdom (**England, Scotland, Wales, Northern Ireland**). |  

---

## **Applications**  
1. **A/B Testing**: Analyze the difference in metrics like **conversion rates** and **time spent** across the two groups.  
2. **Data Visualization**: Use segmentation (e.g., by device or location) to derive actionable insights.  
3. **Machine Learning**: Build classification models to predict user behavior (e.g., **Conversion** as a target variable).  
4. **Mathematical Modeling**: Validate results using statistical metrics like **p-values** and **confidence intervals**.  

---

## **Mathematical Formulation**  
The dataset enables A/B Testing using the following key metrics:  

### 1. **Conversion Rate (CR)**  
\[
CR = \frac{\text{Number of Conversions}}{\text{Total Users in Group}}
\]  
Analyze whether the conversion rate is significantly higher in **Group B** (Black background).  

### 2. **Lift**  
\[
\text{Lift} = \frac{CR_B - CR_A}{CR_A}
\]  
Quantify the percentage increase in conversions for Group B compared to Group A.  

### 3. **t-Test (Statistical Significance)**  
\[
t = \frac{\bar{X}_A - \bar{X}_B}{\sqrt{\frac{s_A^2}{n_A} + \frac{s_B^2}{n_B}}}
\]  
Where:  
- \(\bar{X}_A, \bar{X}_B\): Mean values for groups A and B.  
- \(s_A^2, s_B^2\): Variances for groups A and B.  
- \(n_A, n_B\): Sample sizes for groups A and B.  

---

## **Code Implementation Examples**  

### **1. Load the Dataset**  
```python
import pandas as pd

# Load the dataset
df = pd.read_csv('ab_testing_dataset.csv')

# Display dataset overview
print(df.head())
```

### **2. Visualize Group Performance**  
```python
import seaborn as sns
import matplotlib.pyplot as plt

# Boxplot of Time Spent by Group
sns.boxplot(x='Group', y='Time Spent', data=df, palette='coolwarm')
plt.title('Time Spent by Group')
plt.show()
```

### **3. Calculate Conversion Rate**  
```python
# Conversion rates for each group
conversion_rate = df.groupby('Group')['Conversion'].apply(lambda x: (x == 'Yes').mean())
print(conversion_rate)
```

### **4. Statistical Testing**  
```python
from scipy.stats import ttest_ind

# Time spent in each group
group_a = df[df['Group'] == 'A']['Time Spent']
group_b = df[df['Group'] == 'B']['Time Spent']

# t-test
t_stat, p_val = ttest_ind(group_a, group_b)
print(f"t-statistic: {t_stat}, p-value: {p_val}")
```

---

## **Roles for Analysis**  
1. **Data Analyst**:  
   - Conduct statistical tests and visualizations to determine significant differences between groups.  
2. **Data Scientist**:  
   - Build predictive models to forecast conversion probabilities.  
3. **Business Analyst**:  
   - Derive actionable insights for decision-making based on data trends.  

---

## **Conclusion**  
This dataset is a versatile tool for practicing **A/B Testing**, **data visualization**, and **statistical analysis**. It provides a structured environment to apply theoretical concepts in a practical context, enabling you to develop expertise in decision-making through data.

---

### **License**  
This dataset is synthetic and free to use for educational and research purposes.
