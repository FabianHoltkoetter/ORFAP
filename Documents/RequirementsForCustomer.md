#Systemspezifikation

## 1. User Storys

1. As a User I want to see the newest available data from transtats displayed in bar-graph form so that I can analyse the data to determine the best flight routes for the company.
2. As a User I want to configure the X-Axis of the graph to display one of the qualitative features TIME (day of week), destination, origin so that I can adapt the graph for my current needs.
3. As a User I want to configure the Y-Axis of the graph to display one of the quantitative features Flights, Passengers, Delays, DelayDuration, Cancellations so that I can adapt the graph for my current needs.
4. As a Max Schug I want to export the graph to PDF so that [insert reason here]
5. As a User I want to save my graph configurations to easily continue working on different analysations.
6. As a User I want to publicly share configurations with my colleagues to analyse stuff together. :heart:

## 2. Technical Requirements
### 2.1. GUI
### 2.2. Backend
Für die Datenspeicherung (User Story 1) soll es ein Backend geben. Dieses wird an eine vorhandene MYSQL Datenbank angebunden. Der Zugriff auf die Daten erfolgt über eine RESTFul Schnittstelle.

![FAPBAckend](Images/FAPBAckend.png)

Die RESTFul Schnittstelle bietet dabei sämtliche CRUD Operationen (Create, Read, Update, Delete). Zusätzlich soll es Schnittstellen zum Filtern der Daten geben. (User Story 2, 3)

### 2.3. Crawler

## 3. Ziele

## 4. Nicht-Ziele
