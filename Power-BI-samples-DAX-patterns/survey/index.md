<style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
</style>


## Survey DAX pattern

Survey [explained on DAX patterns site](https://www.daxpatterns.com/survey/)

- Basic pattern example
    
    <iframe id="iframe-ss-1" title="static-segmentation-1" importance="low" allow="fullscreen"
    src="https://app.powerbi.com/view?r=eyJrIjoiOTIzZjVkNDEtYTQ4Yi00NmE0LWE5NTAtZGI5M2ZlN2U1ZTM4IiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    

- Complete pattern example
  
  This DAX version includes checks to handle special conditions.
  ```
  CustomersQ1andQ2 = SWITCH (
    TRUE,
    NOT ( ISCROSSFILTERED ( Filter2[AnswerKey] ) ), [CustomersQ1],
    NOT ( ISCROSSFILTERED ( Filter1[AnswerKey] ) ), [CustomersQ2],
    IF (
        HASONEVALUE ( Filter1[Question 1] )
            && HASONEVALUE ( Filter2[Question 2] ),
        IF (
            VALUES ( Filter2[Question 2] )
                <> VALUES ( Filter1[Question 1] ),
            CALCULATE (
                COUNTROWS ( Customers ),
                CALCULATETABLE (
                    Answers,
                    USERELATIONSHIP ( Answers[AnswerKey], Filter2[AnswerKey] )
                ),
                CALCULATETABLE (
                    Answers,
                    USERELATIONSHIP ( Answers[AnswerKey], Filter1[AnswerKey] )
                )
            )
        )
    )
  )
  ```
  
  This sample has separate pages with a single slicer and two slicers.
  
    <iframe id="iframe-ss-2" title="static-segmentation-1" importance="low"  allow="fullscreen" 
    src="https://app.powerbi.com/view?r=eyJrIjoiNjI3ZWZjYWUtOGMxZS00Nzg2LTkwMzAtYmJkMmYyZGIyMjcwIiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"></iframe>
    

### Return to: 
[Top](#survey-dax-pattern)
  
[Basket Analysis DAX pattern](/Power-BI-samples-DAX-patterns/basket-analysis/)
  
[Back to overview of DAX patterns](/Power-BI-samples-DAX-patterns/)
  
[Home](/.)
