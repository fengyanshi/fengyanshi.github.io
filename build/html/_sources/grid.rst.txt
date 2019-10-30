.. _definition_grid:

Grid and Computational Time
***************************

**SPECIFICATION OF DIMENSION**

* :code:`Mglob`: global dimension in x direction.

* :code:`Nglob`: global dimension in y direction.

**SPECIFICATION OF GRID SIZE**

* :code:`DX`: grid size(m) in x direction.

* :code:`DY`: grid size(n) in y direction.

**SPECIFICATION OF WATER DEPTH**
 
* :code:`DEPTH_TYPE`: depth input type. 

 The program includes several simple bathymetry configurations such as:
 
 * :code:`DEPTH_TYPE = DATA`: from a depth file. 
   
 * :code:`DEPTH_TYPE = FLAT`:  flat bottom, need :code:`DEPTH_FLAT` 
                
 * :code:`DEPTH_TYPE = SLOPE`:  plane beach along x direction. It needs three parameters: slope, :code:`SLP`, slope starting point, :code:`Xslp` and flat part of depth, :code:`DEPTH_FLAT`.

* :code:`DEPTH_FILE`: name of bathymetry file, if :code:`DEPTH_TYPE = DATA`. The file dimensions should be the same as :code:`Mglob x Nglob` with the first point as the south-west corner. The read format in the code is shown below:

  .. code-block:: rest

       DO J=1,Nglob
       
        READ(1,*)(Depth(I,J),I=1,Mglob)
        
       ENDDO
 
* :code:`DEPTH_FLAT`: water depth of flat bottom if :code:`DEPTH_TYPE = FLAT` or :code:`DEPTH_TYPE = SLOPE` (flat part of a plane beach).
 
* :code:`SLP`: slope if :code:`DEPTH_TYPE = SLOPE`.

* :code:`Xslp`: starting x (m) of a slope, if :code:`DEPTH_TYPE = SLOPE`.

* :code:`WaterLevel`: Specify a water level which will be added to the input bathymetry and wavemaker depth such as :code:`DEP_WK` (internal wave generator) and :code:`DepthWaveMaker` (left boundary generator). 

 .. note::   IF you add surge or tide level using :code:`WaterLevel`,  please keep :code:`DEP_WK` the same as the original depth in the depth file because the water level will be automatically added to the model bathymetry. 

**SPECIFICATION OF TIME**
 
* :code:`TOTAL_TIME`: simulation time in seconds.

* :code:`PLOT_INTV`: output interval in seconds (Note, output time is not exact because adaptive :code:`dt` is used.)

* :code:`SCREEN_INTV`: time interval (s) of screen print. 

* :code:`PLOT_INTV_STATION`: time interval (s) of gauge output.

* :code:`PLOT_START_TIME`: start time for output of field results (s). Default: 0.0

* :code:`DT_fixed`: time step (s) if use fixed DT. But :code:`DT_fixed` will be checked by the CFL condition. IF :code:`DT_fixed` does not satisfy CLF, DT/2, DT/4 ... will be checked until it satisfies CFL. Default is using variable DT based on CFL. 



