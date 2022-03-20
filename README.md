# Big_Data_Intro

## Background: 
* Please note this is copied directly from the module * 

"Since your work with Jennifer on the SellBy project was so successful, you’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, you’ll have access to approximately 50 datasets. Each one contains reviews of a specific product, from clothing apparel to wireless products. You’ll need to pick one of these datasets and use PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, you’ll use PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members in your dataset. Then, you’ll write a summary of the analysis for Jennifer to submit to the SellBy stakeholders."

- From Module 16 Challenge

## Results: Using bulleted lists and images of DataFrames as support, address the following questions:
![Python Table](https://github.com/awar2170/Big_Data_Intro/blob/main/Amazon_Vine_Analysis/PgAdmin%20Tables/Python%20Table.PNG)

    1. How many Vine reviews and non-Vine reviews were there?
    - There were 33 Vine reviews and 45,388 non-Vine reviews
    2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
    - There were 15 5-Star Vine reviews and 23,733 5-Star non-Vine reviews. 
    3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
    - 45.45% Of the vine reviews were 5-stars and 52.28% fo the non-Vine reviews were 5-stars.

## Summary: In your summary, state if there is any positivity bias for reviews in the Vine program. Use the results of your analysis to support your statement. 
There appears to be bias in those who reviewed the vine because there are 45.45% 5-star reivews for unpaid groups, but 0 5-star reviews for those who paid for the vine.  There is a bias towards the unpaid.  