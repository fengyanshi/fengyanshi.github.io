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

We are preparing some simple examples for testing your system. If you want to make a test now, please visit **Download Benchmark tests** 

* Solitary wave propagation on a flat bottom
* Solitary wave propagation on a conical island
* Japanese Tohoku tsunami (Ocean-basin scale)
* Waves and wave-induced current on a beach

***************************
Download benchmark tests
***************************

`Available benchmarks: click here to download from GitHub <https://github.com/fengyanshi/BENCHMARK_FUNWAVE>`_


*************************
Compile and setup
*************************

1. uncompress the code from the package downloaded
2. modify *Makefile* if needed. There are several necessary flags in Makefile needed to specify below.

* --DDOUBLE_PRECISION: use double precision, default is single precision.
* --DPARALLEL: use parallel mode, default is serial mode.
* --DSAMPLES: include all samples, default is no sample included.
* --DCARTESIAN: Cartesian version, otherwise Spherical version
* --DINTEL: if INTEL compiler is used, this option can make use of FPORT for the RAND() function
* --DCRAY: for CRAY RAND() and system commands
* --DMIXING: include Smagorinsky mixing. 
* --DCOUPLING: nesting mode.
* --DMANNING: Using Manning coefficient for friction calculation.
* CPP: path to CPP directory.
* FC: Fortran compiler. 

3. compile the code

in command line type

> make clean

> make

The executable file such as 'funwave' or 'mytvd' (specified in *Makefile*) will be generated.   Note: always use 'make clean' after modifying Makefile.  

4. run the model

Modify input.txt if needed and run. 



