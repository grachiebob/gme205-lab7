# GmE 205: Laboratory 7 
## PostGIS to REST API to GIS Clients

### *Description*
This project shows how statial data flows from PostGIS through a REST API using Flask endpoints to GIS clients like QGIS for visualization and analysis.

### *Dependencies*
* Python 3.14
* Visual Studio Code
* flask
* flask-cors
* psycopg2-binary
* python-dotenv

### *Reflection*
1. **What role does PostGIS play in this architecture?** <br>
PostGIS plays an important role in this architecture because it extends PostgreSQL with spatial capabilities. While PostgreSQL can only keep attributes such as names and numbers, PostGIS serves like a special storage system for maps, which knows how to store, query, and process spatial data, such as polygons for parcels and lines for roads.  In this case, the function `ST_AsGeoJSON(ST_Force2D(geom))` demonstrates how PostGIS takes part in transforming geometries into a format that the system or computer can easily understand and serve directly to clients.<br>

2. **What role does Flask play in this laboratory?** <br>
Flask can be visualized as a mailman for maps. The database, or PostGIS, is where the maps are stored. However, clients need a way to access this database. Thus, Flask sets up web addresses called endpoints, such as `/api/parcels.geojson` and `/api/roads.geojson`. Flask serves as a web framework to show this spatial data using HTTP endpoints. Using these endpoints, data stored in PostGIS will be retrieved and returned in JSON or GeoJSON format. To simplify, it serves as a helper that delivers maps from a database.<br>

3. **Why is GeoJSON useful for spatial web services?** <br>
GeoJSON is like a special language for maps where both the client and the system or computer can understand. This format is useful because it is widely accepted and used for representing spatial features. It also makes it easier to integrate with web-mapping software, such as QGIS. In the code, the function `geojson_response()`ensures that the data is returned in a QGIS-friendly response, which can be consumed and visualize the parcel and road data without additional methods. <br> 

4. **How does `ST_AsGeoJSON()`support distributed GIS?** <br>
`ST_AsGeoJSON()`serves as a converter where the spatial data stored in a database (PostGIS) is converted into GeoJSON format, which both clients and systems or computers can easily process, share, and understand across different systems or computers and clients over the web. In this case, the query `get_parcels` uses `ST_AsGeoJSON(ST_Force2D(geom)) to transforms the parcel data into GeoJSON format through the Flask endpoints. Through this process, clients can easily access the data using QGIS or other web applications without the need to connect directly to the database (PostGIS).< br>

5. **Why is QGIS considered a heavy client?**<br>
QGIS is a mapping application which is considered a heavy client because it performs complex tasks for the client, such as visualizing data, showing multiple layers of data, and running various spatial analyses and  operations simultaneously. This application usually requires significant processing power and memory. Based on experience, it processes the data more slowly once the datasets become larger and heavier, specifically with large and complex maps. In this laboratory, the endpoints `/api/parcels.geojson` and `/api/roads.geojson` are connected and opened in QGIS to retrieve the data for the client’s visualization and analysis. QGIS is a powerful tool but requires intensive resources, which makes it a heavy client.<br>

6. **Why is a REST API better than manually exporting shapefiles?**<br>
A REST API is better than manually exporting shapefiles. Instead of saving and exporting shapefiles manually whenever there are changes, the REST API provides real-time access to spatial data without the need to repeatedly perform the manual steps. Manually, it becomes insufficient, since shapefiles need to be loaded, saved, and transferred whenever changes occur. By using REST API, the manual and slow-paced process becomes faster and more efficient with shapefiles.<br>  

7. **How does this laboratory demonstrate distributed geospatial computing?**<br>
There is a separate responsibility among the database, server, and client, where this laboratory demonstrated a distributed geospatial computing. PostGIS serves as the database where it stores spatial data, such as the parcel and road data, while Flask serves as the server, which handles the conversion of spatial data into GeoJSON format to be served to the client through endpoints. Lastly, the QGIS application loads these endpoints for visualization and analysis of parcel and road data. These tasks across the system demonstrates distributed geospatial computing, which makes the process more efficient.<br>

8. **What advantages does service-based GIS architecture provide?**<br>
The advantages of service-based GIS architecture include easier data access and sharing, as well as a centralized way to manage stored spatial data. Instead of manually passing data back and forth between clients, they can easily access the data through endpoints in real-time. The data can also be easily used and integrated into various web-mapping applications, such as QGIS and ArcGIS Pro, without the need for additional steps in exporting and saving, which makes the process more efficient.<br> 

9. **How does this architecture support scalability in spatial systems?**<br>
This architecture supports scalability in spatial systems by allowing clients to request and work on the same data service simultaneously without the need to duplicate the available datasets. Similar to the previous explanation, the database (PostGIS) stores all the spatial data, while Flask serves this stored data through REST endpoints, where new clients can access the GeoJSON given by Flask, without changing the database. For instance, the endpoints `/api/parcels.geojson`and `/api/roads.geojson` can be accessed by multiple clients at the same time. As this demand for data grows, the server can still distribute the data efficiently, which makes it easier to handle larger datasets and constant requests.<br> 

## Author
Maria Graciella L. Roque  
Discord:[@grachiebob]

## Acknowledgements
* GmE 205 Laboratory Exercise 7 Manual
* [MarkDown](https://www.markdownguide.org/cheat-sheet/)

Edited on VS Code