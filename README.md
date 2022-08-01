# Amazon_Vine_Analysis

#### Tools: PySpark, Google Colaboratory, Postgress/Pgadmin, AWS

### Overview of the analysis: 

The purpose of this analysis is to determine if the there is bias in the paid reviews. Using PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, using PySpark, Pandas, or SQL to determine if there is any bias toward favorable reviews from Vine members in your dataset. This analysis uses PySpark to prefrom the analysis. The dataset the was selected for analysis was 'Pet products' at this link: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Pet_Products_v1_00.tsv.gz.

The four tables created with data loaded into pgadmin are shown below:
The review_id_table:
![Screen Shot 2022-08-01 at 1 10 36 PM](https://user-images.githubusercontent.com/99676466/182245747-db61458a-8767-49bd-a9fb-3c8ef1fa62fd.png)

The customers_table:
![Screen Shot 2022-08-01 at 1 10 19 PM](https://user-images.githubusercontent.com/99676466/182245764-de8076aa-8eca-450a-8feb-90ebe4de0c1a.png)

The products_table:
![Screen Shot 2022-08-01 at 1 09 55 PM](https://user-images.githubusercontent.com/99676466/182245781-1611a52a-e29b-4431-a161-0023a8907d5f.png)

The vine_table:
![Screen Shot 2022-08-01 at 1 10 58 PM](https://user-images.githubusercontent.com/99676466/182245930-7f8b5844-10e9-4e90-913d-f4b71fc195c7.png)


### Results: Using bulleted lists and images of DataFrames as support, address the following questions:
The analysis begins with the creation of the Vine table with star ratings, helpful votes, total votes, whether or no the review is part of the Vine program, and if the purchase was verified. The first table is filtered to show only total votes over 20. Then that table is filtered to show the helpful votes that are over 50%. Then there are two tables; one shows which reviews are in the Vine program and which are not.
The vine table filtered ot show 50% helpful votes is shown below:

![Screen Shot 2022-08-01 at 2 57 19 PM](https://user-images.githubusercontent.com/99676466/182245343-3e28f045-0179-430d-bd97-4109f48b1351.png)


* How many Vine reviews and non-Vine reviews were there?
There were far more non_Vine review than Vine reviews, 37,840 unpaid, non-vine reviews and 170 paid, Vine review total.
~~~
total_review_unpaid = unpaid_df.count()
total_review_unpaid
~~~
~~~
total_review = paid_df.count()
total_review
~~~

* How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
Of the 170 vine reviews 65 of them were five star reviews.
~~~
five_star_paid = paid_df.filter(paid_df.star_rating ==5).count()
five_star_paid
~~~
And there were 20,612 five star unpaid reviews that are not a part of the Vine program. ~~~ five_star_unpaid = unpaid_df.filter(unpaid_df.star_rating == 5).count()
five_star_unpaid ~~~

* What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
The percent of Vine reviews that were five stars was 38.24% whereas the percent of unpaid five star reviews was 54.47%. 

~~~ 
percent_fivestar_paid = (five_star_paid/total_review)*100
percent_fivestar_paid ~~~
~~~ 
percent_fivestar_unpaid = (five_star_unpaid/total_review_unpaid)*100
percent_fivestar_unpaid 
~~~

### Summary: 
In your summary, state if there is any positivity bias for reviews in the Vine program. Use the results of your analysis to support your statement. Then, provide one additional analysis that you could do with the dataset to support your statement.
