# Surf Up
Challenge Module 9 - Surf_Up_Challenge

## Overview of Project

### Background

> W. Avy wants an ideal surfing and ice cream weather in Oahu, so he has supplied with the data to be analyzed for it

### Purpose

> W. Avy wants more information about temperature trends before opening the surf shop, in order to determine if the surf
> and ices creamshop business is sustainable year-round he desires to analyze the following months for Oahu:

- *`June`*
- *`December`*

## Results

- June has more data that can be used for the analysis than december.
- The mean temperature for June is around 74.94 degrees and December is 71.04, so we can gather
  that there is no a great change in temperature between both months. 
- June data are more closed to the mean, since its standard deviation is lower than December 


### June vs December data statistics

|           | June | December |
| :------------ |:---------------:| :-----:|
| Temperature statistics | ![June Temperature Statistics](https://user-images.githubusercontent.com/86028032/131235084-4826e6a3-3ff3-4936-ab7b-14d3497ff16b.PNG) | ![December Temperature Statistics](https://user-images.githubusercontent.com/86028032/131235098-9d57aca8-f08d-4a4f-8341-b92bf93a39ad.PNG) |

## Summary

The surf and icess creamshop business is sustainable year-round, we can gather this from the analysis from both
months in which the mean temperature is betweeen 71 - 74 degrees, the data analysis is significant because the 
provided information is beyond 1500 data and most of the data is closed to the mean.

- Query for getting the *lowest temperature recorded*, *highest temperature recorded*, and *average temperature*
  for the most active station *USC00519281*

```
  session.query(func.min(Measurement.tobs), func.max(Measurement.tobs), func.avg(Measurement.tobs)).\
  filter(Measurement.station == 'USC00519281').all()*
```

- Query for getting the temperatures for the station *USC00519281* for the desired month

```
  results = session.query(Measurement.tobs).\
  filter(Measurement.station == 'USC00519281').\
  filter(func.strftime("%m", Measurement.date) == month_str).all()
  df = pd.DataFrame(results, columns=['tobs'])
  print(df)
```
