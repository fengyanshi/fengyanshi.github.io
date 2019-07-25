.. _section-definitions:

**DEFINITIONS OF PARAMETERS**
=============================

.. note:: Examples of model setup are provided in the downloaded package (simpe example folder). If you are a beginner, we strongly suggest trying those examples first and find an example similar to your case. Introduction to those examples can be found at `Simple tests <examples.html>`_.

In this section, we will describe the structure of the "input.txt" file and the input parameters required for each module available in FUNWAVE. Each example in the :code:`/simple_cases/` folder of the downloaded package has a version of the "input.txt" file that is unique to that example. You can refer to the "input.txt" file for each example when reviewing the definitions of parameters described here.

In addition, you will need to create the unique executable needed to run the specific example. This executable is created by the "Makefile". In some cases, multiple examples can be run from the same executable so long as the appropriate flags pertaining to the example are active in the "Makefile". To learn more about makefiles and running FUNWAVE, review the :ref:`Model Download and Setup <section-download>` page.

********************************

=========
INPUT.TXT
=========

An example "input.txt" file is presented below. This file is from the :ref:`Waves on 1D Slope <section-1d-slope>` example, located in :code:`/simple_cases/surface_wave_1d/input_files`. The input file is divided into sections with dashes, where lines with "!" are comments. Brief descriptions of the parameters are listed in each section. Most model parameters are specified in "input.txt", except the parameters specific to a particular module. There parameters will be added to "input.txt". Take a moment to familiarize yourself with the basic structure of the FUNWAVE input file. A comprehensive description of all parameters is located at the :ref:`bottom <subsection-defs>` of this page.

.. code-block:: rest

        ! INPUT FILE FOR FUNWAVE_TVD 
        ! NOTE: all input parameter are capital sensitive 
        ! --------------------TITLE------------------------------------- 
        ! title only for log file 
         TITLE = regular_1D
        
        ! -------------------PARALLEL INFO----------------------------- 
        !  
        !    PX,PY - processor numbers in X and Y 
        !    NOTE: make sure consistency with mpirun -np n (px*py) 
        !     
         PX = 2
         PY = 1
        
        ! --------------------DEPTH------------------------------------- 
        ! Depth types, DEPTH_TYPE=DATA: from depth file 
        !              DEPTH_TYPE=FLAT: idealized flat, need depth_flat 
        !              DEPTH_TYPE=SLOPE: idealized slope,  
        !                                 need slope,SLP starting point, Xslp 
        !                                 and depth_flat 
         DEPTH_TYPE = SLOPE
        ! if depth is flat and slope, specify flat_depth
         DEPTH_FLAT = 10.0
        ! if depth is slope, specify slope and starting point
         SLP = 0.05
         Xslp = 800.0

        ! -------------------PRINT--------------------------------- 
        ! PRINT*, 
        ! result folder 
         RESULT_FOLDER = output/

        ! ------------------DIMENSION----------------------------- 
        ! global grid dimension 
         Mglob = 1024
         Nglob = 3 

        ! ----------------- TIME---------------------------------- 
        ! time: total computational time/ plot time / screen interval  
        ! all in seconds 
         TOTAL_TIME = 200.0 
         PLOT_INTV = 10.0 
         PLOT_INTV_STATION = 0.5 
         SCREEN_INTV = 10.0 

        ! -----------------GRID---------------------------------- 
        ! if use spherical grid, in decimal degrees 
         DX = 1.0 
         DY = 1.0 
        
        ! ----------------WAVEMAKER------------------------------ 
        !  wave maker 
        ! LEF_SOL- left boundary solitary, need AMP,DEP, LAGTIME 
        ! INI_SOL- initial solitary wave, WKN B solution,  
        ! need AMP, DEP, XWAVEMAKER  
        ! INI_REC - rectangular hump, need to specify Xc,Yc and WID 
        ! WK_REG - Wei and Kirby 1999 internal wave maker, Xc_WK,Tperiod 
        !          AMP_WK,DEP_WK,Theta_WK, Time_ramp (factor of period) 
        ! WK_IRR - Wei and Kirby 1999 TMA spectrum wavemaker, Xc_WK, 
        !          DEP_WK,Time_ramp, Delta_WK, FreqPeak, FreqMin,FreqMax, 
        !          Hmo,GammaTMA,ThetaPeak 
        ! WK_TIME_SERIES - fft time series to get each wave component 
        !                 and then use Wei and Kirby 1999  
        !          need input WaveCompFile (including 3 columns: per,amp,pha) 
        !          NumWaveComp,PeakPeriod,DEP_WK,Xc_WK,Ywidth_WK 
         WAVEMAKER = WK_REG 
         DEP_WK = 10.0 
         Xc_WK = 250.0 
         Yc_WK = 0.0 
         Tperiod = 8.0
         AMP_WK = 0.5
         Theta_WK = 0.0
         Delta_WK = 3.0   ! the default is 0.5, set a large number for nonlinear waves
        
        ! ---------------- PERIODIC BOUNDARY CONDITION --------- 
        ! South-North periodic boundary condition 
        ! 
         PERIODIC = F

        ! ---------------- SPONGE LAYER ------------------------ 
        ! need to specify widths of four boundaries and parameters if needed
        ! set width=0.0 if no sponge 
         DIFFUSION_SPONGE = F 
         FRICTION_SPONGE = T 
         DIRECT_SPONGE = T 
         Csp = 0.0 
         CDsponge = 1.0 
         Sponge_west_width =  180.0 
         Sponge_east_width =  0.0 
         Sponge_south_width = 0.0 
         Sponge_north_width = 0.0 

        ! ----------------PHYSICS------------------------------ 
        ! parameters to control type of equations 
        ! dispersion: all dispersive terms 
        ! gamma1=1.0,gamma2=1.0: defalt: Fully nonlinear equations 
        !----------------Friction----------------------------- 
         Cd = 0.0 

        ! ----------------NUMERICS---------------------------- 
        ! time scheme: runge_kutta for all types of equations 
        !              predictor-corrector for NSWE 
        ! space scheme: second-order 
        !               fourth-order 
        ! construction: HLLC 
        ! cfl condition: CFL 
        ! froude number cap: FroudeCap 
         ! HIGH_ORDER = THIRD 
        ! CFL 
         CFL = 0.5 
        ! Froude Number Cap (to avoid jumping drop, set 1.5) 
         FroudeCap = 3.0 

        ! --------------WET-DRY------------------------------- 
        ! MinDepth for wetting-drying 
         MinDepth=0.01 

        ! -------------- BREAKING ----------------------------
         VISCOSITY_BREAKING = T  
         Cbrk1 = 0.65 
         Cbrk2 = 0.35 

        ! ----------------- WAVE AVERAGE ------------------------ 
        ! if use smagorinsky mixing, have to set -DMIXING in Makefile 
        ! and set averaging time interval, T_INTV_mean, default: 20s 
         T_INTV_mean = 240.0 
         STEADY_TIME=480.0 

        ! -----------------OUTPUT----------------------------- 
        ! stations  
        ! if NumberStations>0, need input i,j in STATION_FILE 
         NumberStations = 0
         STATIONS_FILE = gauges.txt 
        ! output variables, T=.TRUE, F = .FALSE. 
         DEPTH_OUT = T 
         ETA = T 
         MASK = T 
         WaveHeight = T 

*************************************

.. _subsection-defs:

===========
Definitions
===========

.. note:: All parameter names are case sensitive.

.. toctree::
   :maxdepth: 2
   
   central_para
   spherical
   shipwakes_para
   sediment_para
   meteo_tsu
   tracer_setup
   slide






