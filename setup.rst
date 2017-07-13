**MODEL DOWNLOAD AND SETUP**
=============================

**********************
Download source code 
**********************


Version 3.0: Released Apr 2017 :download:`download here <versions/funwave_tvd_30.zip>`

`Version 3.1 (beta version): click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_

Versions 1.0, 1.1, 2.0, 2.1: Please contact fyshi@udel.edu

*************************
Download simple examples
*************************

Simple examples are included in the package of Version 3.1 or higher (`click here to download from GitHub <https://github.com/fengyanshi/FUNWAVE-TVD>`_) . They are located in the directory /simple_cases/. 
The simple examples serve as baseline cases for testing your system. You can also choose a simple case similar to your modeling scenario to set up your case. The following simple cases available. The simple examples are also used during the FUNWAVE training workshop. 

* `Waves on 1D slope <slope.html>`_

* `Waves on 2D beach <beach_2d.html>`_

* `Surface waves at an inlet-beach-shoal system <inlet_shoal.html>`_

* `Japanese Tohoku tsunami (Ocean-basin scale) <tohoku.html>`_

* `ship-wakes <vessel.html>`_

***************************
Download benchmark tests
***************************

Benchmark tests are validation and verification (V & V) cases with model comparisons with lab or field experiment data. `Available benchmarks: click here to download from GitHub <https://github.com/fengyanshi/BENCHMARK_FUNWAVE>`_


*************************
Compile and setup
*************************

1. uncompress the code from the package downloaded
2. modify *Makefile* if needed. There are several necessary flags in Makefile needed to specify below. 

* --DDOUBLE_PRECISION: use double precision, default is single precision.
* --DPARALLEL: use parallel mode, default is serial mode.
* --DCARTESIAN: Cartesian version, otherwise Spherical version
* --DINTEL: if INTEL compiler is used, this option can make use of FPORT for the RAND() function
* --DCRAY: for CRAY RAND() and system commands
* --DCOUPLING: nesting mode.
* --DVESSLE: include shipwake module
* CPP: path to CPP directory.
* FC: Fortran compiler. 

3. compile the code

in command line type

> make clean

> make

The executable file such as 'funwave' or 'mytvd' (specified in *Makefile*) will be generated.   **Note: always use 'make clean' after modifying Makefile**.  

4. run the model

Modify input.txt if needed and run. 



