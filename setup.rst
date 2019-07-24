.. _section-download:

MODEL DOWNLOAD AND SETUP
************************

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
   
    We recommend that you download the latest version of Cygwin (`<https://www.cygwin.com>`_). Cygwin is a bash shell/unix emulation program, and contains many of the tools such as :code:`tar, gzip/gunzip, and cpp`, which will be useful for installation and compilation of FUNWAVE-TVD. In addtion, if you don't have access to a High Performance Computing (HPC) machine at your home location, it is recommended you use the :ref:`Amazon AWS Cloud Computing <section-aws-computing>`.

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

`Version 3.3 Released July 19 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

`Version 3.2 Released Jan 27 2018: click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.1 Released Sep 2017: Used for FUNWAVE-TVD Workshop 2017 `click here to download <https://github.com/fengyanshi/FUNWAVE-TVD/releases>`_

Version 3.0: Released Apr 2017 :download:`download here <versions/funwave_tvd_30.zip>`

Versions 1.0, 1.1, 2.0, 2.1: Please contact fyshi@udel.edu

***********************************************************

=================
Compile and setup
=================

1. Uncompress the code from the package downloaded
2. Modify :code:`Makefile` if needed. There are several necessary flags in Makefile needed to specify below. 
 
 * :code:`-DDOUBLE_PRECISION`: use double precision, default is single precision.
 * :code:`-DPARALLEL`: use parallel mode, default is serial mode.
 * :code:`-DCARTESIAN`: Cartesian version, otherwise Spherical version
 * :code:`-DINTEL`: if INTEL compiler is used, this option can make use of FPORT for the RAND() function
 * :code:`-DCRAY`: for CRAY RAND() and system commands
 * :code:`-DCOUPLING`: nesting mode.
 * :code:`-DSPHERICAL_IJ_STATION`: in spherical mode, if you want your station locations defined by grid point (I,J). Otherwise, station locations should be defined by (lat lon).  
 * :code:`-DVESSEL`: include shipwake module
 * :code:`-DSEDIMENT`: include sediment and morphological module
 * :code:`-DWIND`: include wind effect
 * :code:`-DMETEO`: include meteo tsunami module
 * :code:`-DMANNING`: use Manning formula for bottom friction
 * :code:`-DCHECK_MASS_CONSERVATION`: correct mass conservation problem caused by wetting/drying
 * :code:`-DTRACKING`: include Lagrangian tracking module
 * :code:`CPP`: path to CPP directory.
 * :code:`FC`: Fortran compiler. 


3. Compile the code

   The command :code:`make`, by default, will look for a file named "Makefile" in the current directory. It will read the contents of the file to find the target program or project that needs to be built (i.e., compiled). Generally, once a program is compiled, an executable file is generated. Any changes made to the source file (e.g., "Makefile") will need to be re-compiled, and a new executable will need to be generated. To clean, or remove, the files generated by the makefile and create new ones, the :code:`make clean` command is used prior to compiling with :code:`make`.
   
   In your terminal, navigate to the directory :code:`/src/` containing the file :code:`Makefile`, and type the following:
   
   .. code-block:: rest
        
        make clean

        make

   The executable file such as :code:`funwave` or :code:`mytvd` (specified in :code:`Makefile`) will be generated.   **Note**: always use :code:`make clean` after modifying the makefile.  

   If you want to use a specific "Makefile" under a different name (e.g., "makefile-svg"), the command :code:`make -f "makefile-svg"` is used.

4. Run the model

   Modify :code:`input.txt` if needed and run.


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





