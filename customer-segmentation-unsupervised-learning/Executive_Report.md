# Executive Report: Customer Segmentation Using Unsupervised Learning

**Program:** Applied Artificial Intelligence and Data Science  
**Institutional Context:** Great Learning x MIT  
**Project Type:** Capstone / Portfolio Project  
**Domain:** Marketing Analytics, Customer Segmentation, Unsupervised Machine Learning  

---

## 1. Executive Summary

### Most Important Findings from the Analysis

This project focused on identifying meaningful customer segments from a marketing campaign dataset using unsupervised learning. The dataset included customer demographics, household structure, income, product spending, purchase channels, campaign response history, and complaint information.

The most important findings from the analysis are:

- **Customer value is strongly associated with income, total spending, total purchases, catalog purchases, and store purchases.** Higher-income customers generally spend more and purchase more frequently.
- **Website visits do not necessarily indicate high customer value.** Several customers visit the website frequently but have low total spending and weak purchase conversion.
- **Catalog and store purchases are stronger indicators of high customer value** compared with website visits alone.
- **Customers with more children tend to spend less**, suggesting that larger households may be more budget-conscious.
- **Campaign responsiveness differs across customer groups.** Some customers are high-value and highly responsive, while others purchase frequently but do not respond strongly to campaigns.
- **K-Means with 4 clusters** provided the most practical final segmentation solution because it produced interpretable, balanced, and actionable customer segments.

Several clustering models were tested, including K-Means, K-Medoids, Hierarchical Clustering, DBSCAN, and Gaussian Mixture Model. The final model was selected based not only on statistical metrics, but also on cluster balance, interpretability, and business usefulness.

### Final Proposed Model Specifications

The final proposed model is **K-Means Clustering with 4 clusters**.

| Item | Specification |
|---|---|
| Final model | K-Means Clustering |
| Number of clusters | 4 |
| Input data | PCA-transformed customer segmentation dataset |
| Preprocessing | Missing value imputation, feature engineering, outlier review, scaling |
| Dimensionality reduction | PCA |
| Main evaluation criteria | Silhouette score, cluster balance, interpretability, business actionability |
| Final business use case | Customer segmentation for targeted marketing strategy |

The final customer segments are:

| Cluster | Segment Name | Summary |
|---|---|---|
| Cluster 0 | Budget-conscious family customers | Larger families, low spending, low campaign response, high web visits, deal-oriented behavior |
| Cluster 1 | Premium high-value customers | Highest income, highest spending, strongest campaign response, strong catalog and store purchases |
| Cluster 2 | Active multi-channel value customers | Frequent buyers, moderate-to-high spending, active across web, store, and catalog channels, relatively deal-sensitive |
| Cluster 3 | Young low-value web browsers | Younger customers, lower income, low spending, high web visits, weak purchase conversion |

### Key Next Steps

The recommended next steps are:

- Deploy the K-Means 4-cluster segmentation as an initial customer segmentation framework.
- Add segment labels to the customer database or CRM system.
- Build dashboards to monitor customer behavior and performance by segment.
- Design targeted campaigns for each customer segment.
- Track business KPIs such as campaign response rate, conversion rate, average order value, retention, and revenue per segment.
- Run A/B tests to compare segment-based campaigns against generic campaigns.
- Refresh the segmentation periodically as new customer data becomes available.

---

## 2. Problem and Solution Summary

### Summary of the Problem

The business problem is that customers do not all behave in the same way. They differ in income, household structure, purchasing habits, product preferences, purchase channels, and responsiveness to marketing campaigns.

If a company applies the same marketing strategy to all customers, marketing resources may be used inefficiently. Some customers may respond better to premium offers, some may prefer discounts, and some may browse frequently without converting into purchases.

The goal of this project was to use customer data to discover meaningful groups of similar customers. Since there was no predefined customer segment label, this was treated as an **unsupervised learning problem**.

The problem can be formulated as:

> Given customer demographic, behavioral, purchase, and campaign response data, group customers into segments such that customers within the same segment are similar, while customers in different segments are meaningfully different.

### Reason for the Proposed Solution Design

The proposed solution uses **K-Means clustering with 4 clusters** after data preprocessing, feature engineering, scaling, and PCA transformation.

This solution design is appropriate because:

- The business problem requires discovering hidden customer groups without a target variable.
- K-Means is simple, scalable, and easy to interpret.
- The 4-cluster solution creates more actionable marketing segments than a broad 2-cluster solution.
- The resulting clusters are reasonably balanced and meaningful from a business perspective.
- The final segments can be directly translated into marketing strategies.

Other clustering models were tested but were not selected as the final solution:

- **K-Medoids** produced similar insights but did not significantly improve over K-Means.
- **Hierarchical Clustering** produced one extremely small cluster with only 2 customers, making it less practical.
- **DBSCAN** produced highly imbalanced clusters, with almost all customers assigned to one large cluster.
- **Gaussian Mixture Model** produced balanced clusters and useful insights, but it had lower silhouette performance at 4 components and was less straightforward to explain as the primary business model.

Therefore, K-Means with 4 clusters was selected because it provided the best balance between performance, interpretability, and business actionability.

### How the Solution Solves the Problem

The K-Means segmentation model helps the business move away from one-size-fits-all marketing. Instead of treating all customers the same, the company can design targeted strategies for each customer segment.

For example:

- **Premium high-value customers** can receive loyalty programs, premium offers, and exclusive campaigns.
- **Active multi-channel value customers** can receive cross-channel campaigns, product bundles, and targeted promotions.
- **Budget-conscious family customers** can receive family bundles, value packs, and discount-based campaigns.
- **Young low-value web browsers** can receive retargeting campaigns, entry-level offers, and conversion-focused website promotions.

This solution is valid because the segments are based on actual observed customer behavior, including income, total spending, purchase channels, household structure, and campaign responsiveness. The model does not only create statistical groups; it creates business-interpretable customer segments that can guide marketing action.

### Production Readiness and Interpretability

The model is suitable as a **first production-ready segmentation framework** for marketing analysis, campaign planning, and customer profiling.

It is interpretable because each cluster can be described using original customer variables such as:

- income,
- total spending,
- total purchases,
- purchase channels,
- family size,
- campaign response,
- website visits.

However, because this is an unsupervised learning model, it should not be deployed as a fully automated decision system without monitoring. There is no true target label, so the model should be evaluated through business KPIs after implementation.

Important KPIs to monitor include:

- campaign response rate,
- conversion rate,
- average order value,
- revenue per segment,
- retention rate,
- customer lifetime value,
- repeat purchase rate.

The model should be refreshed periodically as new customer behavior data becomes available.

---

## 3. Recommendations for Implementation

### Key Recommendations to Implement the Solution

The company should implement the K-Means 4-cluster segmentation as an initial customer segmentation framework.

Recommended implementation steps:

1. **Assign customer segment labels**
   - Apply the trained K-Means model to assign each customer to one of the four segments.
   - Store the segment label in the customer database or CRM system.

2. **Build segment-level dashboards**
   - Track income, spending, purchase channels, campaign response, and product preferences by segment.
   - Monitor segment behavior over time.

3. **Design segment-specific campaigns**
   - Create different campaigns for different customer groups.
   - Avoid using the same message, discount, or offer for all customers.

4. **Run A/B testing**
   - Compare targeted segment-based campaigns with generic campaigns.
   - Measure uplift in conversion rate, campaign response, average order value, and revenue.

5. **Refresh the model periodically**
   - Re-run segmentation every 3 to 6 months, or whenever major new customer data becomes available.
   - Check whether cluster profiles remain stable over time.

### Key Actionables for Stakeholders

| Stakeholder | Key Actionables |
|---|---|
| Marketing Team | Design segment-specific campaigns, offers, and messaging |
| CRM Team | Add customer segment labels to CRM records |
| Data Team | Maintain the segmentation pipeline and refresh the model |
| Management | Use segment insights to allocate marketing budget |
| Sales / Channel Teams | Prioritize high-value customers and optimize channel strategy |
| Product Team | Use segment preferences to design product bundles and recommendations |

---

## 4. Benefits, Costs, Risks, and Further Analysis

### Benefits of the Solution

The expected benefits of the segmentation solution include:

- More targeted marketing campaigns.
- Improved marketing resource allocation.
- Higher campaign response rate.
- Better customer retention for high-value customers.
- Improved conversion among frequent website visitors.
- Better understanding of customer value and behavior.
- More personalized product recommendations.
- Clearer prioritization of high-value customer groups.

A rational assumption can be made that even a small improvement in campaign performance may create business value. For example, if segment-based targeting improves campaign conversion by **5% to 10%** among high-value or active customer groups, the incremental revenue may be meaningful because those customers already have higher spending and stronger purchase activity.

For the premium high-value segment, even a small improvement in retention or average order value can have a larger revenue impact than applying the same campaign equally to all customers.

### Potential Costs

The main costs of implementation include:

- Data engineering effort to prepare customer-level features regularly.
- CRM integration effort to store and use segment labels.
- Marketing cost to design different campaigns for different segments.
- Time required to build dashboards and reporting tools.
- Ongoing monitoring and model refresh cost.

However, the technical implementation cost is relatively manageable because K-Means is simple, fast, and easy to update.

### Key Risks and Challenges

The main risks and challenges are:

- **Cluster stability risk:** Customer behavior changes over time, so the segmentation may become outdated.
- **Data quality risk:** Missing values, outliers, and inconsistent data can affect the segmentation.
- **Business adoption risk:** Marketing teams must understand and use the segments correctly.
- **Overgeneralization risk:** Customers in the same segment are similar, but not identical.
- **Campaign execution risk:** Poor campaign design may reduce the value of the segmentation.
- **Privacy and compliance risk:** Customer data must be handled responsibly, especially when used for personalized marketing.
- **Monitoring risk:** If KPIs are not tracked, the business cannot know whether segmentation improves results.

### Further Analysis Needed

Further analysis can improve the solution before or after deployment.

Recommended future analyses include:

- Validate segments using future campaign performance.
- Run A/B testing for segment-based campaigns.
- Analyze customer lifetime value by segment.
- Study product preference ratios within each segment.
- Test whether customers move between segments over time.
- Compare clustering results using different PCA thresholds, such as 7 components versus 9 components.
- Test alternative scaling methods such as RobustScaler.
- Explore more refined outlier treatment for income and spending variables.
- Add more recent transaction data if available.
- Build a dashboard to monitor segment-level KPIs.

Potential associated problems to solve include:

- Predicting campaign response within each segment.
- Recommending products by customer segment.
- Identifying customers likely to move from low-value to high-value segments.
- Designing retention strategies for premium customers.
- Improving conversion among high web-visit but low-spending customers.

---

## 5. Final Recommendation

The company should adopt **K-Means with 4 clusters** as the final customer segmentation model.

This model is recommended because it is:

- interpretable,
- actionable,
- reasonably balanced,
- simple to implement,
- easy to communicate to business stakeholders,
- practical for marketing strategy design.

The final segmentation provides a clear framework for differentiated marketing strategy:

| Segment | Recommended Strategy |
|---|---|
| Budget-conscious family customers | Use family bundles, value packs, and discount-based campaigns |
| Premium high-value customers | Prioritize loyalty programs, premium offers, and personalized campaigns |
| Active multi-channel value customers | Use cross-channel promotions, product bundles, and targeted offers |
| Young low-value web browsers | Focus on website conversion, retargeting, and entry-level offers |

Overall, K-Means with 4 clusters offers a practical and interpretable customer segmentation framework that can support more targeted marketing, better resource allocation, and improved campaign effectiveness.

The segmentation should be deployed as an initial framework and improved over time using new customer data, campaign results, and business KPI monitoring.