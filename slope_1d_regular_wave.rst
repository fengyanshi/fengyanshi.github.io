Regular wave 
#############

.. figure:: images/simple_cases/eta_1d_reg.jpg
    :width: 600px
    :align: center
    :height: 300px
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
|   WAVEMAKER = WK_REG
|   DEP_WK = 10.0 
|   Xc_WK = 250.0 
|   Yc_WK = 0.0 
|   Tperiod = 12.0 
|   AMP_WK = 0.5 
|   Delta_WK = 3.0  ! the default is 0.5, set a larger number for nonlinear waves

|  **Add sponge layer**
|   FRICTION_SPONGE = T 
|   DIRECT_SPONGE = T 
|   Sponge_west_width =  180.0 
|   Sponge_east_width =  0.0 
|   Sponge_south_width = 0.0 
|   Sponge_north_width = 0.0 

|  **Breaking scheme (default: SWE breaker)**
|   VISCOSITY_BREAKING = T  
|   Cbrk1 = 0.65 
|   Cbrk2 = 0.35 

|  **Wetting and Drying**
|   MinDepth=0.01 

|  **Output**
|   RESULT_FOLDER = output/
|   ETA = T 
|   MASK = T 
