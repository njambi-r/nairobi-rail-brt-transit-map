# 🚇 Nairobi Commuter Rail and Planned Bus Rapid Transport (BRT) Transit Map
This project provides code and structured data for generating a schematic-style transit map of Nairobi’s commuter rail and planned BRT network. It is not a web app, but you can use the code and data to create and customize your map.

Demo:  https://nairobi-rail-brt-transit-map.netlify.app/

# About
+ Map created using a modified version of [d3-tube-map](https://github.com/johnwalley/d3-tube-map)
+ The download options capture the section of the map visible on the screen 

# Inspo from other people
+ [Berlin U-Bahn Map](https://github.com/skamsie/berlin-ubahn-map)
+ [Lisbon Schematic Metro Map](https://github.com/Joao-Pedrosa/GSDB)

# 📁 Project Structure
.
├── index.html # Main HTML file (renders the map)
├── js/
│ └── d3-nairobi-map.js # D3 logic for rendering the map
├── json/
│ └── NCR+BRT_v1.json # Map data in schematic JSON format
├── css/
│ └── tubeMap.css # Styles for layout and legend
├── convert_csv_stations_to_json.ipynb # Notebook to convert CSV to JSON
├── csv/
│ └── NCR+BRT_v1.csv # Original station data
├── examples/
│ └──(several html and json files) # files adopted from the original d3-tube-map folder which are simply examples of schematic maps of other areas. They help show the interaction between html and json files
├── test/
│ └── NCR+BRT_v1.csv # Original station data
└── README.md # This guide

