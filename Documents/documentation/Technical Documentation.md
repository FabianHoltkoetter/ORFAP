# Technical Documentation
## GUI
## Backend

The Backend holds the whole data and offers an API for it. The following section will describe this API. For every Entity on the database the necessary  endpoints
(Path) will be shown with the depending HTTP Methods to call.

Base URL: `http://10.28.2.166/api`

### Airline
#### Entity Schema
| Property  | Type   | Required  |
|-----------|--------|-----------|
| id        | String | yes       |
| name      | String | yes       |

#### Path `/airlines`

##### Http Methods
###### ***`Get`***

**Description:** Get all saved airlines.

**Response Example:**
```
Code 200
```
```
[
  {
    "id": "213123",
    "name": "Lufthansa"
  },
  {
    "id": "12312",
    "name": "AirBerlin"
  }
]
```
###### ***`Post`***

**Description:** Save an airline.

**Request Example:**
Header: Content-Type application/json
```
{
  "id": "213123",
  "name": "Lufthansa"
}
```

**Response Example:**
```
Code 201
```
```
{
  "id": "213123",
  "name": "Lufthansa"
}
```
#### Path `/airlines/{id}`

##### Http Methods
###### ***`Get`***

**Description:** Get an specific airline with the given `id`.

**Response Example:**
```
Code 200
```
```
{
    "id": "213123",
    "name": "Lufthansa"
}
```
###### ***`Put`***

**Description:** Update an specific airline with the given `id`.

**Request Example:**
Header: Content-Type application/json
```
{
  "id": "213123",
  "name": "Lufthansa"
}
```

**Response Example:**
```
Code 200
```
```
{
  "id": "213123",
  "name": "Lufthansa"
}
```
###### ***`Delete`***

**Description:** Deletes an specific airline with the given `id`.

**Response Example:**
```
Code 204
```
### Market
#### Entity Schema
| Property  | Type   | Required  |
|-----------|--------|-----------|
| id        | String | yes       |
| name      | String | yes       |

#### Path `/markets`

##### Http Methods
###### ***`Get`***

**Description:** Get all saved markets.

**Response Example:**
```
Code 200
```
```
[
  {
    "id": "213123",
    "name": "New York"
  },
  {
    "id": "12312",
    "name": "Colorado"
  }
]
```
###### ***`Post`***

**Description:** Save a market.

**Request Example:**
Header: Content-Type application/json
```
{
  "id": "213123",
  "name": "New York"
}
```

**Response Example:**
```
Code 201
```
```
{
  "id": "213123",
  "name": "New York"
}
```
#### Path `/markets/{id}`

##### Http Methods
###### ***`Get`***

**Description:** Get a specific market with the given `id`.

**Response Example:**
```
Code 200
```
```
{
    "id": "213123",
    "name": "New York"
}
```
###### ***`Put`***

**Description:** Update a specific market with the given `id`.

**Request Example:**
Header: Content-Type application/json
```
{
  "id": "213123",
  "name": "New York"
}
```

**Response Example:**
```
Code 200
```
```
{
  "id": "213123",
  "name": "New York"
}
```
###### ***`Delete`***

**Description:** Deletes a specific market with the given `id`.

**Response Example:**
```
Code 204
```
### Route
#### Entity Schema
| Property      | Type         | Required  |
|----------------|-------------|-----------|
| id             | String      | no        |
| date           | Date/String | yes       |
| delays         | double      | no        |
| cancelled      | double      | no        |
| passengerCount | double      | no        |
| flightCount    | double      | no        |
| airline        | Link        | yes       |
| source         | Link        | yes       |
| destination    | Link        | yes       |

#### Path `/routes`

##### Http Methods
###### ***`Get`***

**Description:** Get all saved routes.

**Response Example:**
```
Code 200
```
```
[
  {
    "date": "2015-12-01",
    "delays": 10,
    "cancelled": 0,
    "passengerCount": 130,
    "flightCount": 1,
    "airline": "http://10.28.2.166/api/airlines/123123",
    "source": "http://10.28.2.166/api/markets/23423424",
    "destination": "http://10.28.2.166/api/markets/1231231"
  },
  {
    "date": "2015-10-20",
    "delays": 15,
    "cancelled": 0,
    "passengerCount": 120,
    "flightCount": 1,
    "airline": "http://10.28.2.166/api/airlines/123123",
    "source": "http://10.28.2.166/api/markets/23423424",
    "destination": "http://10.28.2.166/api/markets/1231231"
  }
]
```
###### ***`Post`***

**Description:** Save a route.

**Request Example:**
Header: Content-Type application/json
```
{
  "date": "2015-12-01",
  "delays": 10,
  "cancelled": 0,
  "passengerCount": 130,
  "flightCount": 1,
  "airline": "http://10.28.2.166/api/airlines/123123",
  "source": "http://10.28.2.166/api/markets/23423424",
  "destination": "http://10.28.2.166/api/markets/1231231"
}
```

**Response Example:**
```
Code 201
```
```
{
  "date": "2015-12-01",
  "delays": 10,
  "cancelled": 0,
  "passengerCount": 130,
  "flightCount": 1,
  "airline": "http://10.28.2.166/api/airlines/123123",
  "source": "http://10.28.2.166/api/markets/23423424",
  "destination": "http://10.28.2.166/api/markets/1231231"
}
```
#### Path `/routes/saveAll`

##### Http Methods
###### ***`Post`***

**Description:** Saves a list of routes.

**Request Example:**
Header: Content-Type application/json
```
[
  {
    "date": "2015-12-01",
    "delays": 10,
    "cancelled": 0,
    "passengerCount": 130,
    "flightCount": 1,
    "airline": "123123",
    "source": "23423424",
    "destination": "1231231"
  },
  {
    "date": "2015-10-20",
    "delays": 15,
    "cancelled": 0,
    "passengerCount": 120,
    "flightCount": 1,
    "airline": "123123",
    "source": "23423424",
    "destination": "1231231"
  }
]
```

**Response Example:**
```
Code 200
```
#### Path `/routes/search/isRouteInMonthOfYear`

##### Http Methods
###### ***`Get`***

**Description:** Determine if there are already routes saved for
the given month of year.

**Query**

* **date** Date to check with format: yyyy-MM

**Response Example:**
```
Code 200
```
```
true
```

#### Path `/routes/{id}`

##### Http Methods
###### ***`Get`***

**Description:** Get a specific route with the given `id`.

**Response Example:**
```
Code 200
```
```
{
  "date": "2015-12-01",
  "delays": 10,
  "cancelled": 0,
  "passengerCount": 130,
  "flightCount": 1,
  "airline": "http://10.28.2.166/api/airlines/123123",
  "source": "http://10.28.2.166/api/markets/23423424",
  "destination": "http://10.28.2.166/api/markets/1231231"
}
```
###### ***`Put`***

**Description:** Update a specific route with the given `id`.

**Request Example:**
Header: Content-Type application/json
```
{
  "date": "2015-12-01",
  "delays": 10,
  "cancelled": 0,
  "passengerCount": 130,
  "flightCount": 1,
  "airline": "http://10.28.2.166/api/airlines/123123",
  "source": "http://10.28.2.166/api/markets/23423424",
  "destination": "http://10.28.2.166/api/markets/1231231"
}
```

**Response Example:**
```
Code 200
```
```
{
  "date": "2015-12-01",
  "delays": 10,
  "cancelled": 0,
  "passengerCount": 130,
  "flightCount": 1,
  "airline": "http://10.28.2.166/api/airlines/123123",
  "source": "http://10.28.2.166/api/markets/23423424",
  "destination": "http://10.28.2.166/api/markets/1231231"
}
```
###### ***`Delete`***

**Description:** Deletes a specific route with the given `id`.

**Response Example:**
```
Code 204
```
#### Path `/routes/filter`

##### Http Methods
###### ***`Get`***

**Description:** Apply a given filter setting to the database and
provide preformatted data.

**Request Example:**
Header: Content-Type application/json
```
{
  "name": "Test-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-03-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```

**Response Example:**
```
Code 200
```
```
{
  "y": "FLIGHTS",
  "z": "TIME",
  "x": "January, February, March",
  "data":{
    "January": 20,
    "February": 15,
    "March": 21
  }
}
```

### Settings
#### Entity Schema
| Property  | Type        | Required |
|-----------|-------------|----------|
| id        | String      | no       |
| name      | String      | yes      |
| creator   | String      | yes      |
| shareable | boolean     | no       |
| rangeFrom | Date/String | no       |
| rangeTo   | Date/String | no       |
| filter    | Filter      | yes      |
| axis      | Axis        | yes      |

#### Path `/settings`

##### Http Methods
###### ***`Get`***

**Description:** Get all saved settings.

**Response Example:**
```
Code 200
```
```
[
  {
    "name": "Standard-View",
    "creator": "Hans",
    "shareable": true,
    "rangeFrom": "2015-01-01",
    "rangeTo": "2015-12-31",
    "filter": {
      "destinations": [
        "23123123","2313123123"
      ],
      "airlines": [
        "678678","6786786867"
      ],
      "timestep": "MONTH"
      },
    "axis": {
      "x": "TIME",
      "y": "FLIGHTS"
    }
  },
  {
    "name": "Extended-View",
    "creator": "Hans",
    "shareable": true,
    "rangeFrom": "2015-01-01",
    "rangeTo": "2015-01-31",
    "filter": {
      "destinations": [
        "23123123","2313123123"
      ],
      "airlines": [
        "678678","6786786867"
      ],
      "timestep": "DAY_OF_WEEK"
      },
    "axis": {
      "x": "DESTINATION",
      "y": "PASSENGERS"
    }
  }
]
```
###### ***`Post`***

**Description:** Save a setting.

**Request Example:**
Header: Content-Type application/json
```
{
  "name": "Standard-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-12-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```

**Response Example:**
```
Code 201
```
```
{
  "name": "Standard-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-12-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```
#### Path `/settings/{id}`

##### Http Methods
###### ***`Get`***

**Description:** Get a specific setting with the given `id`.

**Response Example:**
```
Code 200
```
```
{
  "name": "Standard-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-12-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```
###### ***`Put`***

**Description:** Update a specific setting with the given `id`.

**Request Example:**
Header: Content-Type application/json
```
{
  "name": "Standard-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-12-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```

**Response Example:**
```
Code 200
```
```
{
  "name": "Standard-View",
  "creator": "Hans",
  "shareable": true,
  "rangeFrom": "2015-01-01",
  "rangeTo": "2015-12-31",
  "filter": {
    "destinations": [
      "23123123","2313123123"
    ],
    "airlines": [
      "678678","6786786867"
    ],
    "timestep": "MONTH"
    },
  "axis": {
    "x": "TIME",
    "y": "FLIGHTS"
  }
}
```
###### ***`Delete`***

**Description:** Deletes a specific setting with the given `id`.

**Response Example:**
```
Code 204
```
#### Path `/settings/search/
findByNameContainingIgnoreCaseOrCreatorContainingIgnoreCase`

##### Http Methods
###### ***`Get`***

**Description:** Find settings by name or by creator name.

**Query**

* **name** Name of setting
* **creator** Name of creator

**Response Example:**
```
Code 200
```
```
[
  {
    "name": "Standard-View",
    "creator": "Hans",
    "shareable": true,
    "rangeFrom": "2015-01-01",
    "rangeTo": "2015-12-31",
    "filter": {
      "destinations": [
        "23123123","2313123123"
      ],
      "airlines": [
        "678678","6786786867"
      ],
      "timestep": "MONTH"
      },
    "axis": {
      "x": "TIME",
      "y": "FLIGHTS"
    }
  }
]
```
#### Path `/settings/search/
findByCreatorContainingIgnoreCaseOrShareableTrue`

##### Http Methods
###### ***`Get`***

**Description:** Find settings by creator name including all
public settings.

**Query**

* **creator** Name of creator

**Response Example:**
```
Code 200
```
```
[
  {
    "name": "Standard-View",
    "creator": "Hans",
    "shareable": true,
    "rangeFrom": "2015-01-01",
    "rangeTo": "2015-12-31",
    "filter": {
      "destinations": [
        "23123123","2313123123"
      ],
      "airlines": [
        "678678","6786786867"
      ],
      "timestep": "MONTH"
      },
    "axis": {
      "x": "TIME",
      "y": "FLIGHTS"
    }
  }
]
```





## Crawler
### Detailed listing of the proceedings of the crawling process
1. Start the crawler via a REST command, either by using the "Crawler"-Button in
 the GUI or by just sending the command to http://10.28.2.166/crawler.  
The command has the following syntax: http://\<serverIPAddress/crawler\>/crawlIntoBackend?year=\<year\>(&month=\<month\>)  
The year must be a number, so must the month. If just the year is provided, the full year will be crawled.  
Months can be given as discrete months or in ranges, e.g. 1-7.  
The part in () brackets is optional.  
2. The crawler now starts the crawling process. This process is divided in several steps.
3. The list of all airlines available is downloaded from the transtats server and they are saved in a hashmap.
Also all airlines already in the database are requested and saved into a set.
4. The list of all markets available is downloaded from the transtats server and they are saved in a hashmap.
Also all markets already in the database are requested and saved into a set.
5. The given year and month or months, are extracted and a loop is created, starting with the first given month, ending with the last given month.
6. The T100D database is queried for all routes originating in the NYC market, going to other markets in the US, in the first given month.
7. The route pipeline is created.
8. The zip-file containing the routes is extracted entry by entry and pushed into the route pipeline.
9. Routes are created from the given entry.
10. Invalid routes are filtered.
11. Airlines and markets used in the created route and not already in the database are written into the database.
12. The route is written into the database
13. Step 6 to 12 are done for the on-time-database, now creating (logical) flights instead of routes.
14. If there is more than one month to be crawled, steps 6 to 13 are repeated for every given month.

### Definitions  
Route = Information available on a monthly base. They contain the number of passengers going from one market to the other in the given month. The information for number of passengers is always given as a route with the date of the first day of the corresponding month.  
Flight = Information available on a daily base. This contains, for each flight, information about delays and cancellations, as well as the exact date of the flight. Flights also make up the number of flights from one market to another.
