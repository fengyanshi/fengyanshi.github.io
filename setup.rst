.. _section-download:

**MODEL DOWNLOAD AND SETUP**
****************************

=============
Prerequisites
=============

There are a few software requirements your computer needs in order to execute FUNWAVE--TVD and to visualize the results. Please ensure you have installed the necessary software prior to downloading the source code.

You will need:

* Access to the Internet (Ethernet or WiFi)
* SSH Secure Shell Client (e.g., Putty or Cygwin on Windows)
* Working suite of compilers and Message Passing Interface (MPI) wrappers to build a parallel version of FUNWAVE-TVD

  * **If you are using a Mac OS X machine**
     
    We recommend you install GNU compilers (e.g., :code:`gcc, g++, gfortran`) via Homebrew. If you don't have Homebrew installed, type the following in your terminal:
    
    .. code-block:: rest
        
        cd ~
        mkdir homebrew
        curl -L https://github.com/Homebrew/brew/tarball/master
        tar xz --strip 1 -C homebrew
        
    If you didn't previously have these compilers on your system (say via Xcode), then the :code:`gcc, g++, gfortran` compilers would be placed under :code:`/usr/local/bin/` directory; otherwise they could be placed under :code:`/usr/local/Cellar/gcc/9.1.0/bin/`. You will then need to install the GNU suite of compilers using :code:`brew`, where the current versions are 9.1.0.
    
    **Important**: you want to use all suite components [:code:`gcc, g++, gfortran`] of the same version to avoid possible issues/compiler conflicts later on:
    
    .. code-block:: rest

        cd ~
        brew install gcc
        brew install gfortran

    Lastly, you will need to install MPI compiler wrappers:
    
    .. code-block:: rest

        cd ~
        brew install mpich
   
    **Note**: if you had a trace of previous compilers, you may need to explicitly tell Homebrew during installation to point to/use the newly installed compiler via FULL PATH in your terminal prior to executing the MPI installation command described above. You can do this by:
    
    .. code-block:: rest
    
        export HOMEBREW_FC = /usr/local/Cellar/gcc/9.1.0/bin/gfortran
        export HOMEBREW_CC = /usr/local/Cellar/gcc/9.1.0/bin/gcc
        export HOMEBREW_CCX = /usr/local/Cellar/gcc/9.1.0/bin/g++

  * **If you are using a Linux machine**
    
    You can use either your system-wide installation commands in your terminal/command line (*if you have admin/sudo privileges*). In your Ubuntu, Debian, Mint, or other Debian-based distribution, you can check if you have a working suite of compilers via:
    
    .. code-block:: rest

        which gcc
        which g++
        which gfortran

    Otherwise, if you don't have the suite of compilers already, type the following in your terminal to download and install:
    
    .. code-block:: rest

        sudo apt install gcc
        sudo apt install gfortran
        sudo apt install mpich

    For Red Hat, Fedora, or CentOS Linux kernels, you would replace :code:`apt` in the three commands above with :code:`yum`.

    Alternatively, you can also use Homebrew to install the required packages. See here for more details: `<https://docs.brew.sh/Homebrew-on-Linux>`_. It should be noted that Homebrew only does local installation (i.e., no system-wide :code:`sudo` commands for installation are allowed).

  * **If you are using a Windows 10 machine**
    
    Instructions on how to install FUNWAVE-TVD on Windows 10 can be found :ref:`here <section-win10-install>`.

  * **If you are using a Windows OS lower than Windows 10**
   
    We recommend that you download the latest version of Cygwin (`<https://www.cygwin.com>`_). Cygwin is a bash shell/unix emulation program, and contains many of the tools such as :code:`tar, gzip/gunzip, and cpp`, which will be useful for installation and compilation of FUNWAVE-TVD. In addtion, if you don't have access to a High Performance Computing (HPC) machine at your home location, you can use the Amazon AWS Cloud Computing service. For instructions on how to use AWS with FUNWAVE, visit :ref:`section-workshop-ud2019` and review pages 35-41 of the tutorial document (pdf1).

* A post-processing toolbox (e.g., MATLAB and Python)

  Both MATLAB and Python post-processing scripts are provided with most practice examples. If you do not have access to a MATLAB license, we recommend that you install an Anaconda Python package, usable on any platform.

  * **Downloading and installing a Python Package (Anaconda)**
    
    Arguably one of the best and most comprehensive FREE packages for the Python language, along with most tools and modules (e.g., :code:`NumPy, Matplotlib`, etc.) is distributed by the Continuum Analytics under the Anaconda package. It is available for Linux, Mac OS X, and Windows machines. You do NOT need administrator privileges to install the Anaconda package; you can do so as a standard user on all three platforms.

    For the Anaconda package, go to: `<https://www.anaconda.com/distribution/>`_.

    Choose the appropriate platform (Linux, Mac OS X, Windows) by selecting the correct tab and getting the Anaconda distribution that comes with **Python 3.7** (not 2.7). You can either download the Graphical Installer (recommended), or if you are comfortable with the terminal in the Linux/Mac OS X environment, you can also download it through the command line.

    For the complete list of packages/modules included in the Anaconda Python distribution, see: `<https://docs.continuum.io/anaconda/packages/pkg-docs>`_.

********************************************

====================
Download source code 
====================

`Version beta: not fully tested. click here to download/clone from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_

`Version 3.4 Released July 12 2019: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

`Version 3.3 Released July 19 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

`Version 3.2 Released Jan 27 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.1 Released Sep 2017: Used for FUNWAVE-TVD Workshop 2017 `click here to download <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.0: Released Apr 2017 :download:`download here <versions/funwave_tvd_30.zip>`

Versions 1.0, 1.1, 2.0, 2.1: Please contact fyshi@udel.edu

***********************************************************


.. _subsection-compile:

=================
Compile and setup
=================

Uncompress the code from the package downloaded

You have two options to compile the program

 * `Use a more automated Makefile <make_and_cml_input.html>`_. If you can compile the code successfully, go to 3. 

 * Use the following traditional method.

1. Modify "Makefile" as needed. An example "Makefile" is shown below. The primary variables you will need to change/check are the :code:`EXEC` in the :code:`BEGIN MAKEFILE` section, and the flags in the following section. The :code:`EXEC` variable defines the name of the executable that will be generated. This should be descriptive of which flags (i.e., modules) are active in the "Makefile" for good book-keeping when you have multiple executables.

 There are several flags in "Makefile" that specify different compiling structures and turn on/off modules depending on your simulation. To turn on/off a flag, simply comment the line by adding "\#" before the command (e.g., :code:`# FLAG_8 = -DVESSEL` turns the shipwake module "off" in the new executable). 
 
 * :code:`-DDOUBLE_PRECISION`: use double precision, default is single precision
 * :code:`-DPARALLEL`: use parallel mode, default is serial mode
 * :code:`-DCARTESIAN`: Cartesian version, otherwise Spherical version
 * :code:`-DINTEL`: if INTEL compiler is used, this option can make use of FPORT for the RAND() function
 * :code:`-DCRAY`: for CRAY RAND() and system commands
 * :code:`-DCOUPLING`: nesting mode
 * :code:`-DSPHERICAL_IJ_STATION`: in spherical mode, if you want your station locations defined by grid point (I,J). Otherwise, station locations should be defined by (lat lon)  
 * :code:`-DVESSEL`: include shipwake module
 * :code:`-DSEDIMENT`: include sediment and morphological module
 * :code:`-DWIND`: include wind effect
 * :code:`-DMETEO`: include meteo tsunami module
 * :code:`-DMANNING`: use Manning formula for bottom friction
 * :code:`-DCHECK_MASS_CONSERVATION`: correct mass conservation problem caused by wetting/drying
 * :code:`-DTRACKING`: include Lagrangian tracking module
 * :code:`CPP`: path to CPP directory
 * :code:`FC`: Fortran compiler 

 This sample "Makefile" shows a case where the shipwakes module (e.g., :code:`-DVESSEL`) is active, and the model will be executed in parallel (:code:`-DPARALLEL`) with a Cartesian coordinate system (:code:`-DCARTESIAN`) using an MPI F90 Compiler (:code:`FC = mpif90`).

 .. code-block:: rest

        #-----------BEGIN MAKEFILE-------------------------------------------------
            SHELL         = /bin/sh
            DEF_FLAGS     = -P -traditional 
            EXEC          = funwave_vessel
        #==========================================================================
        #--------------------------------------------------------------------------
        #        PRECISION          DEFAULT PRECISION: SINGLE                     
        #                           UNCOMMENT TO SELECT DOUBLE PRECISION
        #--------------------------------------------------------------------------

            FLAG_1 = -DDOUBLE_PRECISION 
            FLAG_2 = -DPARALLEL
        #             FLAG_3 = -DSAMPLES
            FLAG_4 = -DCARTESIAN
        #             FLAG_6 = -DINTEL
        #             FLAG_7 = -DMIXING
        #             FLAG_8 = -DCOUPLING
        #             FLAG_9 = -DZALPHA
        #             FLAG_10 = -DMANNING
        #             FLAG_11 = -DSPHERICAL_IJ_STATION
            FLAG_12 = -DVESSEL
        #             FLAG_13 = -DVIS_KENNEDY
        #             FLAG_14 = -DVESSEL_PANEL_SOURCE
        #             FLAG_15 = -DREALISTIC_VESSEL_BODY
        #             FLAG_16 = -DMETEO
        #             FLAG_17 = -DWIND
        #--------------------------------------------------------------------------
        #  mpi defs 
        #--------------------------------------------------------------------------
         CPP      = /usr/bin/cpp 
         CPPFLAGS = $(DEF_FLAGS)
         FC       = mpif90
         DEBFLGS  = 
         OPT      = 
         CLIB     = 
        #==========================================================================

         FFLAGS = $(DEBFLGS) $(OPT) 
         MDEPFLAGS = --cpp --fext=f90 --file=-
         RANLIB = ranlib
        #--------------------------------------------------------------------------
        #  CAT Preprocessing Flags
        #--------------------------------------------------------------------------
           CPPARGS = $(CPPFLAGS) $(DEF_FLAGS) $(FLAG_1) $(FLAG_2) \
	  	     $(FLAG_3) $(FLAG_4) $(FLAG_5) $(FLAG_6) \
		     $(FLAG_7) $(FLAG_8) $(FLAG_9) $(FLAG_10)  \
		     $(FLAG_11) $(FLAG_12) $(FLAG_13) $(FLAG_14) \
		     $(FLAG_15) $(FLAG_16) $(FLAG_17) $(FLAG_18) \
		     $(FLAG_19) $(FLAG_20) $(FLAG_21) $(FLAG_22) \
		     $(FLAG_23) $(FLAG_24)
        #--------------------------------------------------------------------------
        #  Libraries           
        #--------------------------------------------------------------------------

        #            LIBS  = $(PV3LIB) $(CLIB)  $(PARLIB) $(IOLIBS) $(MPILIB) $(GOTMLIB)
        #            INCS  = $(IOINCS) $(GOTMINCS)


        #--------------------------------------------------------------------------
        #  Preprocessing and Compilation Directives
        #--------------------------------------------------------------------------
        .SUFFIXES: .o .f90 .F .F90 

        .F.o:
	        $(CPP) $(CPPARGS) $*.F > $*.f90
        	$(FC)  -c $(FFLAGS) $(INCS) $*.f90
        	/bin/rm $*.f90
        #--------------------------------------------------------------------------
        #  FUNWAVE-TVD Source Code.
        #--------------------------------------------------------------------------

        MODS  = mod_param.F mod_global.F mod_input.F mod_vessel.F mod_bathy_correction.F \
                mod_meteo.F mod_parallel_field_io.F

        MAIN  = main.F bc.F fluxes.F init.F io.F tridiagnal.F       \
                breaker.F derivatives.F dispersion.F etauv_solver.F \
                sponge.F sources.F masks.F parallel.F statistics.F \
                wavemaker.F mixing.F nesting.F misc.F samples.F\

        SRCS = $(MODS)  $(MAIN)

        OBJS = $(SRCS:.F=.o)

        #--------------------------------------------------------------------------
        #  Linking Directives               
        #--------------------------------------------------------------------------

        $(EXEC):	$(OBJS)
	        	$(FC) $(FFLAGS) $(LDFLAGS) -o $(EXEC) $(OBJS) $(LIBS)
        #		mv $(EXEC) ../bin/
        #--------------------------------------------------------------------------

        #--------------------------------------------------------------------------
        #  Tar Up Code                           
        #--------------------------------------------------------------------------

        tarfile:
	        tar cvf funwave_tvd.tar *.F  Makefile

        #--------------------------------------------------------------------------
        #  Cleaning targets.
        #--------------------------------------------------------------------------

        clean:
	        	/bin/rm -f *.o *.mod

        clobber:	clean
	        	/bin/rm -f *.f90 *.o $(EXEC)


2. Compile the code

   The command :code:`make`, by default, will look for a file named "Makefile" in the current directory. It will read the contents of the file to find the target program or project that needs to be built (i.e., compiled). Generally, once a program is compiled, an executable file is generated. Any changes made to the source file (e.g., "Makefile") will need to be re-compiled, and a new executable will need to be generated. To clean, or remove, the files generated by the makefile and create new ones, the :code:`make clean` command is used prior to compiling with :code:`make`.
   
   In your terminal, navigate to the directory :code:`/src/` containing the file "Makefile", and type the following:
   
   .. code-block:: rest
        
        make clean

        make

   The executable file such as :code:`funwave_vessel` or :code:`mytvd` (specified in "Makefile", :code:`EXEC = executable_name`) will be generated in the :code:`/src/` folder.  **Note**: always use :code:`make clean` after modifying the "Makefile".  

   If you want to use a specific "Makefile" under a different name (e.g., "makefile-svg"), the command :code:`make -f "makefile-svg"` is used.

3. Run the model

   Modify "input.txt" as needed. An example "input.txt" file is presented on the :ref:`Definitions of Parameters <section-definitions>` page where you can review the available input options. Review the required variables for specific modules (e.g., shipwakes) on the :ref:`Examples <section-examples>` page.

   To run FUNWAVE locally, navigate to the directory containing the input files needed for your simulation and type the following command in your terminal: 

   .. code-block:: rest
       
        mpirun -np 4 /src/funwave_vessel

   Here, the parallel processing MPI is established and the number of processors, :code:`-np` is set to 4. This number will change depending on the capacity of your local machine. Next, the path to the FUNWAVE exectuable :code:`funwave_vessel` is called upon, and the model begins the simulation.

   If you are running FUNWAVE on a HPC machine . . .

************************************************************

========================
Download simple examples
========================

Simple examples are included in the package of Version 3.1 and higher (`click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_) . They are located in the directory :code:`/simple_cases/`. 
The simple examples serve as baseline cases for testing your system. You can also choose a simple case similar to your modeling scenario to set up your case. A brief list of examples are listed below; the full list of simple cases can be found :ref:`here <section-examples>`. These simple examples are also used during the FUNWAVE training workshop. 

* `Waves on 1D slope <slope.html>`_

* `Waves on 2D beach <beach_2d.html>`_

* `Waves and rip currents on 2D beach <rip_2d.html>`_

* `Sediment transport in 2D rip channels <sediment_rip.html>`_

* `Surface waves at an inlet-beach-shoal system <inlet_shoal.html>`_

* `Japanese Tohoku tsunami (Ocean-basin scale) <tohoku.html>`_

* `Ship-wakes <vessel.html>`_

* `Ship-wakes + sediment transport <vessel_morpho.html>`_

* `Meteotsunami <meteo.html>`_

========================
Download benchmark tests
========================

Benchmark tests are validation and verification (V\&V) cases with model comparisons with lab or field experiment data. `Available benchmarks: click here to download from GitHub <https://github.com/fengyanshi/BENCHMARK_FUNWAVE>`_





