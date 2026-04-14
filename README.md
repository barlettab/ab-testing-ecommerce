# A/B Testing for E-commerce Recommendation

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-orange)
![Plotly](https://img.shields.io/badge/Plotly-Visualization-purple)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Statistical%20Testing-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## Project Overview
This project analyses the impact of a **product recommendation system** on an e-commerce platform using **A/B Testing (Split Testing)** and statistical hypothesis testing. 

Two versions of the website were tested:
- **Control Group**: Original website without recommendation system.
- **Treatment Group**: New version of the website with the recommendation system.

The goal of the analysis is to evaluate whether the recommendation system improves the **conversion rate**, measured as the proportion of users who complete a purchase.

This project was developed as part of the **7DaysOfCode Data Science challenge by Alura**, focusing on real-world experimentation and hypothesis testing.

---

## Notebook

The full analysis can be accessed in two ways:

• Kaggle Notebook (interactive version):  
https://www.kaggle.com/code/barlettab/a-b-testing-e-commerce

• Repository version:  
`notebook/ab_testing_analysis.ipynb`

---

## Dataset

The dataset used in this analysis comes from Kaggle: 

https://www.kaggle.com/datasets/zhangluyuan/ab-testing

It simulates the results of an A/B testing experiment for an e-commerce platform. The dataset contains **294,478 observations** and the following columns:

| Column | Description |
|------|-------------|
| user_id | Unique identifier for each user |
| timestamp | Time when the user visited the website |
| group | Experiment group (control or treatment) |
| landing_page | Version of the page shown to the user |
| converted | Indicates whether the user made a purchase (1) or not (0) |

Although the dataset is already structured for experimentation analysis, some preprocessing steps were required, such as removing inconsistencies between experiment groups and landing pages and eliminating duplicated users.

## Data Quality Issues

During the analysis, some inconsistencies were identified in the dataset:

- Some users assigned to the **control group** were shown the **new page**
- Some users assigned to the **treatment group** were shown the **old page**
- Duplicate user IDs were present

These issues were handled during the preprocessing stage to ensure the integrity of the A/B testing analysis.

## Data Cleaning

To ensure the integrity of the experiment, several preprocessing steps were applied:

- Convert the `timestamp` column to datetime format
- Remove inconsistencies between experiment groups and landing pages (Data Quality Issues)
- Remove duplicated users
- Reset the dataframe index
- Generate a **sample of 5,000 users** for exploratory analysis

## Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed to better understand the experiment structure and user behavior before applying statistical tests.

Several visualizations were created to explore the dataset and validate assumptions of the A/B test.

### • User Distribution Between Groups

One important aspect of A/B testing is ensuring that traffic is **evenly distributed** between the control and treatment groups. This helps guarantee that both groups are comparable and that the results are not biased by uneven sampling.

A visualization of user distribution confirmed that the experiment groups contain a similar number of users.

### • Conversion Rate Comparison

The conversion rate represents the **percentage of users who completed a purchase**. By comparing the conversion rates of the control and treatment groups, it is possible to observe whether the new recommendation system leads to higher user engagement and purchasing behavior.

### • Conversion Over Time

Analyzing conversions over time helps verify whether the experiment remained stable throughout the testing period and whether external factors may have influenced the results.

Time-based visualizations allow the identification of trends, fluctuations, or anomalies during the experiment.

## Hypothesis Testing

To statistically evaluate the impact of the recommendation system, a **hypothesis test for proportions** was applied. 

The objective is to determine whether the **conversion rate of the treatment group is significantly higher than the control group**.

### Hypotheses

- **Null Hypothesis (H₀):** The recommendation system does not increase the conversion rate.

$$
H_0: p_{treatment} = p_{control}
$$

- **Alternative Hypothesis (H₁):** The recommendation system increases the conversion rate.

$$
H_1: p_{treatment} > p_{control}
$$

Since the objective is to verify whether the recommendation system improves the conversion rate, a **one-tailed Z-test for proportions** was applied. This statistical test compares the conversion rates of the control and treatment groups to determine whether the observed difference is statistically significant.

## Results

Three hypothesis tests were performed:

1. One-tailed test using a **sample of 5,000 users**
2. Two-tailed test using the **same sample**
3. One-tailed test using the **full cleaned dataset**

### One-Tailed Test (5,000 Sample)

Results obtained from the sample:

- **Z-statistic:** 0.4566  
- **P-value:** 0.3246  

Since the p-value is greater than the significance level (α = 0.05), there is **not enough statistical evidence to reject the null hypothesis**.

This means that, based on the sample, there is no significant evidence that the recommendation system increases the conversion rate.

---

### Two-Tailed Test (5,000 Sample)

A two-tailed test was also performed to evaluate whether the conversion rate of the treatment group is **different** from the control group, regardless of direction.

Results obtained:

- **Z-statistic:** 0.4547  
- **P-value:** 0.6494  

Since the p-value is much greater than 0.05, we again **fail to reject the null hypothesis**.

This result suggests that there is **no statistically significant difference** between the two versions of the website.

---

### Full Dataset Analysis

The hypothesis test was also performed using the entire cleaned dataset.

Results obtained:

- **Z-statistic:** 1.2942  
- **P-value:** 0.0978  

Although the treatment group shows a slightly higher conversion rate, the p-value remains above the significance level (0.05). Therefore, we **fail to reject the null hypothesis**.

This indicates that the observed difference in conversion rates may be due to **random variation rather than a real impact of the recommendation system**.

## Conclusion

The hypothesis test results indicate that we fail to reject the null hypothesis at the chosen significance level (α = 0.05). Therefore, there is no statistically significant evidence that the recommendation system increases the conversion rate.

Although the treatment group achieved a slightly higher conversion rate, the difference between the groups is small and could plausibly be attributed to random variation.

These findings suggest that the recommendation system did not produce a measurable improvement in user conversion during the experiment period.

## Technologies Used
* Python
* Pandas
* Numpy
* Plotly
* Statsmodels

## Project Structure
ab-testing-ecommerce
│
├── notebook
│   └── ab_testing_analysis.ipynb
│
├── data
│   └── ab_data.csv
│
├── README.md
└── requirements.txt

## References
### Dataset
- Kaggle — A/B Testing Dataset  
  https://www.kaggle.com/datasets/zhangluyuan/ab-testing

### Learning Resources
- Alura — 7 Days of Code  
  https://7daysofcode.io/#dados

- Khan Academy — Hypothesis Testing and P-values  
  https://pt.khanacademy.org/math/statistics-probability/significance-tests-one-sample/more-significance-testing-videos/v/hypothesis-testing-and-p-values

- Wikipedia — Two-tailed Test  
  https://pt.wikipedia.org/wiki/Teste_bicaudal

- Alura Study Material — Hypothesis Testing (PDF)
  https://drive.google.com/file/d/13Y7kWoYAe7Qsbbwfx2_m86bXRumoSdwQ/view
  
## Acknowledgements

This project was developed as part of the **7DaysOfCode Data Science challenge** organized by Alura.

The challenge proposes seven days of practical data science tasks, focusing on real-world experimentation, data analysis, and hypothesis testing.

## Author
Barbara Barletta
Data Science Portfolio Project.
