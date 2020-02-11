<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## Customer Churn DAX pattern
  
  
- 2015 New and returning customers [explained on DAX patterns site.](https://www.daxpatterns.com/new-and-returning-customers/)

  - Complete pattern example   
    This includes both absolute and relative measures.
      
    <iframe id="iframe-cc-4" title="customer-churn-4" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiYmRkZTIyNTgtMTM1Yi00ZWNlLWI0MTMtNjRmNWFmZTI4NmJlIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe><br>

  - Improved using VAR and a set function

    ```
      MEASURE Customer[NewCustomersSet] =
        VAR CurrentCustomers = VALUES ( Sales[CustomerKey] )
        VAR OldCustomers = 
            FILTER (
                CurrentCustomers,
                CALCULATE (
                    MIN ( Sales[OrderDate] ), 
                    ALL ( 'Date' )
                ) < MIN ( 'Date'[FullDate] )
            )
        RETURN COUNTROWS ( EXCEPT ( CurrentCustomers, OldCustomers ) )
    ```
    
  - Sales by Customer type example   
    Here the list of customers is a filter argument in the relevant CALCULATE expression.
      
    <iframe id="iframe-cc-4" title="customer-churn-4" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiMDU2MGI1MzQtZDNhMS00MWZlLWIwOTYtYmFmYWI5MzZhZmVjIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe><br>


- 2016-05 Faster New and Returning Customers [explained on the SQLBI site.](https://www.sqlbi.com/articles/computing-new-customers-in-dax/)   
  This version of the measure is much faster than the one published in 2015.

  ```
  MEASURE Sales[NewCustomers] =
    COUNTROWS (
        FILTER (
            CALCULATETABLE (
                ADDCOLUMNS (
                    VALUES ( Customer[CustomerKey] ),
                    "DateOfFirstBuy", CALCULATE ( MIN ( Sales[OrderDate] ) )
                ),
                ALL ( 'Date' )
            ),
            CONTAINS (
                VALUES ( 'Date'[FullDate] ), 
                'Date'[FullDate], 
                [DateOfFirstBuy] 
            )
        )
    )
  ```
  
    <iframe id="iframe-cc-1" title="customer-churn-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiMDZkOTI5NjMtZDk3OC00OWU5LTgxMDMtZDJmNTE0ZWM3MTIwIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe><br>
    

- 2017 Customer Attribution Analysis [explained by Sam McKay.](https://blog.enterprisedna.co/customer-attrition-analysis-advanced-dax-in-power-bi/)

-2020-02 More measures for Customer Retention [explained by Reza Rad](https://radacad.com/customer-retention-in-power-bi-dax-measures)
  
### Return to: 
[Top](#customer-churn-dax-pattern)
  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns/)
 
[Basket Analysis DAX pattern](/Power-BI-samples-DAX-patterns/basket-analysis/)
  
[Home](/.)
