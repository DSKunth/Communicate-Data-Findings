# (Prosper Marketplace Loan Data Exploration)
## by Dorothy Kunth



## Dataset

The dataset is a loan data from Prosper Marketplace, a lending platform which contains 113,937 listings of loans with origination dates between 2005 and 2014. It has 81 variables on each loan such as loan amount, loan status, borrower rate, term, borrower's income range, employment status, Prosper rating, Prosper score and many others. The dataset can be dowloaded [here](https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv) and tha data dictionary can be found [here](https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0). [Investment Glossary](https://www.prosper.com/investor/glossary), [Search Listings Tool](https://www.prosper.com/invest/search_results.aspx?cg=HR&ena=False&enf=False&eng=False&enh=False&gc=-1&hd=True&lq=&m=1&nc=True&pg=1&sf=8&tg=1) and [Prosper Zendesk](https://prosper.zendesk.com/hc/en-us/categories/200531029-General) are good sources of additonal information regarding the different variables. 

For the purpose of this data exploration, 20 variables were selected and two dataframes will be used: df_prosper with 113,937 records and df_prosper_rating with 84853 records. df_prosper_rating is the dataframe created where the variables: EstimatedReturn, ProsperRating (Alpha) and ProsperScore are not null. There are 29084 records with null values in EstimatedReturn, ProsperRating (Alpha) and ProsperScore columns as these features are applicable only for loans originated after July 2009. Since it is a lot of records - about 25% of the total records, the df_prosper_rating will be used for analysis where the said variables are involved.




## Summary of Findings

During the data exploration, I have confirmed that the borrower rate is strongly affected by the Prosper rating and Prosper score. The borrower rate has a negative correlation with Prosper rating. That is, the higher the borrower rate, the lower the rating and obviously, when the rating is high, the borrower rate is low. Same with Prosper score, the borrower rate has a negative correlation with Prosper score based on both scatterplot and heatmap. This is what I expected as it is a common knowledge that if a borrower has a good rating and score, he can then get a lower interest rate. It means that based on the rating and score, he has a good credit standing and payment history. In the distribution of borrower rate, majority of the loans have borrower rates between 5 and 40%. After adjusting the bins, it looks unimodal with high peak between 15-16% and there is also a very high peak at 31-32%.

For the other variables other than the variables of interest, I have established the features, related to the borrowers’ credit profile, that affect the origination of the loans. The origination of the loans is mostly affected by income range specifically those in USD 50,000-74,999, USD 75,000-99,999 and USD 100,000+ income range. Based on my findings, the top two most annual income ranges are USD 25,000-49,999 and USD 50,000-74,999 respectively. However, it is interesting to see that a little above 1% belongs to the loans taken by those not employed and with income range of USD 0.  I find it usual that majority of the loans amounts from USD 4,000 to USD 15,000 are granted to those employed or with full-time job. Borrowers who are retired and part timers get the lowest loan amount, which I also find reasonable. As for Prosper rating, majority of the loans have rating of C.  There is a significant number of loans which has the lowest rating HR (high risk) which I find unusual. If I am the investor I would definitely not invest in loan listed as high risk rating. 

As for the loan features, there is not much strong indication that a certain loan feature drives more origination than the others. But for the loan amounts, the top 3 loan amounts are USD 4,000.00, USD 15,000.00 and USD 10,000.00 respectively. Majority of the loans have a term of 36 months or 3 years. The top listing category is debt consolidation which means most loan originations are for the purpose of payment of existing debts. And most loans have borrower rates between 5 and 40%.

There are some findings that did not meet my expectations:
1. CurrentDelinquencies and AmountDelinquent have a week positive correlation with each other. Though I expected a stronger correlation as these variables are both about past due loans.
2. The amount delinquent, number of current delinquencies and debt to income ratio are part of the borrowers’ credit profile that are computed at the time the credit profile was pulled and these don't have that much effect on loans.
3. I didn't see a strong relationship between number of investors and lender yield and between number of investors and estimated return. I was expecting that more investors will fund loans that have high lender yield and estimated return.
4. While investors are funding the loans of those with high income range, there are also investors funding those unemployed and with 0 income.
5. As mentioned above, there is a significant number of loans which has the lowest rating HR (high risk) which I find unusual. I am under the impression that an investor would definitely not invest in loan listed as high risk rating.




## Key Insights for Presentation

For the presentation, I will focus on the main features of interest, which are the borrower rate, Prosper rating and Prosper score. To visualize the findings, I will display the distribution of borrower rate, the correlation of borrower rate and Prosper rating, the correlation of borrower rate and Prosper score and a scatterplot of loan amount by borrower rating and Prosper score.

I will also present some features affecting the origination of the loan. To visualize, I will display the distribution of income range, distribution of loan amount and a plot matrix of loan amount against categorical features: Prosper rating, employment status and income range. 

And lastly, I will present whether the number of investors are driven by the income range or Prosper rating or both. I will display a bar chart to visualize this.
