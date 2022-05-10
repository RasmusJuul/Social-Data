# The Air of New York City:<br> An Analysis of Pollution and Asthma
It is common knoweldge that air pollution is a contributing factor of respiratory diseases. And among all the broad types of respiratory diseases that exists, specifically asthma. Asthma is a chronic respiratory disease characterized by variable airflow obstruction, bronchial hyperresponsiveness, and airway inflammation. [[1]](https://pubmed.ncbi.nlm.nih.gov/32867076/) Researchers have long linked asthma with exposure to air pollution, which can make asthma symptoms worse and trigger asthma attacks. Moreover, it is estimated six million children in the United States with asthma are especially vulnerable to air pollution. [[2]](https://www.epa.gov/sciencematters/links-between-air-pollution-and-childhood-asthma#:~:text=Researchers%20have%20long%20linked%20asthma,worse%20and%20trigger%20asthma%20attacks). And not only vulnerable once they have the disease. It has been also proved that exposure to main air pollutants such as NO2, CO, and PM2.5 is linked to regional DNA methylation differences in asthma. [[3]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5756438/pdf/13148_2017_Article_433.pdf)

The aim of this website is to dig deeper into this relation between air pollution and asthma. To do so, NYC air pollution data will be used and combined with asthma hospitalizations data for children. Is there any clear correlation between air pollution and the number of asthma hospitalizations? If so, which are the air pollutants that are more correlated? How do these values vary between the different neighbourhoods? Where is more urgent to reduce the emissions of hazardous air pollutants? Is it possible to predict which is gonna be the number of asthma hospitalizations in order to prepare these hospitals that are gonna suffer more for such big workloads? 

<iframe src="evolution.html" height="400" width="1100"></iframe>

It can be clearly seen how there is a tendence in decrease in both the number of asthma hospitalizations and the levels of emission of the main pollutants. With the exception of O3, the levels of PM2.5, NO2 and SO2 have been significanlty reduced in the last decade, which evidence that sustainability policies were put into practice. Air quality levels registred during the 2000-2010 decade and their impact on population's health raised the attention of key decision makers and the public which lead to polices aming to improve local air quality, reduce greenhouse gas emissions and revert the situation that air pollution was taking. [[4]](https://www.healthypeople.gov/2020/healthy-people-in-action/story/new-york-city-air-quality-programs-reduce-harmful-air-pollutants)

Once seen how the tendency that both asthma cases and air pollutants are following, the next question that arise is: Is it possible to build a model that relates the number of asthma hospitalizations with the different levels of air pollutants? Which is the impact that each district has?
## Machine learning model to predict the level of asthma hospitalizations

We've trained a machine learning model, namely a random forest regressor, to predict the number of hospitalizations from the measured amounts of polution. The algorithm was able to accurately model the dataset and it is clear that there is a distinct relationship between polutants and asthma cases. The model can tell us which parts of the data is more influential on the number asthma hospitalization and in this case it is very dependent on which district we are in. This is interesting since it might hint that social and economic factors are very influential on asthma hospitalization. It can also be observed that every polutant measured have an effect on the number of hospitalizations and that the effect is different for each polutant. The model was so effective at predicting the dataset that we can conclude that most of the important features for predicting asthma cases is somewhat present in our dataset, albeit having to analyse why the district is so important (which may be a very deep rabbit hole).

<iframe src="feature_importance.html" height="550" width="1100"></iframe>

The main conclusion from this step is that the analysis has to be split between geographical areas. Thus, we decide as a first step to study asthma vs pollution per borough.

## Study of pollution per Borough. When the trendline highly varies depending on the district we are located.
<iframe src="scatter_borough.html" height="525" width="1600"></iframe>
Something really interesting can be observed here, and is the fact that really different regression trendlines can be observed depending on the neighbourhood. While in the Bronx the number of asthma hospitalizations strongly increases as the levels of pollution increase, in Manhattan happens exactly the opposite.

Bronx, Brooklyn and Queens district seem to show the expected behaviour. As levels of pollution increase, air becomes more polluted, and so the number of asthma hospitalizations increases. However, why does the number of hospitalizations decrease in Manhattan as the levels of air pollution increase?

To answer this question we looked into a variable we had not yet considered the quality of life based on income. Checking the Median Household Income from 2017 in NYC, we observe that the Bronx (highest number of hospitalizations) has the lowest value with a median income of $37.397 , while Manhattan (lowest number of hospitalizations) has a median income of $85.071.

## The strange case of Manhattan. More money = Better healthcare? 
<iframe src="manhattan_districts.html" height="500" width="1600"></iframe>
In the previous plot it has been clearly seen how the trend between asthma and pollution was the oposite than the one found in the other districts. This made us realize that a zoom-in was needed in order to find possible explanations on way this was happening. How is it possible that in these Manhattan districts with higher levels of pollution there are less asthma cases? And we found it. If we add the district feature in the visualization, we can easily observe some clustering between the dots: high values of asthma mainly correspond to 301,302 and 303 (upper manhattan) while low values corresponds to the others. Why this big geographical difference?

So with the knowledge that there is a big difference in median income and number of hospitalizations between Manhattan and the Bronx, we looked further into the impact of median income on the number of asthma hospitalizations? To answer this question a new visualization has been made.
<iframe src="proportion_manhattan.html" height="500" width="1600"></iframe>
In the above graphic it is clear that for each district when median income is low the number of asthma hospitalizations are high, and pollution seemingly have little effect compared to income. And that the low income districts of Manhattan has slightly lower amounts of pollution, which is why we saw the reverse correlation between pollution and hospitalizations in Manhattan.

## District map
To further investigate the difference in districts a visualization of the asthma hospitalizations, pollutants, and median income for each district was made:
<iframe src="map.html" height="1150" width="1600"></iframe>
In the district map we see an overall decrease in pollutants (other than O3), and a decrease in the amount of asthma hospitalizations. It is also easy to see when swiching between the median income overlay and the asthma hospitalization overlay that there is an inverse correlation between the two. While, we have shown that the amount of hospitalizations is highly dependent on the median income of the district, this median income does not change much over the 8 year time period. So we observe a decrease in both overall pollution and asthma hospitalizations independent of median income over the time period, which is what we would expect to see considering the well established connection between air pollution and asthma.

So the main takeaway from this analysis is while air pollution plays a role in whether or not you'll end up hospitalized for asthma, the biggest contributing factor is seemingly your income, which is most likely just an indicator of some other underlying cause, like how much time/money you have for preventive care etc. which is harder to measure.


# Explainer notebook:
[Click here to access the notebook](https://nbviewer.org/github/RasmusJuul/Social-Data/blob/main/Explainer%20Notebook.ipynb)
