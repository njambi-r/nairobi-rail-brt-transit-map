# 🚇 Nairobi Commuter Rail and Planned Bus Rapid Transport (BRT) Transit Map
This project provides code and structured data for generating a schematic-style transit map of Nairobi’s commuter rail and planned BRT network. It is not a web app, but you can use the code and data to create and customize your map.

Demo:  https://nairobi-rail-brt-transit-map.netlify.app/
![tube_map_with_legend (19)](https://github.com/user-attachments/assets/88adb917-d8f4-4827-af80-cb8a1b9af1f5)

### About
+ Map created using a modified version of [d3-tube-map](https://github.com/johnwalley/d3-tube-map)
+ The SVG/PNG download options capture the section of the map visible on the screen 

### Inspo
+ [Berlin U-Bahn Map](https://github.com/skamsie/berlin-ubahn-map)
+ [Lisbon Schematic Metro Map](https://github.com/Joao-Pedrosa/GSDB)
+ [Stuttgart Light Rail Network Maps](https://github.com/ad-freiburg/loom)

### Project Structure
```
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
│ └──# Files adopted from the original d3-tube-map folder. Used to create dynamic maps that load data from JSON
├── test/
│ └── # HTML files with all station paths and geometry hardcoded directly. Use it as a template if you want to manually construct small, fixed maps without needing JSON or JavaScript  
└── README.md # This guide
```
## 🛠️ Recreate or Customize the Map

### 1. Acquire data
Get the data related to the stations and lines you want to represent. This includes the station name, station coordinates, and line name. 

### 2. Create schematic layout
Quantum GIS (QGIS) software was used to create the schematic layout. The procedure outlined in the instruction guide [found here](https://dent.org.uk/materials-for-recreating-tube-map/) was loosely followed.
- The station and line data showing the real locations and links was loaded into QGIS. UTM
- A 1000m square grid was generated. Stations and lines were relocated to grid locations such that a route had only two types of corners: a 90 degree turn and a 45 degree turn.
- The result was a schematic map showing the modified locations and links.
- Tip: Organize stations along the same line in one layer to make it easier to define their order along the line.
- In the stations attribute table include the station name, line, x and y coordinates, and order along the line.
- Download the station attributes in csv format.

### 3. Prepare station data in CSV format
Make sure your CSV includes the following columns:
- `Name`: station name
- `Line`: route identifier
- `x_coord`, `y_coord`: schematic grid coordinates
- `line_order`: order of stations on each line

### 4. Convert CSV to JSON
Open the provided Jupyter notebook:
```bash
convert_csv_stations_to_json.ipynb
```
Run all cells to convert the CSV into the schematic JSON format required by d3-nairobi-map.js.

Save the output inside the json/ folder.

### 5. View map
You can open the map directly in your browser:
```bash
index.html
```
Ensure all file paths are correctly referenced:
```bash
<script src="./js/d3-nairobi-map.js"></script>
<script>
  d3.json("./json/NCR+BRT_v1.json").then(function (data) {
    // render map
  });
</script>
```
No server or build tools are required.

### 6. Customize
Modify `style.css` to adjust layout, fonts, or legend styles.

Edit `d3-nairobi-map.js` to tweak map behavior or add interactivity (e.g., tooltips, highlighting).

Update the `.json` data file manually if needed for fine-tuned control e.g., positioning of labels, offsetting, etc.

## ✅ To-do / Ideas for extension
- Auto-generate JSON from spatial (e.g., shapefile or GeoJSON) data
- Add interactivity to the map e.g., bringing up station info when clicked
- Add route finder
- Ingest GTFS data
