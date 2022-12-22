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
