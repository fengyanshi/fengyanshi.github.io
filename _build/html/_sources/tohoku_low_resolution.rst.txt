Tohoku Low Resolution 
########################

.. figure:: images/simple_cases/tohoku_surface.jpg
    :width: 400px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center

**input.txt:**

|  **Parallel(if applicable)**
|   PX = 2
|   PY = 2

|  **Specify bathymetry**
|   DEPTH_TYPE = DATA
|   DEPTH_FILE = ../external_files/depth_30min.txt

|  **Dimensions**
|   Mglob = 320
|   Nglob = 240

|  **Grid**
|   Lon_West = 132.0
|   Lat_South = -60.0
|   Dphi = 0.5
|   Dtheta = 0.5

|  **Time**
|   TOTAL_TIME = 86400.0
|   PLOT_INTV = 3600.0
|   PLOT_INTV_STATION = 1.0
|   SCREEN_INTV = 3600.0

|  **Add initial conditions**
|   INI_UVZ = T
|   ETA_FILE = ../external_files/ETA_30min.txt
|   U_FILE = ../external_files/U_30min.txt
|   V_FILE = ../external_files/V_30min.txt

|  **Add Sponge layers**
|   DIRECT_SPONGE = T
|   FRICTION_SPONGE = T
|   Sponge_west_width =  100000.0 
|   Sponge_east_width =  100000.0
|   Sponge_south_width = 100000.0
|   Sponge_north_width = 100000.0

|  **Add friction**
|   Cd = 0.001

|  **Avoid inundation in the basin scale**
|   MinDepth= 10.0

|  **Output**
|   NumberStations = 78
|   STATIONS_FILE = stations-pacific.txt
|   ETA = T
|   Hmax = T








