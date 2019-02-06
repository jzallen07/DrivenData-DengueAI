# Project: Dengue AI 

## Table of contents:
* EDA and data cleaning - [Jupyter](https://github.com/jzallen07/DrivenData-DengueAI/blob/master/EDA.ipynb)  -  [HTML](https://github.com/jzallen07/DrivenData-DengueAI/blob/master/EDA.html)
* First Round Linear Model -  [Jupyter](https://github.com/jzallen07/DrivenData-DengueAI/blob/master/Linear_Model.ipynb))  - [HTML](https://github.com/jzallen07/DrivenData-DengueAI/blob/master/Linear_Model.html)

## Background:

I recently participated in a competition hosted by ([DrivenData](https://www.drivendata.org/)) with the goal of predicting the case level of  [Dengue fever](https://en.wikipedia.org/wiki/Dengue_fever).  Dengue is a mosquito-borne, generally topical, disease that is endemic in over 110 countries and affects millions of people every year.

Cases of Dengue (Past 3 Months)
<ceneter><img src="/img/Screen Shot 2019-02-05 at 9.44.30 AM (2).png" alt="world cases - past 3 months"></center>
Source: Driven Data, based on CDC reporting

Malaria and other similar diseases that have largely been eradicated with in much of the first world are now back burner topics that find themselves much neglected within and without much of the medical community at large.

Given the disease vector i.e. mosquitos dengue tends to present in an at least somewhat seasonal and weather related trend. As in with an increase in rainfall, heat, and humidity we would expect to see more mosquitos and thus more cases of dengue. 
Trending rainfall and # of reported cases:
![](readme/Average-rainfall-and-dengue-fever-notified-cases-per-month-Southern-State-of-Mato.png)
Source: [Average rainfall and dengue fever notified cases per month, Southern… | Download Scientific Diagram](https://www.researchgate.net/figure/Average-rainfall-and-dengue-fever-notified-cases-per-month-Southern-State-of-Mato_fig4_316177451)

So, on this basis, with the data from this project I hope to answer the following questions: 

The Data:
The data for this project is centered around two cities [San Juan, Puerto Rico](https://en.wikipedia.org/wiki/San_Juan,_Puerto_Rico) and [Iquitos, Peru](https://en.wikipedia.org/wiki/Iquitos). 
![](readme/Screen%20Shot%202019-02-05%20at%209.26.47%20AM%20(2).png)

The goal is to accurately predict the case load of Dengue (# of reported cases) in each location. **Side note**: reporting data for tropical diseases such as dengue, malaria, and chikungunya has historically been very….messy as can been seen ([here](https://www.biomedcentral.com/about/press-centre/science-press-releases/03-03-2016))([here](https://www.sciencedirect.com/science/article/pii/S0140673604174461)) and [here](https://www.who.int/neglected_diseases/Social_determinants_NTD.pdf). 

Real-world reporting messiness aside, the feature set for this data principally comes from NOAA in the form of regional weather data. At a glance these include temperature (mean, min, max), precipitation, relative humidity, and a vegetation index based of satellite imagery. A full feature description can be found [here](https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/page/82/#features_list).

This feature set is based on the fact that dengue as with many other tropical diseases is spread by mosquitos. These environmental factors are directly correlated with the growth of mosquito populations around the world round. Therefore, precipitation, temperature and humidity play an important role in accelerating the mosquito population.—[Life Cycle - American Mosquito Control Association](https://www.mosquito.org/page/lifecycle)

These features give a fairly simple representation of a complex reality. There are many other factors that could potentially affect not only the spread of dengue but also the severity of the impact it has at a public heath level. Those concerns are well beyond the scope of this project. 

Preparing the data for use:

As we are working with two distinct geographic regions with their own microclimates and other innate (unmeasured) variables we will split this project into two independent models and sub data sets. 

It would also be possible to treat each city as a categorical variable.  Especially, if using other types of ML model e.g. a tree, but sine I am making an initial run with a linear model and the meaningful differences between the two cities will only create noise in such a model this manner of dealing with city feature seems best in the current situation. 

Further, as we are dealing with data of several different scales and unit types it will be necessary to standardize the numerical data prior to training any form of linear based model.

Looking at the distribution below we can see that the former discussion is strengthened by the fact that each cities data covers different time periods and with greatly differing volumes of reported cases. 
![](readme/data_points_by_year.png)

Missing data:

As can be seen below. There is a moderate degree of missing data in each of the cities. We will be accounting for this by forward filling the empty fields. I will avoid dropping the missing field as I do not wish to loose the associated data

When we examine the reported cases at a weekly level it would appear that we can see the anticipated seasonal spikes (at least at a macro level) taking place in both San Juan and Iquitos . 
![](readme/weekly_trend.png)

Detailed discussion of the predictive modeling can be found in the notebooks found in this repository.
