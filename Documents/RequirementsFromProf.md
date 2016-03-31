# What do we need?

## Data!

* Destinations in Germany that are already there
* Which airlines serve these destinations? (competitors)
  * How often do they serve these destinations? -> Number of passengers
* Delay frequencies?
* Delay duration?
* Cancelation Frequency

## Graph!

* x-Axis: quantitative numbers
  * frequencies
  * passenger numbers
  * delay frequencies / durations
  * Cancelation frequencies
* y-Axis: qualitative numbers
  * time
  * day of week
  * destination
  * origin
* Filters!
  * by airlines
  * or any of the qualitative numbers

## Several analysts work on the same data!

* store settings under some kind of name
* share settings

## More stuff

* only passenger transportation is relevant
* CentOS server will be provided with MySQL database, ssh access from within companys (faculty) network
* It's enough for the data to be available only in the office
* Should work on Win 10 Installation with Firefox
* no stupid people
* time is local of the destination
* no design guidelines yet
* no authentication but identification
* Multiple Logins of of one user on more than one machine possible
* Data not present mustnt be calculated or made up
* Export current graph + filtersettings to pdf, popup Explorer to choose directory/filename

## GUI
* no colorblind users present
* Dropdownlist for Achsenbeschriftung
* Maybe Dropdownlist for Filtercategories & checkboxes originating from the connection
* Logo upper left, Logout button upper right, logged in user left of the logoutbutton. logoutbutton changes to login, if not logged in.
* Saved Filtersettings in the application to be load/stored
* Export/Load/Save Buttons on the left
