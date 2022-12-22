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

## Results

**Histogram of item sales by outlet type**
![plot](https://github.com/jiashenyue/salary-insights/blob/main/hist_outlet_type.png)

- The histogram of item sales amount by outlet location type indicated the similar pattern: the median of item sales is similar across outlet location types.

- In this comparison, Tier 3 outlets have a similar item sales pattern with Tier 1 outlets, but a lot more low item sales amount than Tier 2 outlets. This is different from the comparison between high, medium, and low outlet size.

**Histogram of item sales by outlet size**
![plot](https://github.com/jiashenyue/salary-insights/blob/main/hist_outlet_size.png)

- The figure above indicated that regardless of outlet size, the medium of item sales is similar. Small outlets have more items with a low sales price.

- The high outlets have a lot less number of item because of the total number of high outlets is much smaller in our data.

**Correlation between item sales and item visibility**
![plot](https://github.com/jiashenyue/salary-insights/blob/main/scatter_outlet_type.png)

The scatterplot indicates that the `Item_Visibility` and `Item_Outlet_Sales` do not have any correlation if we do not distinguish between item types.

**Correlation of numeric variables available in dataset**

![plot](https://github.com/jiashenyue/salary-insights/blob/main/corr.png)

The heatmap showed that `Item_MSRP` has the best correlation with `Item_Outlet_Sales`.

**Regression tree model**

![plot](https://github.com/jiashenyue/salary-insights/blob/main/linear_regression.png)

- Here is the model performance curve while fine-tuning the regression tree model
- The model performance over testing data reached the peak at `model_depth = 5`

**Model comparison**

- Comparing the regression tree model with a linear regression model, we find that the regression tree model performs much better than linear regression model over testing data.
- This is our recommended model to estimate the `Item_Outlet_Sales`.

**Model** | **Training R^2** | **Testing R^2**  
---|--- | ---
Linear Regression | 0.67 | -1.3788716713163139e+20
Regression Tree | 0.605 | 0.596
