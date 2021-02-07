# Amazon Vine Analysis

## Overview

The purpose of this analysis is to extract, transform, and load a large dataset of Amazon reviews in order to further analyze trends within the data- more specifically to compare the differences in reviews for members of Amazon's Vine program and non-members.  We would like to uncover whether or not there is a positivity bias in the reviews between the paid Vine users and the non-Vine users.

**Extract-** The dataset category I chose to work with is a collection of reviews for outdoor equipment from Amazon's US Reviews Dataset.

**Transform-** Using PySpark the data was transformed into 4 relevant tables:

- Customer Table: comprised of Customer ID and Customer Count

- Products Table: comprised of Product ID and Product Title

- Review ID Table: comprised of Review ID, Customer ID, Product ID, Product Parent, and Review Date

- Vine Table: comprised of Review ID, Star Rating, Helpful Votes, Vine(Y/N), and Verified Purchase(Y/N)

**Load-** After connecting to an AWS RDS instance, the tables were then loaded into a pgAdmin database.


## Resources
- Data Sources: [amazon_reviews_us_Outdoors_v1_00.tsv.gz](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt)
               
 - Software: PySpark, Google Colab, pgAdmin 4, AWS (RDS and S3)
 
## Results 

-The entire dataset was comprised of 2,302,401 reviews

-Reviews with at least 20 votes (relevant reviews) amounted to 43,574 

-Reviews considered to be helpful (at least 50% of votes were deemed helpful) amounted to 39,976

#### How many Vine reviews and non-Vine reviews were there?

![vine-reviews.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/vine-reviews.PNG)

![non-vine-reviews.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/non-vine-reviews.PNG)

#### How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

![vine5star.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/vine5star.PNG)

![novine5star.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/novine5star.PNG)

#### What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

![vine5star%.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/vine5star%25.PNG)

![novine5star%.PNG](https://github.com/agregorash/Amazon_Vine_Analysis/blob/main/images/novine5star%25.PNG)

## Summary

The results of the analysis suggest that there is no positivity bias for reviews in the Vine program.  By percentage, the amount of 5-star reviews are nearly identical, 52.34% for Vine members and 52.69 % for non-members. The issue, however, is that the sample size of relevant Vine member reviews (107) is much smaller than relevant non-member reviews (39,869).  To further support this claim using this dataset, I might retrace run the analysis without filtering out reviews with less than 20 votes and with 50% of those votes being deemed unhelpful.  This may give us a larger sample size and more confidence in the results.

In order to further confirm the reportings of this analysis, I would randomly choose 4 more Amazon Review Datasets to run through my PySpark ETL pipeline and compare the findings.I would expect that some of these product review categories would have a higher count of relevant Vine member reviews, which would give us more confidence in the results.
