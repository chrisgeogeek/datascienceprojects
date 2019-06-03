The Ontario Energy Project by Christopher Mills
===============================================

This project was undertaken to explore energy use in the province of Ontario and attempt prediction using machine learning models.
The logical order of these notebooks is exploration.ipynb, followed by feature_engineering_daily.ipynb and then data_modeling.ipynb.

Energy demand and hourly price data were collected from the Independent Electricity System Operator (IESO) website's Data Directory.
All of this data, and more, can be found at http://www.ieso.ca/en/Power-Data/Data-Directory.
All data examined in the exploration.ipynb notebook comes from this source.

Both population data and weather data are introduced in the feature_engineering_daily.ipynb notebook.
The metropolitan area population figures came from the Statistics Canada webpage at
https://www12.statcan.gc.ca/census-recensement/2016/dp-pd/hlt-fst/pd-pl/Table.cfm?Lang=Eng&T=201&SR=1&S=3&O=D&RPP=50&PR=35.
The selected areas account for about 85% of the province's population, with the remainder scattered across areas with populations of 
under 90 thousand. I was unable to find weather stations adequately close to these smaller population centers. The original intention 
was to somehow weight the weather station data according to local population size, which is why I bothered engineering a population value 
for each year for each area. However, after doing that, I decided to instead let the machine learning model fitting determine appropriate 
weights, which would hopefully reflect the size of the population of the respective areas. For example, I hoped the models would place 
much greater emphasis on Toronto weather features than Ottawa weather features, because Toronto has about 6 times the population of 
Ottawa. As observed and discussed in data_modeling.ipynb, this turned out not to be the case.

The weather data files loaded in feature_engineering_daily.ipynbwere found and downloaded using the Government of Canada website 
Historical Data search tool at http://climate.weather.gc.ca/historical_data/search_historic_data_e.html. The 17 weather stations were 
selected for their proximity to the largest population centers and their availability of daily data in the 2009-2018 timespan that I 
settled on. A larger timespan would be desirable, but would have reduced the number of weather stations with adequate data.

The only data used in the data_modeling.ipynb notebook is the engineered.csv file created in feature_engineering_daily.ipynb.
