# Please access the nbviewer notebook for Route Gen Asia.ipynb here to checkout the interactive maps of Folium : [Click here](https://nbviewer.org/github/Anik320Bhowmick737/Flight-Root-Generator-Asian-Airspace/blob/main/Route%20Gen%20Asia.ipynb)
# Flight Root Generator Asian Airspace
This repository uses Waypoints from Aircraft Navigation Database of Flight Simulator to generate Flight Routes that are most fuel efficient by considering shortest path. Dijkstra Algorithm is used for getting this shortest path.

# Procedure
The user needs to give the ICAO of Departing and Arrival airport. The code in python will generate the shortest path and shows the output. Lets us consider one such example with a flight from **Kolkata (VECC) to Mumbai (VABB)**:
```
route = get_Route("VECC","VABB")
print("Waypoints:", route["Route"])
print("\n")
print(f"Total Distance: {route['Distance']:.2f} NM")
print("\n")
print(f"Airways used: {route['Airway']}")
print("\n")
print("ATC route:")
summarize_ATCroute(route)
```
This snippet will give the following output:
```
Waypoints: ['CEA', 'NUDLA', 'JRS', 'OGUNA', 'IKINA', 'OSVAS', 'OMLEG', 'TASEX', 'ASIPI', 'LUXIP', 'OPAKA', 'BBB']


Total Distance: 900.62 NM


Airways used: ['J46', 'J46', 'W160', 'Z14', 'Z14', 'Q20', 'Q20', 'Q20', 'Q20', 'Q20', 'W18']


ATC route:
CEA J46 JRS W160 OGUNA Z14 OSVAS Q20 OPAKA W18 BBB

```
**Explanation:**


* The route begins with the VOR of Kolkata i.e **CEA** and takes up the airway **J46** to reach **Jharsuguda (JRS)**
* Then it takes another airway **W160** to reach a Fix **OGUNA** and then to **OSVAS** via **Z14**
* Then using **Q20** it reaches OPAKA and then finally reaches **Mumbai (BBB)** using **W18**
* The distance it takes is about 900.62 Nautical Miles roughly about 1668 Km.

**For verification purpose a map view is shown from Folium**


<img width="1200" alt="Screenshot 2024-08-18 at 10 31 29 PM" src="https://github.com/user-attachments/assets/57af1d6d-6ae1-4050-b642-9ceeb1755517">


# Special Note
* All the Waypoints, Navaids, Airways that are shown here and in the notebook do exist in the real world.
* The route that is generated by our code does not consider terminal area movement like SIDs and STARs, so this should never be used in real world aviation and flying purpose. The sole purpose of this repository is to highlight the working and very good uses case of Dijkstra's Algorithm.
* The route that is generated here does not consider weather avoidance and restricted airspaces.
* The database that is used for this task is a paid one from a very well known company and is **copyright protected**, so I can not upload the dataset here. The dataset that I used is CSV and is parsed from their raw database.
