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
1. A
2. B
3. C


### Summary ###
Summary of Results

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
