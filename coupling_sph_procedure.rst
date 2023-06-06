Coupling procedure
**********************************

The case has two grids in the spherical system, the coarse grid (GRID A) and fine grid (GRID B). GRID B is nested in GRID A at i = 500 (point). A solitary wave is specified in GRID A as the initial condition. 

* Run GRID A using funwave_nocoupling compiled without -DCOUPLING. Specify a station file 'station.txt' for output at the coupling boundaries. 
* Make a coupling file 'coupling.txt' using the output from GRID A.
* Run GRID B using funwave_coupling compiled with -DCOUPLING. Specify the coupling file 'coupling.txt' in input.txt.