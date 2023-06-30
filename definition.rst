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
         PLOT_START_TIME = 100.0

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
   subgrid_para

***************************************

.._subsection-checklist:

====================
Simulation Checklist
====================

After the FUNWAVE-TVD model has been downloaded and compiled on either your local machine or remote computing environment (e.g., HPC or AWS Cloud), and you’ve familiarized yourself with the :ref:`simple cases <section-examples>` in the model repository, you’re ready to begin running numerical wave simulations for your application. If you haven’t yet downloaded and compiled the model, follow the instructions on the :ref:`Model Download and Setup <section-download>` page. 

Below is a simple checklist to review before hitting “go” on a simulation. This checklist was designed to reduce the probability of experiencing an error when initiating a new simulation; however, it is not comprehensive of all possible input parameters and input file conditions for all applications.  

#. Input wave conditions are within the :ref:`valid range <info-structures>` of the model.
#. For stability, the ratio of DX and water depth is greater than 1/15, :ref:`DX/h > 1/15 <info-structures>`. 
#. The number of processors to request on the HPC or local machine matches the product of PX and PY from input.txt. This number should be a divisor of the number of available processors or cores per compute node (e.g., if 1 node supports 44 processors, -np must be 1, 2, 4, 11, 22, or 44).
#. Cross-reference the name and path of the FUNWAVE executable file to be used for the simulation in the run command or PBS script (if submitting a job on an HPC environment).
#. Cross-reference input file names (input.txt, depth.txt, gauges.txt or stations.txt, friction.txt, etc.) across the working directory, input.txt, and the PBS script (if submitting a job on an HPC environment).
#. Global input filetypes (e.g., depth.txt and friction.txt) are the same size as the domain (Mglob x Nglob) starting from the south-west corner. If generating files in Python, the bathy array will have Nglob rows and Mglob columns.
#. If using a depth type of FLAT or SLOPE, the DEPTH_FLAT = DEP_WK at the wavemaker. If using a depth type of DATA, ensure that the DEP_WK at XC_WK matches the depth at that location in the bathy.txt. For stability, it is best to artificially smooth the bathymetry to a constant depth at and around the wavemaker.
#. If transferring files from a Windows to a Linux machine (in an HPC environment, for example), run :code:`dos2unix [filename]` on input files to eliminate any possible Windows return characters (^M) at the end of a line.

If you have experience with running many FUNWAVE-TVD simulations and have recommendations to add to this simple checklist with respect to the Central, Vessel, Sediment, or Meteo modules, please send an email the FUNWAVE user group with the subject “Checklist Recommendations”. We will consider your recommendations and include them on the Wiki as appropriate. We appreciate your support and engagement as the modeling community and the model itself continues to evolve and grow.


