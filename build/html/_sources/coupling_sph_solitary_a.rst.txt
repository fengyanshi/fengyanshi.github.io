GRID A (solitary wave case)
########################################

.. figure:: images/simple_cases/solitary_nesting.jpg
    :width: 400px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

.. NOTE:: RUN funwave_nocoupling

**input.txt:**

|  **Parallel(if applicable)**
|   PX = 2
|   PY = 2

|  **Depth**  
|   DEPTH_TYPE = FLAT 
|   DEPTH_FILE = ../bathy/depth_a15.txt 

  (refer to :ref:`definition_grid`)

|  **Output folder** 
|   RESULT_FOLDER = output_1/ 
 
|  **Dimensions**
|   Mglob = 1500
|   Nglob = 3

|  **Time**
|   TOTAL_TIME = 400.0 
|   PLOT_INTV = 1.0 
|   PLOT_INTV_STATION = 0.0 
|   SCREEN_INTV = 1.0 

|  **Grid**
|   Lon_West = 120.0
|   Lat_South = 0.0
|   Dphi = 0.000035972
|   Dtheta = 0.0001 

|  **Wavemaker** 
|  WAVEMAKER = INI_SOL
|  AMP = 0.1
|  DEP = 10.0
|  LAGTIME = 0.0
|  XWAVEMAKER = 1000.0

  (refer to :ref:`definition_wavemaker`)

|  **Physics** 
|   Cd = 0.0


|  **Stations** 
|  NumberStations = 3
|  STATIONS_FILE = **station.txt**

|  **Output** 
|   DEPTH_OUT = T 
|   ETA = T 
|   U = T
|   V = T

  (refer to :ref:`definition_output`)
