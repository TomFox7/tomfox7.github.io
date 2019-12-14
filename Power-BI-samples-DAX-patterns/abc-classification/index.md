<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## ABC Classification DAX pattern

ABC analysis is an inventory categorization technique, with conceptual similiarity to Pareto analysis - see [Wikipedia article](https://en.wikipedia.org/wiki/ABC_analysis)

ABC Classification [explained on DAX patterns site](https://www.daxpatterns.com/abc-classification/)

- Basic pattern example
  
  This uses several calculated columns in the Products table.
    
    <iframe id="iframe-ss-1" title="static-segmentation-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiYTg4ODI0MjYtNDlkZi00NmMxLThjZTAtZDU1ZmVkNWYzMGM3IiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    

- Complete pattern example
  
  The template solution uses these generic values: \<granularity_table>, \<granularity_attribute> and \<measure>.
  ```
  [EntityMeasure] = CALCULATE ( <measure> )
 
  [CumulatedPercentage] = CALCULATE (
    <measure>,
    ALL ( <granularity_table> ),
    <granularity_table>[EntityMeasure]
        >= EARLIER ( <granularity_table>[EntityMeasure] )
      )
    / CALCULATE ( <measure>, ALL ( <granularity_table> ) )
 
   [ABC Class] = SWITCH (
    TRUE (),
    <granularity_table>[CumulatedPercentage] <= 0.7, "A",
    <granularity_table>[CumulatedPercentage] <= 0.9, "B",
    "C"
  )
  ```
    <iframe id="iframe-ss-2" title="static-segmentation-1" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiMjY2Y2ZkMjQtNGU5Yi00NjYwLTg0ZjEtYmMzNDRkYTI4MDcwIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    

### Return to: 
[Top](#abc-classification-dax-pattern)
  
[Back to static Segmentation DAX pattern](/Power-BI-samples-DAX-patterns/segmentation-static)
  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns)
  
[Home](/.)
