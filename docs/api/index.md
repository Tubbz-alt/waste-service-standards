
# Waste Services API


## Introduction
This API offers a core set of resources and operations for interacting with local council waste and recycling services.


## ESD Standards
The [ESD Standards](http://standards.esd.org.uk) define all the categories of services that local authorities typically provide. These will be referenced via URL from the Services API, to allow individual council instances of a service to be matched to common service definitions.






## Services


---
Get a list of waste services

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/services</span>
</div>





**Response**
```
[
  {
    "id": 1,
    "name": "Recycling service",
    "frequency": "weekly",
    "esd_url": "http://id.esd.org.uk/service/524",
    "description": "Please put your recycling box on the street."
  },
  {
    "id": 2,
    "name": "Refuse",
    "frequency": "weekly",
    "esd_url": "http://id.esd.org.uk/service/525",
    "description": "Black bins."
  }
]
```









---
Get a single service

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/services/{serviceId}</span>
</div>





**Response**
```
{
  "id": 1,
  "name": "Recycling service",
  "frequency": "weekly",
  "esd_url": "http://id.esd.org.uk/service/1130",
  "description": "Please put your recycling box on the street."
}
```








## Events


---
Get a list of events

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/events</span>
</div>


**Query parameters**

Name | Type | Description
-----|------|------------
<tt>page</tt> | number | 
<tt>uprn</tt> | string | Limit results to those related to the property with this UPRN.
<tt>usrn</tt> | string | Limit results to those related to the street with this USRN.
<tt>type</tt> | string | Limit results to those with a matching type, e.g. "Not presented".
<tt>start_date</tt> | date | Limit results to those created on or after this start date.
<tt>end_date</tt> | date | Limit results to those created before this end date.
<tt>round</tt> | string | Limit results to those recorded against this round.





**Response**
```
[
  {
    "event_type": "Not presented",
    "date_created": "2014-05-23T20:00",
    "uprn": "123456789012",
    "usrn": "123456789012",
    "image": "http://example.com/images/123.png",
    "geo": {
      "@type": "GeoCoordinates",
      "latitude": "40.75",
      "longitude": "73.98"
    }
  },
  {
    "event_type": "Too heavy",
    "date_created": "2014-05-23T20:00",
    "uprn": "123456789012",
    "usrn": "123456789012",
    "image": "http://example.com/images/123.png",
    "geo": {
      "@type": "GeoCoordinates",
      "latitude": "45.75",
      "longitude": "53.98"
    }
  }
]
```









---
Get a single event

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/events/{eventId}</span>
</div>





**Response**
```
{
  "@id": "/api/events/1",
  "type": "Not presented",
  "date_created": "2014-05-23T20:00",
  "uprn": "123456789012",
  "usrn": "123456789012",
  "image": "http://example.com/images/123.png",
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "40.75",
    "longitude": "73.98"
  },
  "round": "/rounds/123"
}
```








## Rounds


---
Get a list of rounds

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/rounds</span>
</div>





**Response**
```
{}
```









---
Get a single round

<div class="api-call">
  <span class="rest-method get">get</span>
  <span>/rounds/{roundId}</span>
</div>





**Response**
```
{
  "@id": "/rounds/456",
  "date": "",
  "plan": {
    "id": "",
    "start_date": "",
    "rrule": "",
    "containers": "/api/containers?round_plan=1"
  },
  "events": "/api/events?round=456"
}
```






