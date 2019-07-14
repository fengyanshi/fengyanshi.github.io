Solitary wave 
###############

.. figure:: images/simple_cases/eta_1d_solitary.jpg
    :width: 400px
    :align: center
    :height: 500px
    :alt: alternate text
    :figclass: align-center

|  **Parallel (if applicable)**
|   PX = 2
|   PY = 1

|  **Depth**
|   DEPTH_TYPE = SLOPE
|   DEPTH_FLAT = 10.0
|   SLP = 0.05
|   Xslp = 800.0

(refer to :ref:`definition_grid`)

|  **Dimensions**
|   Mglob = 1024
|   Nglob = 3

|  **Time**
|   TOTAL_TIME = 200.0 
|   PLOT_INTV = 10.0 
|   SCREEN_INTV = 10.0 

|  **Grid sizes**
|   DX = 1.0 
|   DY = 1.0 

|  **Add wavemaker**
|   WAVEMAKER = INI_SOLITARY
|   AMP = 1.0
|   DEP = 10.0 
|   XWAVEMAKER = 300.0 

|  **Add sponge layer**
|   FRICTION_SPONGE = T 
|   DIRECT_SPONGE = T 
|   Sponge_west_width =  180.0 
|   Sponge_east_width =  0.0 
|   Sponge_south_width = 0.0 
|   Sponge_north_width = 0.0 

  (refer to 2D case :ref:`info_sponge`)


|  **Breaking scheme (default: SWE breaker)**
|   VISCOSITY_BREAKING = T  
|   Cbrk1 = 0.65 
|   Cbrk2 = 0.35 

  (refer to options for breaking scheme :ref:`example_breaking`)

|  **Wetting and Drying**
|   MinDepth=0.01 

|  **Output**
|   RESULT_FOLDER = output/
|   ETA = T 
|   MASK = T 

  (refer to :ref:`definition_output`)
