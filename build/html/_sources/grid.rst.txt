Grid and Computational Time
*****************************

**SPECIFICATION OF DIMENSION**

 *  Mglob: global dimension in x direction.

 *  Nglob: global dimension in y direction.

**PECIFICATION OF GRID SIZE**

 *  DX: grid size(m) in x direction.

 *  DY:   grid size(m) in y direction.

**SPECIFICATION OF WATER DEPTH**
 
 *  DEPTH\_TYPE: depth input type. 

   DEPTH\_TYPE=DATA: from a depth file. 
   
   The program includes several simple bathymetry configurations such as
   
      DEPTH\_TYPE=FLAT:  flat bottom, need DEPTH\_FLAT 
                
      DEPTH\_TYPE=SLOPE:  plane beach along x direction. It needs three parameters: slope,SLP,  slope starting point, Xslp and flat part of depth, DEPTH\_FLAT

 *   DEPTH\_FILE: bathymetry file if  DEPTH\_TYPE=DATA, file dimension should be Mglob x Nglob with the first point as the south-west corner.  The read format in the code is shown below.

       DO J=1,Nglob
       
        READ(1,*)(Depth(I,J),I=1,Mglob)
        
       ENDDO
 
 *  DEPTH\_FLAT: water depth of flat bottom if DEPTH\_TYPE=FLAT or DEPTH\_TYPE=SLOPE (flat part of a plane beach).
 
 *  SLP: slope if DEPTH\_TYPE=SLOPE

 *  Xslp: starting x (m) of a slope, if DEPTH\_TYPE=SLOPE

 *  WaterLevel: Specify a water level which will be added to the input bathymetry and wavemaker depth such as DEP_WK (internal wave generator) and DepthWaveMaker (left boundary generator).

**SPECIFICATION OF TIME**
 
 *  TOTAL\_TIME: simulation time in seconds

 *  PLOT\_INTV: output interval in seconds (Note, output time is not exact because adaptive dt is used.)

 *  SCREEN\_INTV: time interval (s) of screen print. 

 *  PLOT\_INTV\_STATION: time interval (s) of gauge output

 *  DT_fixed: time step (s) if use fixed DT. But DT_fixed will be checked by CFL. IF not satisfy CLF, DT/2, DT/4 ... will be checked until it satisfy CFL. Default is using variable DT based on CFL. 



