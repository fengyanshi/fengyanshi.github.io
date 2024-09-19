DEFINITIONS OF PARAMETERS
============================================

Parallelization
******************************************************
Note that the numbers defined in the following statement are only for example
  .. code-block:: rest

     ! --------------------PROCESSOR NUMBER-------------------------
     ! processors in x and y direction (for parallel run)
     PX = 4 (for example)
     PY = 2

Grid
******************************************************
  .. code-block:: rest

     ! --------------------DIMENSION---------------------------------
     ! cell numbers
     Mglob = 256
     Nglob = 128
     Kglob = 3
     ! ------------------------GRID----------------------------------
     ! grid sizes
     DX = 2.0
     DY = 2.0

Time
***********
  .. code-block:: rest

     ! -----------------------TIME----------------------------------
     ! all in seconds
     TOTAL_TIME =100.0
     PLOT_START = 0.0
     PLOT_INTV = 1.0
     SCREEN_INTV = 1.0

Numerics
***************
  .. code-block:: rest

     ! ----------------------NUMERICS------------------------------------
     HIGH_ORDER = SECOND
     TIME_ORDER = SECOND
     HLLC = F
     CONVECTION = NOTVD
     CFL = 0.5
     FROUDE_CAP = 10.0
     MinDep = 0.20

Physics
***********
  .. code-block:: rest

     ! --------------------VISCOUS NUMBER----------------------------------
     VISCOUS_NUMBER = 0.1666667
     ! -------------------BOUNDARY_TYPE---------------------------------------
     ! bc_type=1: free-slip
     !         2: no-slip
     !         3: influx
     !         4: outflux
     !         5: bottom friction
     BC_X0 = 1
     BC_Xn = 1
     BC_Y0 = 1
     BC_Yn = 1
     BC_Z0 = 5
     BC_Zn = 1

Wavemaker
************
  .. code-block:: rest

     ! ---------------------WAVEMAKER-----------------------------------------
     ! wavemaker
     ! AMP - wave height; PER - wave period; DEP - incident water depth
     ! THETA - incident wave angle
     ! LEF_SOL - left boundary solitary wave, need AMP,DEP
     ! LEF_LIN - left boundary linear wave, need AMP,PER,DEP
     ! LEF_CON - left boundary cnoidal wave, need AMP,PER,DEP
     ! LEF_STK - left boundary stokes wave, need AMP,PER,DEP
     ! LEF_TID - left boundary tide wave, has to specify in subroutine
     ! LEF_SPC - left boundary 2D spectral, need spectral input spc2d.txt
     ! INI_ETA - initial surface elevation specified in subroutine initial
     ! INT_LIN - internal wavemaker for linear wave
     ! INT_CON - internal wavemaker for cnoidal wave
     ! INT_SOL - internal wavemaker for solitary wave
     ! INT_SPC - internal wavemaker for random wave
     !WAVEMAKER = INT_LIN
     WAVEMAKER = INT_LIN (example)
     AMP = 0.5
     PER = 10.0
     DEP = 8.0
     THETA = 0.0

Sponge layer
***************
  .. code-block:: rest

     ! ----------------SPONGE LAYER------------------------------------
     SPONGE_ON = T
     Sponge_West_Width =  35.0
     Sponge_East_Width =  0.0
     Sponge_South_Width = 0.0
     Sponge_North_Width = 0.0
     R_Sponge = 0.85
     A_Sponge = 5.0

Output
*************
  .. code-block:: rest

     ! --------------------FIELD OUTPUT---------------------------------
     ! output variables, T=.TRUE, F = .FALSE.
      OUT_H = T (water depth)
      OUT_E = T (surface elevation)
      OUT_U = T (velocity in x direction)
      OUT_V = T (velocity in y direction)
      OUT_W = T (velocity in z direction)
      OUT_P = T (dynamic pressure)
      OUT_K = T (turbulent kinetic energy)
      OUT_D = T (turbulent dissipation rate)
      OUT_S = T (shear production)
      OUT_C = T (eddy viscosity)



