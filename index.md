# Asthma and Pollution in New York City
It is common knoweldge that air pollution is a contributing factor of respiratory diseases. And among all the broad types of respiratory diseases that exists, specifically asthma. Asthma is a chronic respiratory disease characterized by variable airflow obstruction, bronchial hyperresponsiveness, and airway inflammation. [[1]](https://pubmed.ncbi.nlm.nih.gov/32867076/) Researchers have long linked asthma with exposure to air pollution, which can make asthma symptoms worse and trigger asthma attacks. Moreover, it is estimated six million children in the United States with asthma are especially vulnerable to air pollution. [[2]](https://www.epa.gov/sciencematters/links-between-air-pollution-and-childhood-asthma#:~:text=Researchers%20have%20long%20linked%20asthma,worse%20and%20trigger%20asthma%20attacks). And not only vulnerable once they have the disease. It has been also proved that exposure to main air pollutants such as NO2, CO, and PM2.5 is linked to regional DNA methylation differences in asthma. [[3]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5756438/pdf/13148_2017_Article_433.pdf)

The aim of this website is to dig deeper into this relation between air pollution and asthma. To do so, NYC air pollution data will be used and combined with asthma hospitalizations data for children. Is there any clear correlation between air pollution and the number of asthma hospitalizations? If so, which are the air pollutants that are more correlated? How do these values vary between the different neighbourhoods? Where is more urgent to reduce the emissions of hazardous air pollutants? Is it possible to predict which is gonna be the number of asthma hospitalizations in order to prepare these hospitals that are gonna suffer more for such big workloads? 

<iframe src="evolution.html" height="400" width="1000"></iframe>

It can be clearly seen how there is a tendence in decrease in both the number of asthma hospitalizations and the levels of emission of the main pollutants. With the exception of O3, the levels of PM2.5, NO2 and SO2 have been significanlty reduced in the last decade, which evidence that sustainability policies were put into practice. Air quality levels registred during the 2000-2010 decade and their impact on population's health raised the attention of key decision makers and the public which lead to polices aming to improve local air quality, reduce greenhouse gas emissions and revert the situation that air pollution was taking. [[4]](https://www.healthypeople.gov/2020/healthy-people-in-action/story/new-york-city-air-quality-programs-reduce-harmful-air-pollutants)

Once seen how the tendency that both asthma cases and air pollutants are following, the next question that arise is: Is it possible to build a model that relates the number of asthma hospitalizations with the different levels of air pollutants? Which is the impact that each district has?
## Machine learning model to predict the level of asthma hospitalizations
As a starting point, we built this model aiming to predict if, with the chosen features, we were able to predict the number of asthma hospitalizations. And we were, with high accurate results. Thus, few things to highlight emerged from our analysis. 

First, and the most important, its been shown that the number of asthma hospitalizations basically depends on the district we are located in. And that the levels of pollutants have a small impact when the analysis is done in such general terms (whole NYC).

Secondly, its been seen the importance of each main pollutant with respect to the number of asthma hospitalizations. Thus, it allows us to define an average pollution level, which is basically a descriptive mesure that combines the values of the four main pollutants in just one variable, simplifying in someway the  plots and the analysis. 

$$ Avg pollution = 1.55·NO2 + 0.70·PM2.5 + 0.99·O3 + 0.77·SO2 $$

where each pollutant vector has been normalized between 0 and 1:

$$ zi = (xi – min(x)) / (max(x) – min(x)) $$

<iframe src="feature_importance.html" height="600" width="1000"></iframe>

The main conclusion from this step is that the analysis has to be split between geographical areas. Thus, we decide as a first step to study asthma vs pollution per borough.

## Pollution per Borough. The strange case of Manhattan

<iframe src="scatter_borough.html" height="500" width="1600"></iframe>

## More money = Better healthcare? When the trendline highly varies depending on the district we are located.
Something really interesting can be observed here, and is the fact that really different regression trendlines can be observed depending on the neighbourhood. While in the Bronx the number of asthma hospitalizations strongly increases as the levels of pollution increase, in Manhattan happens exactly the opposite.

Bronx, Brookykn and Queens district seem to show the expected behaviour. As levels of pollution increase, air becomes more polluted, and so the number of asthma hospitalizations increases. However, why does the number of hospitalizations decrease in Manhattan as the levels of air pollution increase?

Different hypothesis appear here. Is it because in the more polluted areas of Manhattan, there is less space for hospitals in which you can treat asthma cases? Or is it because healtcare and quality of life is basically better in Mantattan?

Is it hard to believe that the first hypothesis might be the cause, specially becuase if we look at the more polluted ares of Manhattan we can find hospitals such as the Metropolitan [[5]](https://www.nychealthandhospitals.org/metropolitan/about-us/), which have a Children’s Asthma Program or Bellevue [[6]](https://www.nychealthandhospitals.org/bellevue/health-care-services/childrens-health/) which provides multidisciplinary care for children and adolescents with asthma.

Thus, it seems that these differences are due to the fact that the quality of life and the healthcare services might be better in Manhattan. If we go to check the Median Household Income on 2017 in NYC, we observe that the Bronx has the lowest value with a Median Household Income of 37.397 \\$ , while Manhattan has a value up to 85.071 \\$.

<iframe src="mahattan_districts.html" height="500" width="1600"></iframe>

Two observations can be extracted from the Scatter plot above. First, that definitely a negative correlation exists in Manhattan between the levels of pollutants and the number of asthma hospitalizations. Second, that something weird with the colors, right? Let's dig deep into that:

<iframe src="proportion_manhattan.html" height="500" width="1600"></iframe>

## District map
<iframe src="map.html" height="1150" width="1600"></iframe>
