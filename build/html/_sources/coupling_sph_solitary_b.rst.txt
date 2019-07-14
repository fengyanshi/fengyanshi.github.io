GRID B (solitary wave case)
########################################

.. figure:: images/simple_cases/solitary_nesting.jpg
    :width: 400px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

.. NOTE:: RUN funwave_coupling

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
|   Mglob = 2000
|   Nglob = 3

|  **Time**
|   TOTAL_TIME = 400.0 
|   PLOT_INTV = 1.0 
|   PLOT_INTV_STATION = 0.0 
|   SCREEN_INTV = 1.0 

|  **Grid**
|   Lon_West = 120.0
|   Lat_South = 0.0
|   Dphi = 0.000017986
|   Dtheta = 0.00005 

|  **Wavemaker** 
|  WAVEMAKER = nothing

|  **Physics** 
|   Cd = 0.0

|  **COUPLING**
|  COUPLING_FILE = coupling_same.txt

|  **COUPLING FILE** 
|  COUPLING_FILE = ../make_nest_file/coupling.txt

|  **Output** 
|   DEPTH_OUT = T 
|   ETA = T 
|   U = T
|   V = T

  (refer to :ref:`definition_output`)
