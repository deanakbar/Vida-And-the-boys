# E-Commerce Shipping Data set


## Getting Started : 
 * Import pandas,numpy,matplotlib and seaborn library
* Info and describe data set
* Model Validation
* Model  Visualization

## How to import library
Import library to google collabs or you can use Jupyter notebook.
```sh
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import kruskal
```
Import Rcparams for default settings 
```sh
from matplotlib import rcParams
rcParams['figure.figsize'] = 12, 4
rcParams['lines.linewidth'] = 3
rcParams['xtick.labelsize'] = 'x-large'
rcParams['ytick.labelsize'] = 'x-large'
```
## Importing data
Importing data will be the first step of your project. Whether you have an excel file or csv file, they can easily be imported into pandas.
For importing comma separated value (CSV) files, use this line of code.
```sh
Import dataset
df = pd.read_csv('Train.csv')
```
## How to get Informations from your dataset
Provides a summary of the data including the index data type, column data types, non-null values and memory usage.
```sh
df.info()
```
## How to Describe dataset
Provides descriptive statistics that summarizes the central tendency, dispersion, and shape.
```sh
df.describe()
```
## Returns the first 5 rows of the dataframe.
you may insert a value between the parenthesis to change the number of rows returned. Example: df.head(10) will return 10 rows
```sh
df.head()
```
## Returns the last 5 rows of the dataframe.
you may insert a value between the parenthesis to change the number of rows returned. Example: df.head(10) will return 10 rows
```sh
df.tail()
```
## How to Model Visualization
Histogram Plot
```sh
plt.figure(figsize=(20,12))
for i, column in enumerate(df.columns, 1):
    plt.subplot(4,3,i)
    sns.histplot(df[column])
    plt.tight_layout()
```
Box Plot
```sh
plt.figure(figsize=(20,12))
nums = df.select_dtypes(exclude='object')
for i, column in enumerate(nums.columns, 1):
    plt.subplot(4,3,i)
    sns.boxplot(y = nums[column])
    plt.tight_layout()
```    
Kdeplot 
```sh
features = numerical
plt.figure(figsize=(15, 5))
for i in range(0, len(features)):
  plt.subplot(2, 4, i+1)
  sns.kdeplot(x=df[features[i]], color='green')
  plt.xlabel(features[i])
  plt.tight_layout()
```
Violin Plot
```sh
plt.figure(figsize=(15,5))
for i in range(0, len(numerical)):
    plt.subplot(1, len(numerical), i+1)
    sns.violinplot(y=df[numerical[i]], color='green', orient='v')
    plt.tight_layout()
```
Pair Plots (Hue + Numeric)
```sh
plt.figure(figsize=(10, 10))
sns.pairplot(dfcorr, diag_kind='kde', hue='Late_shipment(cat)')
```




## Source 

| Source | Link |
| ------ | ------ |
| Kaggle Dataset Download  | [https://www.kaggle.com/datasets/prachi13/customer-analytics]
| Google Collabs | [https://colab.research.google.com/drive/1NUEws22AMUXb8YdyrinVXXZ8o1EyRV08?usp=sharing#scrollTo=KM_JhBnGhpvf]|


## Summary  Insight 
**Descriptive Statistics**
 
* A. Pada kolom Discount_offered kami mengubah tipe data dari int64 menjadi float
* B. Tidak memiliki nilai kosong pada data set
* C. Pada kolom discount_offered minimal nilainya adalah 1 sehingga nilai std jauh lebih besar dibanding nilai mean,
* D. Nilai median lebih kecil dibanding dengan nilai mean sehingga memiliki distribusi positif.

## Univariate Analysis
** Box Plot**


A. Customer care call: The box plot indicates that customers typically make 3 to 5 calls to customer care. There are no outliers in this column.

B. Cost of the product: The distribution of data for the cost of the product on the box plot is between 180 and 250. There are no outliers in this column.

C. Prior purchase: The box plot shows that customers tend to make repeat orders, typically 3 to 4 times. There is one extreme outlier in this column at 10 orders.

D. Discount offered: The box plot shows that customers typically take discounts of 1% to 10%. There are many outliers in this column.

E. Weight in gms: The box plot shows that the weight of packages is typically between 1900 and 5000 grams. There are no outliers in this column.

F. Customer rating: The box plot shows that the company typically rates customers between 2 and 4 stars. There are no outliers in this column.

G. Late shipment: The box plot shows that the data is bimodal, with two distinct values: 0 and 1. This suggests that late shipment can be considered a categorical variable.

**Kdeplot**
Kernel Density Plot (Kdeplot)

A. Customer care call: The kdeplot shows that the distribution of customer care calls is multimodal. This suggests that customer care calls can be considered a categorical variable.

B. Cost of the product: The kdeplot shows that the distribution of the cost of the product is approximately normal.

C. Prior purchase: The kdeplot shows that the distribution of prior purchases is multimodal. This suggests that prior purchases can be considered a categorical variable.

D. Discount offered: The kdeplot shows that the distribution of discounts offered is positively skewed, with a mean that is smaller than the median and a long tail.

E. Weight in gms: The kdeplot shows that the distribution of weight in grams is negatively skewed, but not perfectly so. The high spike at 1900 grams makes the distribution appear bimodal.

F. Customer rating: The kdeplot shows that the distribution of customer ratings is multimodal. This suggests that customer ratings can be considered a categorical variable.

G. Late shipment: The kdeplot shows that the distribution of late shipments is bimodal. This suggests that late shipment can be considered a categorical variable.

**Count Plot**
Count Plot

A. Warehouse block: The count plot shows that Warehouse F has the largest number of items stored compared to the other warehouses (A, B, C, and D).

B. Mode_of_shipment: The count plot shows that the most common mode of shipment is by sea, while land and air shipments are relatively equal.

C. Product_importance: The count plot shows that customers most often purchase low-priority items, with a disproportionate number of high-priority items.

D. Gender: The count plot shows that the majority of customers are women, but the proportion of men is not significantly lower.

E. Reached_on_Time_Y.N: The count plot shows that items are often late rather than on time.

F. Customer Rating: The count plot shows that the proportions of ratings from 1 to 5 are not significantly different, with rating 3 being the most common.
## Multivariate Analysis
A. Results based on heatmap and Kendall tau methods:

Features that correlate positively with Late_shipment(num): Customer_rating(num) and Discount_offered.
Features that correlate negatively with Late_shipment(num): Customer_care_calls, Cost_of_the_product, Prior_purchases, and Weight_in_gms.
The two strongest features to pair with Late_shipment(num): Discount_offered and Weight_in_gms.
Based on the heatmap and Kendall tau methods, Late_shipment(num) and Discount_offered have a positive correlation. The higher the discount offered on a product, the higher the potential for its shipment to be delayed.
Based on the heatmap, Late_shipment(num) and Weight_in_gms have a negative correlation. The lighter a product is, the higher the potential for its shipment to be delayed.
Based on the heatmap, no features were found to correlate strongly with a value above 0.7. However, the two features that correlate closely to Late_shipment(num) are Discount_offered and Weight_in_gms.
Based on the Kendall tau method, the feature with the strongest correlation to pair with Late_shipment(num) is Discount_offered. However, this value is still far from approaching one.
Additional Opinion:

The use of heatmaps is not well-suited for this case due to the categorical nature of Late_shipsment(num).
B. Conclusion
Scatter plots where the two colors can be separated well and have a clear pattern are worth considering for the combination of variables Late_shipment(num) and Discount_offered and Weight_in_gms.
Discount_Offered over 10% experiences delays. Hypothesis: Discounts on products over 10% result in high purchases and shipments of a product, while the quota for shipping goods remains unchanged, so shipments are delayed. This type of case is called overload. This is often experienced by various expeditions in the world.
Weight_in_gms in the range of 2000 - 4000 grams experiences delays.



## Business Insight


From the analysis we have carried out, here are some business insights that have been determined:

*See which shipping methods are often delayed:
*Shipments by sea tend to experience delays in delivery. This is understandable because most shipments are made by sea. With that, the company can reduce shipments by sea by using other shipping methods. This will minimize congestion and delays in shipping goods.
*Shipping goods based on priority and shipping status:
*Based on product importance, it can be seen that shipments with a low priority type are more likely to experience delays in delivery. This is because customers are more likely to buy low-priority goods. Therefore, the company can arrange shipments based on the priority and status of shipments that are experiencing congestion.
*The relationship between weight and delays and recommending shipping based on the weight of the goods:
*Shipments of goods with a weight of < 4000 grams tend to experience delays. Therefore, it is necessary to further analyze the data on shipments of goods with a weight of < 4000 grams and 2000-4000 grams. So, we can recommend shipping based on the weight of the goods.
*Make discounts more attractive, use 5%, 10%, and 15% discounts:
*Giving discounts to customers with prior purchases of more than 3, using 5%, 10% and 15% discounts to make it more attractive and increase the likelihood of customers repeating their orders.

Additional Notes
The author uses the term "heatmap" to refer to a correlation matrix visualization.
The author uses the term "Kendall tau" to refer to a correlation coefficient for ordinal data.








 
 


