%Relevant tables on the Transtats website
  
##T-100 Domestic Segment (All Carriers)  
http://transtats.bts.gov/DL_SelectFields.asp?Table_ID=311  
DepScheduled  
DepPerformed  
Passengers  
AirlineID  
OriginCityMarketID  
DestCityMarketID  
Month  
  
##On-Time Performance
http://transtats.bts.gov/DL_SelectFields.asp?Table_ID=236  
Year  
Month  
DayOfWeek  
FlightDate  
AirlineID  
OriginCityMarketID  
DestCityMarketID  
DepDelayMinutes  
ArrDelayMinutes  
Cancelled  

##Needed Lookup-Tables:  
Dest/OriginCityMarketID - http://transtats.bts.gov/Download_Lookup.asp?Lookup=L_CITY_MARKET_ID  
AirlineID - http://transtats.bts.gov/Download_Lookup.asp?Lookup=L_AIRLINE_ID  



# Backend JSON requests:

## Airline

`http.Get("http://transtats.bts.gov/Download_Lookup.asp?Lookup=L_AIRLINE_ID")`
```csv
Code,Description
"19031","Mackey International Inc.: MAC"
"19032","Munz Northern Airlines Inc.: XY"
"19033","Cochise Airlines Inc.: COC"
"19034","Golden Gate Airlines Inc.: GSA"
"19035","Aeromech Inc.: RZZ"
"19036","Golden West Airlines Co.: GLW"
"19037","Puerto Rico Intl Airlines: PRN"
"19038","Air America Inc.: STZ"
"19039","Swift Aire Lines Inc.: SWT"
```
```json
{
	"name": "string[[Description]]",
	"id": "int[[Code]]"
}
```

## Market

`http.Get("http://transtats.bts.gov/Download_Lookup.asp?Lookup=L_CITY_MARKET_ID")`
```csv
Code,Description
"30001","Afognak Lake, AK"
"30003","Granite Mountain, AK"
"30004","Lik, AK"
"30005","Little Squaw, AK"
"30006","Kizhuyak, AK"
"30007","Klawock, AK"
"30008","Elizabeth Island, AK"
"30009","Homer, AK"
"30010","Hudson, NY"
```
```json
{
	"name": "string[[Description]]",
	"id": "int[[Code]]"
}
```

## Route

```
form := url.Values{"sqlstr": {"SELECT DAY_OF_WEEK,FL_DATE,AIRLINE_ID,ORIGIN_CITY_MARKET_ID,DEST_CITY_MARKET_ID,
									ARR_DELAY_NEW,CANCELLED 
							   FROM T_ONTIME 
							   WHERE Month=[[month]] 
							   AND YEAR=[[year]] 
							   AND ORIGIN_CITY_MARKET_ID=31703"}}
http.PostForm("http://transtats.bts.gov/DownLoad_Table.asp", form)
```
```csv
"DAY_OF_WEEK","FL_DATE","AIRLINE_ID","ORIGIN_CITY_MARKET_ID","DEST_CITY_MARKET_ID","ARR_DELAY_NEW","CANCELLED",
1,2015-02-02,19805,31703,32575,,1.00,
1,2015-02-09,19805,31703,32575,22.00,0.00,
1,2015-02-16,19805,31703,32575,0.00,0.00,
1,2015-02-23,19805,31703,32575,9.00,0.00
```

```
form := url.Values{"sqlstr": {"SELECT DEPARTURES_SCHEDULED,DEPARTURES_PERFORMED,PASSENGERS,AIRLINE_ID,
									ORIGIN_CITY_MARKET_ID,DEST_CITY_MARKET_ID,MONTH 
							   FROM  T_T100D_SEGMENT_ALL_CARRIER  
							   WHERE Month=[[month]] 
							   AND YEAR=[[year]] 
							   AND ORIGIN_CITY_MARKET_ID=31703"}}
http.PostForm("http://transtats.bts.gov/DownLoad_Table.asp", form)
```
```csv
"DEPARTURES_SCHEDULED","DEPARTURES_PERFORMED","PASSENGERS","AIRLINE_ID","ORIGIN_CITY_MARKET_ID","DEST_CITY_MARKET_ID","MONTH",
0.00,1.00,0.00,21107,31703,31703,2,
0.00,1.00,0.00,21492,31703,31995,2,
0.00,1.00,0.00,21492,31703,31703,2
```

```json
{
	"date": "date[[FL_DATE]]",
	"delays": "double[[ARR_DELAY_NEW]]",
	"cancelled": "double[[CANCELLED]]",
	"passengerCount": "double[[]]",
	"flightCount": "double[[]]",
	"airline": "hal+id[[AIRLINE_ID]]",
	"source": "hal+id[[ORIGIN_CITY_MARKET_ID]]",
	"destination": "hal+id[[DEST_CITY_MARKET_ID]]"
}

