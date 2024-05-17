**RFM-ANALYSIS-FOR-CUSTOMER-SEGMENTATION-USING-EXCEL**

RFM is a form of behavioural targeting and customer segmentation that helps businesses rank and segment their consumer base. It is sometimes referred to as RFM analysis. It consists of three factors, namely:

Recency (R): This measures how recently a consumer made a purchase within a given time frame. Those who have recently made a purchase will score higher.
Frequency (F): This evaluates how often a customer makes purchases over a period of time and can effectively measure customer loyalty. Customers who make purchases more often score higher.
Monetary Value (M): This refers to how much a customer spends over a period of time. Customers who spend more are given higher scores.
RFM helps businesses identify valuable customers, determine customer support levels, and develop effective marketing campaigns to boost brand loyalty and increase conversions along the customer journey.

RFM analysis is a tool that can predict customer behaviour and help businesses understand the likelihood of future purchases and spending. Focusing on a small percentage of loyal clients can be more beneficial.


**INTRODUCTION**

Savill Corporation faced a critical business problem. They had a lot of customer data, but they needed to segment customers for targeted marketing campaigns. The challenge was to separate top customers from less engaged customers.

**DATASET INFORMATION**

The dataset provided is made up of 3 files in Microsoft Excel format containing the company’s sales data for 2021 to 2023. The dataset contains at least 66,000 rows and 15 columns, each giving specific information. The dataset can be downloaded here. Below is the data dictionary:


**TOOLS USED:**

Microsoft Excel and Power Query were the tools used for cleaning, analyzing, and visualizing this dataset.

Let’s get to work!!!

**DATA CLEANING AND TRANSFORMATION**

I linked Excel to my folder and used Power Query’s “GET DATA” features to load the data for merging, cleaning, and transformation.


The transformations and cleaning were:

Checking and removing all duplicates in the data.
Identifying null/missing values and extracting values for them by using the FILL functionality of Power Query.

3. Getting the Profit from the Sales and Profit margin using the CUSTOM COLUMN functionality of Power Query.


4. I added a new column, DISCOUNT LEVELS from the Discount column to segment them into levels(0–20% — Low; 21%-40% — Medium; 41% and higher — High) using ADD CONDITIONAL COLUMN functionality of Power Query.


5. Getting the Shipping duration from the Ship and Order Date columns using the CUSTOM COLUMN functionality of Power Query.


6. I identified outliers in the data by using Microsoft Excel’s BOX AND WHISKER functionality. Upon further investigations, I was able to get that they were entered in error and I changed them to the correct values.


7. Other necessary transformation using Power Query include changing data types. The table was then loaded back into Excel for further analysis. Below is the table after transformation and cleaning.


8. To represent all three RFM factors, I used a PIVOT TABLE to create columns with Customer ID, Max of Order Date (Recency), Count of OrderID (Frequency) and Sum of Sales (Monetary Value).


9. After preparing the data, I copied the pivot table and pasted it as values into a separate sheet to do customer RFM analysis.


10. I then converted the data into a table and created a column for Days since the last order from the Max Order date column using the formula =TODAY()-B2. B2 is the value of the max order date.


**FEATURE SELECTION**

In the context of RFM (Recency, Frequency, Monetary) Analysis, we will focus exclusively on the relevant columns. These include Customer ID, Max of Order Date, Days Since Last Order, Count of Order ID, and Sum of Sales, in addition to the Recency, Frequency, and Monetary Value score columns.


**PERCENTILE**

To find the RFM scores, I will create an RFM legend and use the PERCENTILE.INC function in Excel. This function was used because it calculates the value at a specified percentile in a dataset, including the value at the specified percentile itself.

The formula we will use is:

=PERCENTILE.INC(array,k)

array: This represents the fixed range of values for which we want to calculate the percentile.

k: the key (each percentage ranging from 0 to 80%)


Our ranking formula assigns a score of 1 to the lowest and 5 to the highest values. This method works well for evaluating the three RFM factors.

**RFM SCORES**

To obtain the Scores for each factor, I used the VLOOKUP function in Excel, with the RFM Legend tables being the reference table for lookup. The scores are highlighted in yellow below.

The formula used is:

=VLOOKUP(B3,$P$5:$Q$9,2,TRUE)
B3: This corresponds to the specific value for which we wish to compute the percentile rank.
$P$5:$Q$9: This represents the fixed range of values for which we want to calculate the percentile rank.
2: This signifies the column whose value we want to return.
TRUE: This represents the range lookup.

**CREATE RFM SCORE**

I generated a new column named “RFM” by summing the individual scores for recency, frequency, and monetary value. Additionally, used the PERCENTRANK.INC function to determine the ranking score for this newly created RFM column. The result will be multiplied by 5 to obtain whole numbers ranging 0–5.

The formula used is;
=PERCENTRANK.INC($I:$I,I3,1)*5
$I:$I: This represents the fixed range of values for which we want to calculate the percentile rank.
- I3: This corresponds to the specific value for which we wish to compute the percentile rank.
- 1: This signifies the number of significant digits to be used in the calculation.

**CUSTOMER SEGMENTATION**

**To segment the customers, I used the IF function in Excel. Customers with RFM scores of 4 and 5 are Top customers, customers with scores of 2 and 3 are Loyal customers and customers with scores of 0 and 1 are At-risk customers. The result is shown in the table below:

The formula used is
=IF(J3>=3.5,”Top Customer”,IF(J3>=1.5,”Loyal Customer”,IF(J3<=0.5,”At Risk/Need Attention”,””)))


**ANALYSIS**

To begin the analysis for each customer group, we’ll use a pivot table. This table will sort customers into their respective segments and provide key statistics for each one.

What is the total number and percentage of customers in each segment?
Using a Pivot table, I was able to get the total number of customers, the total customers in each segment and the percentage of each customer segment

2. What is the average recency, frequency, and monetary value for each customer segment?
We will use a pivot table to obtain the average Recency(days), Frequency, and Monetary values; the result is shown in the table below.

3. Who are our most valuable customers based on RFM segmentation?
A total of 13 customers with RFM scores of 4 and 5 were identified as our most valuable customers with the aid of a pivot table. They are shown in the table below:


**CUSTOMER SEGMENT PROFILE**

We will combine information from the pivot tables to build the customer profile for each segment.

**INSIGHTS**
A total of 50 customers were analyzed, and their distribution across different segments is as follows:
- 26% were categorized as top customers.
- 44% were classified as loyal customers.
- 30% were identified as at-risk/need attention customers.

2. For Top Customers:
On average, they made 4,061 purchases, their average spending per purchase was £4,191,141.38, and their last product purchase by top customers occurred, on average, 126 days ago.

3. At-Risk/ Need Attention Customers:
The average for customers in the at-risk segment was 3,940 purchases. They spent an average of £4,019,141.05 on their purchases, and their most recent product purchase took place, on average, 126 days ago.

**RECOMMENDATIONS**
**Top Customers**

1. Exclusive Loyalty Programs:
   
**Provide top-tier loyalty programmes with unique perks, including early access to deals, VIP events, and customized services.
**Reward them with luxury items, cashback, bonus points, or tiers of rewards according to their spending levels.
2. Personalized Recommendations:

**Make product recommendations based on their past purchases and interests by using data-driven personalization.
**Provide tailored emails that feature limited-edition or carefully chosen collections that correspond with their interests.
3. VIP Treatment:

**To meet their demands quickly and effectively, offer VIP customer service through priority support channels or devoted account managers.
**Provide complimentary upgrades, quicker shipping, or extended return policies to improve their purchasing experience.

**At-risk/Need Attention Customers**

1. Re-Engagement Campaigns:
   
**To win back at-risk clients, send targeted re-engagement emails or SMS campaigns that include attractive deals or incentives.
**Use personalized messaging that acknowledges their past purchases and encourages them to return with a special discount or promotion.
2. Feedback Solicitation:

**Utilize feedback forms or surveys to contact at-risk clients and ascertain the causes of their declining engagement or satisfaction.
**Tailor your offerings to better satisfy their requirements by addressing any concerns or issues raised in their feedback.
3. Win-Back Incentives:

**Implement win-back incentives, such as a complimentary gift or one-time discount, to motivate consumers who are at risk of abandoning your brand and returning with another purchase.
**Implementing expiration dates or limited quantities can effectively generate a sense of urgency, thereby motivating immediate action.
