
# Crawler
## Detailed listing of the proceedings of the crawling process
1. Start the crawler via a REST command, either by using the "Crawler"-Button in the GUI or by just sending the command to http://10.28.2.166/crawler.  
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

Definitions  
Route = Information only available on a monthly base. They contain the number of passengers going from one market to the other in the given month.  
Flight = Information available on a daily base. This contains, for each flight, information about delays and cancellations, as well as the exact date.
