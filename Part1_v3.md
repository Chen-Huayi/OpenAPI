# Manitoba Lake Inquiry
## Description  
The Lake Manitoba API allows researchers or developers to find statistics about any lake within the province of Manitoba. This API can provide a series of data, including accurately reported temperatures, depths, Ph, and water levels since the year 2000. All statistics are recorded daily from all lakes in Manitoba, through sampling and measurement reports.

## Endpoints and Parameters

### Endpoint: __/lake__
#### List of query parameters:  

|Name|Type|Input Format |Description|Request|
| ---- | ---- | ---- | ---|---- |
|lat |float | -90.0 to 90.0 | The latitude coordinate of the lake| **Required**|
|lon |float | -180.0 to 180.0 | The longitude coordinate of the lake | **Required**|
|date |string |MM-DD-YYYY | Date of measurement of lake body | Optional|
|system |integer| 0 or 1 | (Default value: 1) 1 for Metric system (Celsius/Meters), 0 for Imperial (Fahrenheit/Feet) |Optional|

### Endpoint: __/lake/{lakeName}__
#### List of query parameters:  
|Name|Type|Input Format |Description|Request|
| ---- | ---- | ---- | --- |---- |
|lakeName **(path parameter)** |string|name |The full name of lake| **Required**|
|date |string |MM-DD-YYYY | Date of measurement of lake body | Optional|
|system |integer| 0 or 1 | (Default value: 1) 1 for Metric system (Celsius/Meters), 0 for Imperial (Fahrenheit/Feet) |Optional|

#### Return parameters:

|Name|Type|Description|
| ---- | ---- | ---- |
|id|string|ID of specific marine body
|name|string|Returning the name of the body of lake
|lat|float point|Latitude of the lake you are getting information for
|lon|float point|Longitude of the lake you are getting information for
|water level |float point|Average level of lake relative to itself
|depth |integer|Average depth of the lake
|temperature |integer|Average temperature of the lake body
|altitude |integer|Average altitude of the body of lake
|pH value |float point|Average pH value of lake body
|msg|string|Success response

### Request format:
```
lake?lat={value}&lon={value}&date=MM-DD-YYYY&system={0or1}
```
**Latitude** and **longitude** are the coordinates for the lake that you would like information for.
```
lake/{lakeName}?date=MM-DD-YYYY&system={0or1}
```
**lakeName** is the name of the lake you are getting information for


## Resources (Formatted as JSON)  

A response is received as:
##  
```
[
  {
    "results": {
      "id": "CA6505_1",
      "name": "Lake Manitoba",
      "lat": -83.01,
      "long": 111.09,
      "water level": 10.01,
      "depth": 13,
      "temperature": 15,
      "altitude": 231,
      "pH value": 7.48
    },
    "msg": "The query is successful!"
  }
]
```

## Sample Request and Response
Examples:

To receive statistics about Lake Manitoba on November 19th, 2000:
```
lake/LakeManitoba?date=11-19-2000
```
Returns:
```
[{"results": {"id": "CA6505_1","name": "Lake Manitoba","lat": -83.01,"long": 111.09,"water level": 10.01,"depth": 13,"temperature": 15,"altitude": 231,"pH value": 7.48},"msg": "The query is successful!"}]
```
Modifying the parameters into the imperial system or using lake endpoint with latitude and longitude coordinates:
```
1. lake/LakeManitoba?date=11-19-2000&system=0
2. lake?lat=54.668079&long=-101.542809&date=11-19-2000&system=0
```
Both queries return:
```
[{"results": {"id": "CA6505_1","name": "Lake Manitoba","lat": 54.668079,"long": -101.542809,"water level": 2.23,"depth": 33,"temperature": 63,"altitude": 758,"pH value": 7.48},"msg": "The query is successful!"}]
```
