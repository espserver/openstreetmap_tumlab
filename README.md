# OpenStreetmap_tumlab

## Requirements:

-   Docker-compose v2.12.1
-   Need one map uncompressed in folder osm-data. To unziped a map, perform this procedure:
    -   Download the map you want at: [Geofabrik](http://download.geofabrik.de/).
    -   Unzip the map with docker, using this command, you just have to replace the path of the bind mount and the osm.pbf file:
        ```
        ~$docker run -v /path/osm_file/colombia-latest.osm.pbf:/data/region.osm.pbf -v /path/bind_mount/:/data/database/ overv/openstreetmap-tile-server import
        ```
    -   This command will start the decompression of the map with a temporary docker container, once this is finished, we will have a folder called postgres in the folder that we specified when creating the bind-mount. Once finished, that folder is the unzipped map
-   For the Folders osm-data and osm-tiles, full permissions needed
    ```
    ~$chmod 777 osm-data/ osm-tiles/
    ```
### Execution

-   Copy unziped map in folder osm-data
-   Execute comand:
    ```
       docker compose up -d
    ```
In the osm-data folder, the entire application database is stored.
In the osm-tiles folder, all the rendering that users have done when zooming to the map is stored

