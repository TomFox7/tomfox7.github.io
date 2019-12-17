<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## Dynamic ABC Classification DAX pattern

ABC analysis is an inventory categorization technique, with conceptual similiarity to Pareto analysis - see [Wikipedia article](https://en.wikipedia.org/wiki/ABC_analysis)

Understanding of these three DAX patterns is a prerequisite:
- [Dynamic Segmentation][3]
- [Static ABC Classification][2]
- [Parameter Table][1]

Dynamic ABC Classification [as explained on Exceed.hr site in 2018](https://exceed.hr/en/blog/dynamic-abc-analysis-in-dax-variables) 
uses DAX variables to improve the solution by Gerhard Bruekl published in 2015, [explained on DAX patterns site.](https://www.daxpatterns.com/abc-classification/)

- Basic pattern example
  
  This uses several calculated columns in the Products table.
    
    <iframe id="iframe-ss-1" title="static-segmentation-1" importance="low" allow="fullscreen"
    src=""></iframe>
    

- Complete pattern example
  
  
  ```
  ABC Granular = CALCULATE ( [TotalRevenue],
      VALUES ( Dim_product[Product] ),
      FILTER (
          CALCULATETABLE (
              VAR BasicTable =
                  ADDCOLUMNS ( VALUES ( Dim_product[Product] ), "ProductRevenue", [TotalRevenue] )
              RETURN
                  ADDCOLUMNS (
                      BasicTable,
                      "Cumulative%", DIVIDE (
                          SUMX (
                              VAR CurrentProductRevenue = [ProductRevenue]
                              RETURN
                                  FILTER ( BasicTable, [ProductRevenue] >= CurrentProductRevenue ),
                              [ProductRevenue]
                          ),
                          CALCULATE ( [TotalRevenue], VALUES ( Dim_product[Product] ) )
                      )
                  ),
              ALL ( Dim_product[Product] )
          ),
          [Cumulative%] > [MinBoundary]
              && [Cumulative%] <= [MaxBoundary]
      )
  )
  ```
    <iframe id="iframe-ss-2" title="static-segmentation-1" importance="low"  allow="fullscreen" 
    src=""></iframe>
    

### Return to: 
[Top](#dynamic-abc-classification-dax-pattern)
  
[Static Segmentation DAX pattern][2]

[Dynamic Segmentation DAX pattern][3]

[Parameter Table DAX pattern][1]
  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns)
  
[Home](/.)

[1]: /Power-BI-samples-DAX-patterns/Parameter-Table
[2]: /Power-BI-samples-DAX-patterns/segmentation-static
[3]: /Power-BI-samples-DAX-patterns/segmentation-dynamic
