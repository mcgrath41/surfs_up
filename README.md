# Surfs Up

## Project Overview

### Purpose
Compile and analyze temperature trends for the months of June & December to determine if W. Avy's surf and ice cream shop business is sustainable year-round.

### Resources ###
- Data Source: hawaii.sqlite
- Software: Python 3.9, Visual Studio Code 1.60.1, Jupyter Notebook 6.3.0


## Analysis ##

### Results ###
The differences in weather between June and December are as follows:
1. On the average day, it is 3.9 degrees warmer in June (mean temperature = 74.9) than December (mean temperature = 71.0).  
2. The minimum temperature recorded in June (64) is 8 degrees higher than the minimum temperature recorded in December (56); however, the maximum temperature recorded in June (85) is only 2 degrees higher than the maximum temperature recorded in December (83). 
3. The temperature data for both June and December are symmetric (i.e. not skewed left or right) given that the mean vs. median temperatures for each month are nearly the same. Therefore, we can use the mean +/- two (2) standard deviations to get a range of 95% of the data. For December, this range is 63.5 - 78.5 degrees.  For June, this range is 68.4 - 81.5 degrees. 


### Summary ###
The statsitical data suggests that while it does get colder on average in December, the majority of days will be just as warm as a typical day in June. While we have a good understanding of the temperatures in June & December, further analysis is needed on the weather data before a final answer can be given on year-round sustainability. The obvious next step is to compare preciptation trends, and the historical data can be pulled from each month via the following queries:

Two queries
```
jun_rain_list = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6)
jun_rain_df = pd.DataFrame(jun_rain_list, columns=['date', 'precipitation'])
jun_rain_df.set_index(jun_rain_df['date'], inplace=True)
jun_rain_df = jun_rain_df.sort_index()
print(jun_rain_df.to_string(index=False))
jun_rain_df.plot(rot=90)
```


```
dec_rain_list = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12)
dec_rain_df = pd.DataFrame(dec_rain_list, columns=['date', 'precipitation'])
dec_rain_df.set_index(dec_rain_df['date'], inplace=True)
dec_rain_df = dec_rain_df.sort_index()
print(dec_rain_df.to_string(index=False))
dec_rain_df.plot(rot=90)
```
