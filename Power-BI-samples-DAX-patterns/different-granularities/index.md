<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## Different Granularities DAX pattern

Different Granularities	[explained on DAX patterns site](https://www.daxpatterns.com/handling-different-granularities/)

- Basic pattern example
    
    In this example, the advertising expenditure is only known monthly, so the Total Advertising and Advertising% should not be shown at the daily level of sales data.
    
    ```
    [Total Advertising] =
      IF (
          NOT ( ISFILTERED ( 'Date'[Date] ) ),
          SUM ( Advertising[AdvertisingAmount] )
      )
    ```
    
    <iframe id="iframe-dg1" title="Different-Granularities-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiMWFlZTA4NzItOGY1Ny00YzdiLTgzYmEtMzY3NTVhNTk0ZmRmIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9">
    </iframe>
    

- Complete pattern example
    
    <iframe id="iframe-dg2" title="Different-Granularities-2" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiYmJlMDMxNTMtZWQwYS00ZTZmLThkOTQtY2Y2ZGIxNjMyMjJjIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9">
    </iframe>
           
- Simulate a relationship at different granularities example

  The Customers are grouped dynamically by Sales Amount.

    <iframe id="iframe-dg3" title="Different-Granularities-3" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiMTA2NzAxYmUtNDEyZS00ZjVlLWFmYTItZWFlYzY2Y2E4YTZiIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9">
    </iframe>
     
    
### Return to: 
[Top](#different-granularities-dax-pattern)  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns)  
[Home](/.)
