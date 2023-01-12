# Sales Insights
Author: Shenyue Jia | [jiashenyue.info](https://jiashenyue.info)
## Business Problem:
- We have a dataset showing item sales and a number of related metrics of the outlets where the items are sold. 
- We want to use these metrics to investigate which factors are the most important determinants of item sales. 
- Eventually, we want to construct a model to estimate the item sales based on the metrics available from our dataset.
## Data:
The salary data for data scientist is collected and prepared by [Analytics Vidhya](https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/).

### Data Dictionary:
Variable Name  | Description
-------------------|------------------
Item_Identifier	| Unique product ID
Item_Weight	| Weight of product
Item_Fat_Content	| Whether the product is low fat or regular
Item_Visibility	| The percentage of total display area of all products in a store allocated to the particular product
Item_Type	| The category to which the product belongs
Item_MRP	| Maximum Retail Price (list price) of the product
Outlet_Identifier	| Unique store ID
Outlet_Establishment_Year	| The year in which store was established
Outlet_Size	| The size of the store in terms of ground area covered
Outlet_Location_Type	| The type of area in which the store is located
Outlet_Type	| Whether the outlet is a grocery store or some sort of supermarket
Item_Outlet_Sales	| Sales of the product in the particular store. This is the target variable to be predicted.


## Methods
- We conducted exploratory analysis of dataset. Results can be reviewed from [this notebook](https://github.com/jiashenyue/salary-insights/blob/main/Data_Science_Sales_Insights_EDA.ipynb)
- We then compared the performance of two machine learning models: **linear regression** and **regression trees**. Results can be found from [this link](https://github.com/jiashenyue/salary-insights/blob/main/machine_learning_sales.ipynb).

## Exploratory Data Analysis

### 1. Does outlet location type affect the item sales amount?

**Hypothesis: Outlets in cities with a higher tier (i.e. Tier 1) will have a higher item sales amount due to the larger population (thus demand) and greater variety in the products for sale.**

*Test hypothesis*

![plot](https://github.com/jiashenyue/salary-insights/blob/main/hist_outlet_type.png)

- The histogram of item sales may reject this hypothesis as there is no significant difference in the **median** of item sales across the three tiers of outlet location types.

- In this comparison, Tier 3 outlets have a similar item sales pattern in terms of **median** and **distribution** with Tier 1 outlets, but a lot more low item sales amount than Tier 2 outlets. This partially agree with the hypothesis as **low** item sales amount is more common in **Tier 3** outlets than **Tier 1** outlets.

### 2. Does outlet size affect the median item sales amount?

**Hypothesis: Outlets with a bigger size (i.e. Large) will have a median higher item sales amount due to the larger number of customers (thus demand) and greater variety of items available for sale, both may skew the median item sales to a higher level.**

*Test hypothesis*

![plot](https://github.com/jiashenyue/salary-insights/blob/main/hist_outlet_size.png)

- The figure above indicated that regardless of outlet size, the medium of item sales is similar. Small outlets have more items with a low sales price.
- The high outlets have a lot less number of item because of the total number of high outlets is much smaller in our data.
- These findings reject our hypotehsis, indicating the outlet size does not significantly affect the median level of item sales amount, while it will define the **Total Amount** of item sales at an outlet.

### 3. Does item visibility affect the item sales amount?
![plot](https://github.com/jiashenyue/salary-insights/blob/main/scatter_outlet_type.png)

**Hypothesis: Item visibility positively contributes to the item sales amount for the two reasons below:**

- To boost the profits, outlets tend to place the high price items at a highly visible place in the shelf, especially comparing with items of the same type with a lower price.
- Even for items with a relatively low sales price, a higher shelf visibility usually means a greater likelihood of purchase, which again contributes to the positive correlation between **item visibility** and **item sales**.

*Test Hypothesis*

- The scatterplot indicates that the item visibility and item sales do not have any correlation if we do not distinguish between item types, which rejects the hypothesis between the positive correlation between item visibility and item outlet sales.

**4. So, which variables are good candidates to predict the item sales in our dataset?**

*Calculate correlation betwen item sales and all numeric variables*

![plot](https://github.com/jiashenyue/salary-insights/blob/main/corr.png)

- The heatmap showed that **item MSRP** has the best correlation with item sales, indicating that the **item price for sale** is a more important factor to determine the **item sales** at outlets included in our dataset.

## Modeling Results

### 1. Predicting item sales with a regression tree model

- Based on our Exploratory Data Analysis, we can build a regression tree model with all numeric variables in our dataset to estimate the Item_Outlet_Sales
- After fine-tuning our regression tree model, we find that using the **model_depth = 5** will yield a good prediction of item sales 

![plot](https://github.com/jiashenyue/salary-insights/blob/main/regression_tree.png)

- Here is the model performance curve while fine-tuning the regression tree model
- The model performance over testing data reached the peak at the **model_depth = 5**

### 2. Model comparison

- Comparing the regression tree model with a linear regression model, we find that the regression tree model performs much better than linear regression model over testing data.
- This is our recommended model to estimate the item sales.

**Training data**
**Model** | **R^2** | **MAE** | **MSE** | **RMSE** 
--- | --- | --- | --- | ---
Linear Regression | 0.67 | 738.48 | 975000.00 | 987.42
Regression Tree | 0.605 | 760.52 | 1168291.21 | 1080.88

**Testing data**
**Model** | **R^2** | **MAE** | **MSE** | **RMSE** 
--- | --- | --- | --- | ---
Linear Regression | -1.38e+20 | 2.54e+12 | 3.86e+26 | 1.97e+13
Regression Tree | 0.60 | 743.16 | 1130629.33 | 1063.31
