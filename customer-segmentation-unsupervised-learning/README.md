# Customer Segmentation Using Unsupervised Learning

**Program:** Applied Artificial Intelligence and Data Science  
**Institutional Context:** Great Learning x MIT  
**Project Type:** Capstone / Portfolio Project  
**Domain:** Marketing Analytics, Customer Segmentation, Unsupervised Machine Learning  

## Project Overview

This project applies unsupervised machine learning to a marketing campaign customer dataset to identify meaningful customer segments. The main objective is to group customers based on similarities in demographic profile, household structure, spending behavior, purchase channels, and campaign responsiveness.

Customer segmentation is important because different customer groups may have different needs, purchasing habits, channel preferences, and responses to marketing campaigns. Instead of applying the same marketing strategy to all customers, segmentation allows a business to design more targeted and efficient strategies for different customer groups.

The project uses dimensionality reduction and clustering techniques to understand the customer base and recommend practical marketing actions for each segment.

## Business Objective

The goal of this project is to:

- Understand customer behavior through exploratory data analysis.
- Engineer meaningful customer-level features.
- Apply dimensionality reduction techniques to understand the structure of the data.
- Compare multiple clustering algorithms.
- Select the most practical segmentation model.
- Translate the final customer segments into actionable marketing recommendations.

## Dataset Description

The dataset contains customer-level information related to demographics, household structure, spending behavior, purchase channels, campaign response, and complaint history.

The main feature groups include:

- **Demographics:** year of birth, education, marital status, and income.
- **Household structure:** number of children and teenagers at home.
- **Customer relationship:** enrollment date and recency of last purchase.
- **Product spending:** wines, fruits, meat, fish, sweets, and gold products.
- **Purchase channels:** web, catalog, store, and discount purchases.
- **Marketing response:** acceptance of previous campaigns and the latest campaign.
- **Complaint history:** whether the customer complained in the last two years.

## Methodology

This project follows a complete unsupervised learning workflow using Python and common data science libraries such as `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `scipy`, and `scikit-learn-extra`.

### 1. Data Understanding

The dataset was loaded and inspected to understand its structure, variable types, missing values, and summary statistics.

The initial dataset contained:

- 2,240 customer records
- 27 variables
- Numerical, categorical, and date-based features

The only variable with missing values was `Income`.

### 2. Exploratory Data Analysis

Exploratory data analysis was performed on both numerical and categorical variables.

The analysis included:

- Summary statistics for numerical variables.
- Frequency analysis for categorical variables.
- Distribution analysis of income.
- Outlier detection using the IQR method.
- Analysis of education and marital status categories.
- Relationship analysis between income, spending, purchases, web visits, and campaign response.
- Product spending analysis by education and marital status.
- Purchase channel analysis by customer profile.

Important observations from EDA included:

- Income is right-skewed and contains extreme high-income outliers.
- Higher-income customers generally spend more and purchase more.
- Catalog and store purchases are strongly associated with high-value customers.
- Website visits do not necessarily indicate high customer value.
- Customers with more children tend to spend less.
- Some categorical labels, especially in `Marital_Status`, have very low counts and need to be handled carefully.

### 3. Data Preprocessing and Feature Engineering

Several customer-level features were created to make the dataset more suitable for segmentation.

The engineered features include:

- `Age`: created from year of birth.
- `Total_Children`: total number of kids and teenagers in the household.
- `Family_Size`: estimated number of household members.
- `Total_Spending`: total amount spent across all product categories.
- `Total_Purchases`: total number of purchases across all purchase channels.
- `Customer_Tenure`: number of days the customer has been with the company.
- `Total_Campaign_Accepted`: total number of campaigns accepted by the customer.
- `Amount_Spent_Per_Purchase`: average spending per purchase.

Missing values in `Income` were imputed using median-based imputation because the income distribution was right-skewed and affected by outliers.

Rare categorical labels were also reviewed and grouped where appropriate to reduce noise before modeling.

### 4. Data Preparation for Segmentation

The variables used for segmentation were selected carefully. In customer segmentation, not every variable should be used directly for clustering.

Some variables were treated as **segmentation attributes**, while others were kept as **profiling attributes**.

Segmentation attributes included behavioral and customer-value variables such as:

- Age
- Income
- Total children
- Family size
- Customer tenure
- Total spending
- Total purchases
- Amount spent per purchase
- Campaign acceptance
- Purchase channel behavior
- Web visits
- Recency

Profiling attributes included variables such as:

- Education
- Marital status
- Individual product spending categories
- Individual campaign response variables
- Complaint status

This approach allows the clustering model to form groups based mainly on customer behavior and value, while demographic and campaign variables can be used later to interpret the clusters.

All selected segmentation variables were scaled before applying clustering models.

### 5. Dimensionality Reduction

Two dimensionality reduction techniques were used:

- **t-SNE**
- **PCA**

t-SNE was used for exploratory visualization of customer similarity in two dimensions. The t-SNE plot showed some local groupings, but the customer groups were not perfectly separated.

PCA was used to reduce dimensionality and summarize the main sources of variation in the data. PCA helped reduce correlation among variables and prepared the data for clustering.

The PCA results showed that:

- The first principal component captured the strongest customer value pattern.
- The first 7 principal components explained more than 80% of the total variance.
- The first 9 principal components explained more than 90% of the total variance.

The clustering models were then applied to the PCA-transformed dataset.

### 6. Clustering Models

Several clustering models were tested and compared:

- K-Means
- K-Medoids
- Hierarchical Clustering
- DBSCAN
- Gaussian Mixture Model

Each model was evaluated using a combination of technical metrics and business interpretability.

The evaluation considered:

- Silhouette score
- Inertia
- Cophenetic correlation
- AIC and BIC
- Cluster size balance
- Cluster interpretability
- Business usefulness

## Model Comparison

### K-Means

K-Means was tested with different values of K. The highest silhouette score was achieved at K = 2, but this solution was too broad for marketing segmentation. A 4-cluster solution was selected for profiling because it provided more actionable customer groups.

The K-Means 4-cluster solution produced meaningful customer segments such as premium high-value customers, active multi-channel customers, budget-conscious family customers, and young low-value web browsers.

### K-Medoids

K-Medoids was tested as a more robust alternative to K-Means because it uses actual observations as cluster centers. It produced similar customer patterns to K-Means and was useful for comparison.

However, it did not provide a major improvement over K-Means in terms of interpretability or performance.

### Hierarchical Clustering

Hierarchical clustering was tested using different distance metrics and linkage methods. The best cophenetic correlation was achieved using cosine distance with average linkage.

However, the final hierarchical clustering result produced one extremely small cluster containing only two customers. Because of this imbalance, hierarchical clustering was not selected as the final solution.

### DBSCAN

DBSCAN was tested using different combinations of `eps` and `min_samples`.

Although one parameter combination produced a reasonable silhouette score, the resulting clusters were highly imbalanced. Almost all customers were assigned to one large cluster, while another cluster contained only a few customers.

This suggests that the dataset does not contain clear density-separated clusters. Therefore, DBSCAN was not suitable as the final segmentation model.

### Gaussian Mixture Model

Gaussian Mixture Model was tested using different numbers of components. AIC, BIC, and silhouette score gave different recommendations.

The 4-component GMM solution produced balanced clusters and useful business interpretation, especially around campaign responsiveness. However, its silhouette score was lower than K-Means, and the model is more complex to explain in a business setting.

GMM was useful as a supporting model, but K-Means was more practical as the final segmentation solution.

## Final Model Recommendation

The final recommended model is **K-Means with 4 clusters**.

K-Means was selected because it provides the best overall balance between:

- Practical interpretability
- Balanced customer segments
- Clear business meaning
- Simple implementation
- Marketing actionability
- Better performance than other 4-cluster alternatives

Although K = 2 had a higher silhouette score, it was too broad for marketing use. The 4-cluster K-Means solution provides more useful and actionable customer segments.

## Final Customer Segments

| Cluster | Segment Name | Key Characteristics |
|---|---|---|
| Cluster 0 | Budget-conscious family customers | Larger families, low spending, low campaign response, high web visits, deal-oriented behavior |
| Cluster 1 | Premium high-value customers | Highest income, highest spending, strongest campaign response, strong catalog and store purchases |
| Cluster 2 | Active multi-channel value customers | Frequent buyers, moderate-to-high spending, active across web, store, and catalog channels, relatively deal-sensitive |
| Cluster 3 | Young low-value web browsers | Younger customers, lower income, low spending, high web visits, weak purchase conversion |

## Key Findings

The most important findings from the project are:

- Income is strongly related to total spending and purchase activity.
- Catalog and store purchases are more strongly associated with high-value customers than website visits.
- Website visits do not necessarily indicate high customer value.
- Some customers visit the website frequently but purchase very little.
- Customers with more children tend to have lower spending and lower basket value.
- Premium customers tend to have higher income, fewer children, stronger campaign response, and higher spending across product categories.
- Campaign responsiveness differs across customer groups and should be considered separately from customer value.
- Customer segmentation is most useful when technical clusters can be translated into business actions.

## Marketing Recommendations

### 1. Premium High-Value Customers

These customers should be prioritized for loyalty programs, premium offers, personalized recommendations, and exclusive campaigns.

They have high income, high spending, strong campaign response, and strong catalog/store purchasing behavior. Since they are already valuable, the business should focus on retention, loyalty, and increasing lifetime value.

Recommended actions:

- Personalized premium offers
- VIP loyalty programs
- Exclusive product bundles
- Early access campaigns
- High-value catalog or store-based promotions

### 2. Active Multi-Channel Value Customers

These customers purchase frequently across multiple channels and have moderate-to-high spending.

They are valuable customers, but they may also be more deal-sensitive. The goal should be to increase basket size and improve long-term loyalty.

Recommended actions:

- Cross-channel campaigns
- Bundled offers
- Targeted discounts
- Personalized web and store recommendations
- Campaigns encouraging higher basket value

### 3. Budget-Conscious Family Customers

These customers have larger households, lower spending, and weaker campaign response. They appear to be more budget-conscious and deal-oriented.

The marketing strategy should focus on practical value and affordability.

Recommended actions:

- Family bundles
- Discount campaigns
- Value packs
- Essential product recommendations
- Price-sensitive promotions

### 4. Young Low-Value Web Browsers

These customers are younger, lower-income, and low-spending. They visit the website frequently but do not convert strongly into purchases.

The goal should be to improve conversion from browsing to purchasing.

Recommended actions:

- Entry-level offers
- Retargeting campaigns
- First-purchase incentives
- Website personalization
- Low-cost product recommendations
- Conversion-focused email campaigns

## Project Value

This project demonstrates the full workflow of an unsupervised machine learning segmentation problem, including:

- Data cleaning
- Exploratory data analysis
- Feature engineering
- Dimensionality reduction
- Clustering model comparison
- Cluster profiling
- Business interpretation
- Marketing strategy recommendation

The project is not only a technical clustering exercise. It also shows how machine learning can be translated into practical marketing decisions.

## Notes for Viewers

The final segmentation model should not be treated as permanent. In real business applications, customer behavior changes over time. Therefore, the segmentation model should be monitored and updated regularly as new customer data becomes available.

The final recommendation is based on both quantitative metrics and business interpretability. This is important because the best statistical model is not always the most useful model for business decision-making.
