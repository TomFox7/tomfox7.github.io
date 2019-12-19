<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## Basket Analysis DAX pattern
This pattern is a specialization of the Survey pattern.
- 2015 Basket Analysis [explained on the DAX patterns site](https://www.daxpatterns.com/basket-analysis/).  
  
  - Basic pattern example
    
    The key feature is a *copy* of the Product table, which contains the *same data* and has the prefix 'Filter' before all the table and column names. The relationship between the Sales table and the Filter Product table is inactive.  This Filter table enables use of a dual filter on products and/or their attributes.  
    
    <iframe id="iframe-ba-1" title="basket-analysis-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiZjVlNjk4NmItYWMyYi00MzQ1LTllN2UtMGYxZjNmMTdiZWViIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    <br/>
  - Complete pattern example
    
    This sample shows, in separate tabs, measures based on: \- 
    - Orders 
    - Customers 
    - Orders or Customers with both Products.  
    <br/>
    <iframe id="iframe-ba-2" title="basket-analysis-2" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiOTQzMzljZDktZWRkYi00OGJlLTgwZjktMTg5MjQ0MmNlMmU3IiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    <br/>

- 2019 Sequential Basket Analysis [explained by Davis Zhang](https://www.linkedin.com/pulse/explore-potential-products-through-customers-purchase-davis-zhang).  
  This article extends 'Basket Analysis' by taking into account the chronological order in which customers purchase different products.

    <iframe id="iframe-sba-1" title="sequential-basket-analysis-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiZTIzY2M0YmEtNjU2Ni00Mzc1LWE4MjctYWRkOTFiMTAzMGQwIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    <br/>

- 2014 Basket Analysis [explained by Gerhard Brueckl](https://blog.gbrueckl.at/2014/02/applied-basket-analysis-in-power-pivot-using-dax/).  
    <br/>

### Return to: 
[Top](#basket-analysis-dax-pattern)
  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns/)
  
[Home](/.)
