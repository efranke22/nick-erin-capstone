A Spatial Analysis of Elevated Blood Lead Levels in the Twin Cities
Metropolitan Region
================
Erin Franke and Nicholas Di
May 6, 2022

    ## Reading layer `LakesAndRivers' from data source 
    ##   `/Users/erinfranke/Desktop/MACStats/Correlated Data/nick-erin-capstone/DataShapefiles/shp_water_lakes_rivers' 
    ##   using driver `ESRI Shapefile'
    ## Simple feature collection with 2313 features and 8 fields
    ## Geometry type: MULTIPOLYGON
    ## Dimension:     XY
    ## Bounding box:  xmin: 419538.6 ymin: 4922700 xmax: 522665 ymax: 5029945
    ## Projected CRS: NAD83 / UTM zone 15N

    ## Reading layer `tl_2019_27_prisecroads' from data source 
    ##   `/Users/erinfranke/Desktop/MACStats/Correlated Data/nick-erin-capstone/DataShapefiles/tl_2019_27_prisecroads' 
    ##   using driver `ESRI Shapefile'
    ## Simple feature collection with 4309 features and 4 fields
    ## Geometry type: LINESTRING
    ## Dimension:     XY
    ## Bounding box:  xmin: -97.23724 ymin: 43.4995 xmax: -89.58524 ymax: 49.00066
    ## Geodetic CRS:  NAD83

# Introduction

When raising a child, parents go through lots of stress to keep their
children safe and healthy. From using carseats to getting children
vaccinated to working on speech and mobility development and beyond,
parents have a lot on their plate. But one thing that may be overlooked
in providing safe and healthy environment for a child is lead. Lead in
paint, soil, air, or water is invisible to the naked eye and has no
smell (“Prevent Children’s Exposure to Lead” 2021). However, children
can be exposed to lead in a variety of manners, including swallowing
house dust or soil contaminated by lead paint or drinking water
delivered through lead-based pipes, faucets, and plumbing fixtures.
Exposure to this hidden element can seriously harm a child’s health,
including damage to the child’s brain and nervous system, slowed growth
and development, as well as learning, hearing, speech, and behavior
problems (“Prevent Children’s Exposure to Lead” 2021). If exposed to
especially high levels of lead, children can face a brain condition
known as encephalopathy, severe neurological damage, coma, and even
death (“Annual Elevated Blood Lead Levels” 2020). Thus, without a
question it is crucial to keep lead exposure to a minimum when raising a
child.

In this analysis, we analyzed elevated blood lead levels in the
**7-county Twin Cities metropolitan area** using public data provided by
the **Minnesota Department of Health** over the period of 2015-2019
(Health, n.d.). To protect the privacy of individuals, the smallest
granularity we were able to obtain this data was on the census tract
level, meaning for each of the 691 census tracts in the Twin Cities
metropolitan area we obtained information on how many children were
tested and how many of those tests resulted in elevated blood lead
levels. To have **elevated blood lead levels (EBLL)** means that a child
has a confirmed result **at or above 5 micrograms of lead per deciliter
of blood (mcg/dL)** (“Annual Elevated Blood Lead Levels” 2020). Children
under 6 years of age are tested. The Minnesota Department of Health
idenifies children living in the Minneapolis and Saint Paul city limits
as children at a higher risk for lead exposure and recommends these
children to receive blood lead testing at 1 and 2 years of age. This
recommendation is warranted given that in 2019, between 1-2% of children
in Minneapolis or St. Paul had an EBLL, which is double the statewide
average and higher than any other region of Minnesota (“Annual Elevated
Blood Lead Levels” 2020). Interestingly, the MDH has found children
living in the Metro area but not living in the cities of Minneapolis or
St. Paul are at a lower risk of lead exposure than the Greater Minnesota
(non-Metro) are. Only about 0.3% of these children have high EBLL levels
whereas about 0.8% of children living in MN outside the metro area have
high EBLL levels. As a result, to best explore this contrast between
Minneapolis-Saint Paul and the suburban region, this project will solely
focus on EBLL data from the 7 county Twin Cities metro area. This region
is shown in navy on the road map of Minnesota below.

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

# Research Goal

Keeping the health consequences of lead exposure to children in the
front of our minds, our research focuses on investigating what is
correlated with a census tract having a noticeably high proportion of
children testing with elevated blood lead levels. We defined a tract to
be a “high lead tract” if at least 1% of the tests in the tract resulted
in elevated blood lead levels (meaning 5+ mcg lead/dL). This left us
with 106 “high lead” tracts and 585 “safe” tracts. The location of these
“high lead” tracts in the Twin Cities metropolitan area can be seen
below. It is clear that the majority of them fall in the
Minneapolis-Saint Paul city limits.

![](README_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

The reason why this research question is important is because
understanding what is correlated with tracts having high lead levels can
help the Minnesota Department of Health, organizations, and families
protect children from lead exposure. For example, it wouldn’t be
unreasonable to expect tracts with older homes to have higher lead
levels, as these homes are more likely to have been built when science
did not know the harms of lead pipes and paint. On March 28, 2022, Saint
Paul Mayor Melvin Carter announced a $14.5 million American Rescue Plan
investment to remove thousands of lead pipes across the city (n.d.). If
home age appears a strong indicator of high lead levels, identifying
tracts with old homes, high lead levels, and lots of young children can
alert the city to replace their pipes first. In our research we also
might search for a relationship between testing, income, and lead
levels. If we are to find certain income groups getting tested more or
less than others holding other variables constant, we can shed light on
that and advocate for resources to get specific tracts the testing they
need and deserve given their exposure.

To help us understand what is correlated with a tract being “high lead,”
we will need more than just the information provided by the MDH of tract
lead levels. Using the **tidycensus** (Walker and Herman 2022) package
in R, we can access a plethora of information on each census tract
including its estimated mean age, mean income, population, proportion of
family households, home age, and so much more. We begin by exploring the
relationship between many of these variables and testing as well as
EBLLs.

# Exploratory Data Analysis

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-saintpaul" class="csl-entry">

n.d. *Saint Paul Minnesota*.
<https://www.stpaul.gov/news/saint-paul-announces-145-million-investment-replace-lead-pipes>.

</div>

<div id="ref-leadoverview" class="csl-entry">

“Annual Elevated Blood Lead Levels.” 2020. *Childhood Lead Exposure:
Annual Blood Lead Levels - MN Data*.
<https://data.web.health.state.mn.us/lead_annual_level>.

</div>

<div id="ref-mdhdata" class="csl-entry">

Health, Minnesota Department of. n.d. *Childhood Lead Exposure Map: MNPH
Data Access - MN Dept. Of Health*.
<https://mndatamaps.web.health.state.mn.us/interactive/leadtract.html>.

</div>

<div id="ref-cdcPrevention" class="csl-entry">

“Prevent Children’s Exposure to Lead.” 2021. *Centers for Disease
Control and Prevention*. Centers for Disease Control; Prevention.
<https://www.cdc.gov/nceh/features/leadpoisoning/index.html>.

</div>

<div id="ref-tidycensus" class="csl-entry">

Walker, Kyle, and Matt Herman. 2022. *Tidycensus: Load US Census
Boundary and Attribute Data as ’Tidyverse’ and ’Sf’-Ready Data Frames*.
<https://walker-data.com/tidycensus/>.

</div>

</div>
