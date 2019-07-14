Regular wave (baseline case)
##############################

.. figure:: images/simple_cases/eta_inlet_shoal_reg.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

**input.txt:**

|  **Parallel(if applicable)**
|   PX = 8
|   PY = 16

|  **Depth**  
|   DEPTH_TYPE = DATA 
|   DEPTH_FILE = ../bathy/dep_shoal_inlet.txt 

 * Definition: :ref:`definition_grid`
 * Option: Bathymetry Correction. 
   visit :ref:`bathymetry_correction`.

|  **Output folder** 
|   RESULT_FOLDER = output/ 
 
|  **Dimensions**
|   Mglob = 512
|   Nglob = 1024 

|  **Time**
|   TOTAL_TIME = 1200.0 
|   PLOT_INTV = 30.0 
|   PLOT_INTV_STATION = 0.5 
|   SCREEN_INTV = 30.0 

|  **Grid sizes**
|   DX = 2.0 
|   DY = 2.0 

|  **Wavemaker** 
|   WAVEMAKER = WK_REG
|   DEP_WK = 10.0 
|   Xc_WK = 250.0 
|   Yc_WK = 0.0 
|   Tperiod = 12.0 
|   AMP_WK = 1.0 
|   Theta_WK = 0.0 

  (refer to :ref:`definition_wavemaker`)

|  **Sponge layer** 
|   FRICTION_SPONGE = T 
|   DIRECT_SPONGE = T 
|   Csp = 0.0 
|   CDsponge = 1.0 
|   Sponge_west_width =  180.0 
|   Sponge_east_width =  0.0 
|   Sponge_south_width = 0.0 
|   Sponge_north_width = 0.0 

   (refer to :ref:`info_sponge`)

|  **Wetting and drying** 
|   MinDepth=0.01 

|  **Breaking scheme**
|   VISCOSITY_BREAKING = T  
|   Cbrk1 = 0.65 
|   Cbrk2 = 0.35 

  (refer to :ref:`example_breaking`)

|  **Wave averaging property** 
|   T_INTV_mean = 240.0 
|   STEADY_TIME=480.0 

|  **Output** 
|   ETA = T 
|   MASK = T 
|   WaveHeight = T 

  (refer to :ref:`definition_output`)


