# GapMinder data presented in Power BI

Power BI can display a *dynamic time-series scatter chart* like [this original by Gapminder](https://www.gapminder.org/tools/) and then further explore the data by selected regions.

Here is the *live* version in Power BI Service where you can 'play' the time axis (button at bottom left).  To select multiple Regions use Ctrl-click in the other pages.

<iframe id="gm1" title="GapMinder data in Power BI" importance="low" src="https://app.powerbi.com/view?r=eyJrIjoiNjgzYzNjZjItODQwMS00OWVmLWJiNTMtZmIxZTA2MzExYzc1IiwidCI6Ijg1OTBlYTFlLTdiMjctNDJlNS04MTdmLTZjOGYzNzE5ZjMxNCJ9"  allow="fullscreen"><p>iFrames are not supported by this browser nor in Github.</p></iframe>
  <style>
    iframe {
      border: 1px solid black;
      width: 800px;
      height: 506px;
    }
  </style>
  
 This snapshot is for a single year 2015:
![GapMinder_screenshot_for_2015](https://beyondpowerbi.com/Power-BI-samples-GapMinder/countries_health_wealth_2016_v151.png)
([downloaded from here](https://www.gapminder.org/downloads/updated-gapminder-world-poster-2015/))
 

## Why is this interesting? ##

In their book 'Factfulness' the Roslings write that the world is not as bad as it seems and there is more improvement than people usually perceive.  They use data to correct pessimism and unfounded  explanations.  

For example, why are Cuba and the USA outliers in the health and wealth charts?  Cuba is the poorest of the healthy countries and the USA is the sickest of the rich countries.

The main purpose of Power BI is to present data in a persuasive way, to inform good quality decisions and actions.
 
 
## Technical notes on using Power BI ##

The data model in Power BI is quite simple: the two dimension tables are used to filter the one fact table.
![Power BI_data_model_screenshot](https://beyondpowerbi.com/Power-BI-samples-GapMinder/GapMinder_data_model_in_PowerBI.png)

The DAX calculations needed some care: the data are measurements taken over time (year to year) and so they are not additive.  They can only be aggregated in a given year (using SELECTEDVALUE) and calculating weighted averages, not sums or means.  For example:

```
Wt.Avg. GDP = CALCULATE (
    DIVIDE (
        SUMX ( AnnualData, AnnualData[Income] * AnnualData[Population] ),
        SUM ( AnnualData[Population] ),
        0
    ),
    FILTER ( Years, Years[Year] = SELECTEDVALUE ( Years[Year] ) )
)

Wt.Avg. GDP/Lifespan = CALCULATE (
    DIVIDE ( AnnualData[Wt.Avg. GDP], AnnualData[Wt.Avg. Lifespan], 0 ),
    FILTER ( 'list-of-countries-etc',
        'list-of-countries-etc'[Region] = SELECTEDVALUE ( 'list-of-countries-etc'[Region] )
    )
)
```
For more information on Data Models and DAX for 'snapshots of time-series data' see [chapter 6 in Analyzing Data with Power BI and Power Pivot for Excel, 2017 by Alberto Ferrari and Marco Russo](https://www.sqlbi.com/books/analyzing-data-with-microsoft-power-bi-and-power-pivot-for-excel/).

The menu on the front page (and the return Home buttons) use Bookmarks.  The Regional slicers are synchronised across several charts.  The population chart uses a custom visual 'HierarchySlicer' for selection of Regions or Countries.

### Return to: 
[Top](#gapminder-data-presented-in-power-bi)  [Home](https://beyondpowerbi.com/)
