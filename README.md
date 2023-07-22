# Grocery_Analysis
This is a project I did for class about a grocery store analysis. I found this data set through kaggle. Link below. 
https://www.kaggle.com/c/favorita-grocery-sales-forecasting


The question asked by stakeholders is that we need to meet the KPI of 19 million trasactions each year by the day. To get the total number of transactions by day I wrote this code in SQL 

        SELECT 
        SUM(transactions) as total_transactions,
        CASE WHEN EXTRACT(DAYOFWEEK from date) =1 THEN 'sunday' 
        WHEN EXTRACT(DAYOFWEEK from date) = 2 THEN 'monday'
        WHEN EXTRACT(DAYOFWEEK from date) = 3 THEN 'tuesday'
        WHEN EXTRACT(DAYOFWEEK from date) = 4 THEN 'wednesday'
        WHEN EXTRACT(DAYOFWEEK from date) = 5 THEN 'thursday'
        WHEN EXTRACT(DAYOFWEEK from date) = 6 THEN 'friday'
        WHEN EXTRACT(DAYOFWEEK from date) = 7 THEN 'saturday'
        END AS day
        FROM `dulcet-hulling-375416.Grocery.Transactions`
        GROUP BY day

  There is promotion discount data so that plays a role into foot traffic in this sales. It was beneficial to group these discounts to group these discounts by family and day since out KPI is revolving around day. The code cosistented of this 
  
                    SELECT SUM(onpromotion) AS total_discount, 
                  family,
                    CASE WHEN EXTRACT(DAYOFWEEK from date) =1 THEN 'sunday' 
                    WHEN EXTRACT(DAYOFWEEK from date) = 2 THEN 'monday'
                    WHEN EXTRACT(DAYOFWEEK from date) = 3 THEN 'tuesday'
                    WHEN EXTRACT(DAYOFWEEK from date) = 4 THEN 'wednesday'
                    WHEN EXTRACT(DAYOFWEEK from date) = 5 THEN 'thursday'
                    WHEN EXTRACT(DAYOFWEEK from date) = 6 THEN 'friday'
                    WHEN EXTRACT(DAYOFWEEK from date) = 7 THEN 'saturday'
                    END AS day
                  FROM `dulcet-hulling-375416.Grocery.Test`
                  GROUP BY family, day
                  ORDER BY day



  Then I wanted to get the total sales by family of this grocery store because I wanted to focus on the families that produce the most sales to reach our 19 millon transactions KPI. 

                    SELECT family, ROUND(SUM(sales),2) AS sales
                    FROM `dulcet-hulling-375416.Grocery.Train`
                    GROUP BY family

Through extracting this data we conclueded that 

If we take our discounts that happen on Wednesday and Friday from produce, dairy, and deli and distribute some of those discounts to Thursday we could see the result to more transaction being done on Thursday by more foot traffic. In order to follow through with this insight more data needs to be analyized when perishable trucks show up and what is the D&D and shrink on these perishable items from Wednesday to Thursday.


Dashboard and story links below 
https://public.tableau.com/app/profile/jeremy.mccormick/viz/GroceryAnalysisStory/Story1#5

https://public.tableau.com/app/profile/jeremy.mccormick/viz/GroceryAnalysisDashboard/Dashboard1


![Dashboard 1 (3)](https://github.com/SpotMcCormick/Grocery_Analysis/assets/132832823/a3a9cf0b-11b4-44ee-89c8-63ceef129d3f)



![Story 1](https://github.com/SpotMcCormick/Grocery_Analysis/assets/132832823/bac15909-b807-4d07-995d-f55602507030)

    
