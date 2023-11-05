# UN-Datathon-2023

The climate is changing.  

Decade after decade, global temperatures rise, and the effects are seen across the world.
2023 was an unprecedented year for Canadian wild fires, with over 18 million hectares of forest burned compared to less than 2 million in 2022.
(https://en.wikipedia.org/wiki/2023_Canadian_wildfires#/media/File:1983-_Canada_wildfires_-_area_burned_annually.svg)

In the mid 20th century, forest fires were running rampant across canada, with over 12,000 individual fires being ignited (and recorded) in 1989.
![image](https://github.com/liamhn/UN-Datathon-2023/assets/19610597/0712ae9d-841e-4e57-81da-beab5c07bb64)

In the late 1980s, the Canadian government developed and began implementing the Fire Weather Index (FWI).
The FWI is a fire risk system based on four weather measurements: temperature, humidity, precipitation, and wind speed.
A complex mathematical equation is used to compute the fire risk based on these measurements.
The original paper describing this system was published in 1987 and can be accessed at: https://web.archive.org/web/20180103192255/https://cfs.nrcan.gc.ca/publications?id=19927

Since the introduction of the FWI in the late 1980s, while the severity of fires continues to increase, the total number of fires has been in steady decline.
Of course, fire severity is heavily influenced by global climate change, but the number of ignited fires can be immediately reduced by day-to-day changes in human activity. 
The FWI informs policy choices such as fire bans, and other measures and regulations to control human.
The effectiveness of the FWI is well demonstrated by the steady decline in the number of fires since it's development and implementaton.
![image](https://github.com/liamhn/UN-Datathon-2023/assets/19610597/5c046037-bd85-4206-9888-bf1ca7adca71)



But what can be done in the absence of high resolution weather data?
Historically, weather measurements have been performed at "weather stations" scattered across Canada.
This infrastructure is expensive, requiring equipment, building and transportation infratruction, and human labour.
Simply put, this type of investment is simply not globally available on a massive scale.
But as global temperatures rise, and fire risks increase, it is more important than ever to provide real-time risk assessments to influence policy choices and human behaviour.
UN projections suggest that catastrophic wildfire events will uncrease by up to 50% by the end of the century:
![image](https://github.com/liamhn/UN-Datathon-2023/assets/19610597/8b864dbd-dd88-4873-ad73-1b6e7d0621d1)
( from https://www.unep.org/resources/report/spreading-wildfire-rising-threat-extraordinary-landscape-fires?gclid=Cj0KCQjw-pyqBhDmARIsAKd9XINX5gsTcfdWUoYEHL9I3OSm3jWVJeTUOw13taQKiGDoRHF89xPFYVYaAsdBEALw_wcB ).


To combat the rise of catastrophic wildfires, innovative uses of data, software, and predictive modelling will be indispensible.
To this end, we present  "Only ML Can Stop Wildfires"
![image](https://github.com/liamhn/UN-Datathon-2023/assets/19610597/4b647242-3f53-4be8-973c-9c1da65c4f22)

Here, we construct an alternative model to the FWI, that can determine forest fire risk using less data than is required by the FWI.
The idea is to construct a proof of concept idea that allows for the prediction of wild fire risk in remote or low-income regions that may not have access to the expensive equipment and infrastructure required to use a system like the FWI. 
The central idea is that less data is less expensive.
We construct a model that can predict fire risk using only 3 of the four weather measurements that are needed for the FWI predictions, thereby reducing the cost of fire risk prediction.

The model architecture is a simple fully connected feed forward deeep neural network (see ML_FWI_REPLACEMENT notebooks).
To train the model, we use weather data from across 71 different weather stations in ontario that provide historical data for wind speed, temperature, humidity, and precipitation. The data can be accessed at https://climate-change.canada.ca/climate-data/#/daily-climate-data
and a small subset of it is provided in the 'climate_daily_intario_since_2000-reduced' folder. The features we trained on were subsets of the four weather measurements (for example, one model predicts looks only at humidity, precipiptation, and wind speed, and omits temperature), and the labels we trained on were the true FWI computed using the FWI source (in the FWISOurce notebook), which was taken from the canadian government website: https://publications.gc.ca/collections/collection_2016/rncan-nrcan/Fo133-1-424-eng.pdf

Due to time limitations, we trained only on data from Ontario that was recorded since the year 2000.
In principal, this system should be trained on all worldwide data dating back as far asw possible to maximize the accuracy of the predictions.
In spite of our data limitations, we were able to achieve reasonable agreement between our reduced-data predictions and the true values of the FWI:
![image](https://github.com/liamhn/UN-Datathon-2023/assets/19610597/99b86a69-8e8a-4cb9-b15c-2e727ea9e7f0)

Of course, we have extremely good agreement in the case where we trained on all four weather parameters, and worse agreement when only 3 are used.
However, the reduced-feature models still provide reasonable predictions with less data, and therefore with lower acquisition cost.
