
## Purpose

The purpose of this document is to help a beginner level developer/student to add weather API to a website. This API documentation includes a sample request, response in JSON format with a detailed description of the response attributes.

# Introduction

The weather API is a sample API documented to add weather information to the website.


# Weather API

Weather API provides information about the weather conditions like temperature, winds, cloudiness, etc., for a specific location.


## Mandatory-Headers

Key|Value
-------|-----
Authentication |API Key
Content-Type| application/json


## EndPoints
`Get`/ weather

Retrieves the weather conditions for a specific location.

# Parameters

## Path Parameters

Path Parameter | Description
--------------|----------------
{weather}|The details of the weather conditions for a specific location using coordinates.

## Querystring Parameters

Query string Parameter| Description| Required/Optional
----------|-------|-----|
`Zip`|The Zip code of the city.|Required|
`units`|Units to measure the temperature. Imperial: Fahrenheit ; Kevin, Metric: Celsius  |Optional
`Days`|The number of days.|Required
`Lat & Long`| Coordinates (Latitude and Longitude) of the location.|Optional




## Sample-Request

`https://api.openweathermap.org/data/2.5/weather?Zip=95129&units=imperial&appid=APIKEY&days=5&lat=37.2948374&lon=-122.022296`

> Note : In the above sample request, replace APIKEY with your actual API KEY.

**In cURL**

`curl --location --request GET 'https://api.openweathermap.org/data/2.5/weather?Zip=95129&units=imperial&appid=APIKEY&days=5&lat=37.2948374&lon=-122.022296'`


## Sample Response

The following is a sample response for the above request:

> Note : Units in this example are Imperial:Fahrenheit.

```
{
    "coord": {
        "lon": -122.02,
        "lat": 37.29
    },
    "weather": [
        {
            "id": 803,
            "main": "Clouds",
            "description": "broken clouds",
            "icon": "04d"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 75.79,
        "feels_like": 64.72,
        "temp_min": 73,
        "temp_max": 78.01,
        "pressure": 1015,
        "humidity": 47
    },
    "visibility": 16093,
    "wind": {
        "speed": 21.92,
        "deg": 330
    },
    "clouds": {
        "all": 75
    },
    "dt": 1592180828,
    "sys": {
        "type": 1,
        "id": 5845,
        "country": "US",
        "sunrise": 1592138828,
        "sunset": 1592191798
    },
    "timezone": -25200,
    "id": 5393485,
    "name": "Saratoga",
    "cod": 200
}
```


## Response Attributes

Following table details each response attribute:

Attribute |Description|
----------|------|
`coord`|The coordinates of the geolocation. Refer **1.1 coord** for details.
`weather`| An object containing details of more weather condition codes. Refer **1.2 weather** for details.
`base`| An internal parameter.
`main`|An object containing temperature details. Refer **1.3 main** for details.
`visibility`| In meteorology, visibility is a measure of the distance at which an object or light can be clearly discerned. Units are Meters.
`wind`|An object containing wind parameters. Refer **1.4 wind** for details.
`clouds`|Determines the cloudiness. Refer **1.5 Clouds** for details.
`dt`|Time of data calculation (UNIX, UTC).
`sys`| An internal parameter.
`timezone`|Shift in seconds from UTC (Universal Time Coordinated).
`id`|ID of the city.
`name`|Name of the city.
`cod`|API success/failure code.

#### Following are the objects :

**1.1 Coord**

Attribute|Data type |Description|
----------|---------|------|
`lon`|Double |Longitude of the location.
`lat`|Double |Latitude of the location.

**1.2 weather**

 Attribute|Data type |Description|
----------|---------|-----------|
`id`|Integer|A weather condition ID.
`main`|String| Group of weather parameters.
`description` |String|Description of the weather condition in the group.
`icon`| String|A weather icon ID.


**1.3 main**

Attribute| Data Type|Description|
----------|---------|-------
`temp`|Double|Temperature. Units to measure : Metric -> Celsius and Imperial -> Fahrenheit.
`feels_like`|Double|A human felt temperature. Units to measure : Metric -> Celsius, Imperial -> Fahrenheit.
`temp_min`| Double |Lowest calculated temperature of the day. Units to measure : Kevin, Metric -> Celsius, Imperial -> Fahrenheit
`temp_max`| Double | Highest calculated temperature of the day. Units to measure : Kevin, Metric -> Celsius, Imperial -> Fahrenheit,
`pressure`| Double| Atmospheric pressure (assuming the location is at Sea-Level).
`humidity`|Double|Percentage of humidity.|

**1.4 wind**

Attribute | Data type |Description
----------|-----------|------|
`speed`|Double|Speed of the wind. Units to measure : Metric -> meter/second, Imperial -> miles/hour
`deg`|Double|The direction of the wind. Units to measure: Degrees.

**1.5 Clouds**

Attribute | Data type|Description
----------|---------|-----|
`all`|Integer| Indicates the percentage of cloudiness.


**1.6 sys**

Attribute| Data type |Description|
----------|---------|-----|
`type`|Integer |Type of a sys parameter (Internal).
`id`|Integer|Type of a sys parameter (Internal).
`country`|String|Name of the country. Each country has a specific code, e.g., United States-US, Japan-JP.
`sunrise`|Integer |Time of the sunrise. Units to measure: UNIX, UTC
`sunset`|Integer |Time of the sunset. Units to measure: UNIX, UTC
