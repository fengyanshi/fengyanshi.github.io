.. _definition_output:

Output
**********

**SPECIFICATION OF RESULT FOLDER**   
  
 *  RESULT\_FOLDER: result folder name, e.g., RESULT\_FOLDER = /Users/tmp/

**SPECIFICATION OF OUTPUT VARIABLES**

 * NumberStations: number of station for output. If NumberStations :math:`> 0`, need input i,j in STATION\_FILE
 *  DEPTH\_OUT: logical parameter for output depth. T or F. 
 *  U: logical parameter for output u. T or F. 
 *   V: logical parameter for output v. T or F. 
 *  ETA: logical parameter for output :math:`\eta`. T or F. 
 *  MASK: logical parameter for output wetting-drying MASK. T or F. 
 *  MASK9: logical parameter for output MASK9 (switch for Boussinesq/NSWE). T or F. 
 *  SourceX: logical parameter for output source terms in x direction. T or F. 
 *  SourceY:  logical parameter for output source terms in y direction. T or F. 
 *  P:   logical parameter for output of  momentum flux in x direction. T or F. 
 *  Q:  logical parameter for output of  momentum flux in y direction. T or F. 
 *  Fx: logical parameter for output of numerical flux F in x direction. T or F. 
 *   Fy: logical parameter for output of numerical flux F in y direction. T or F. 
 *  Gx: logical parameter for output of numerical flux G in x direction. T or F. 
 *  Gy: logical parameter for output of numerical flux G in y direction. T or F. 
 *  AGE: logical parameter for output of breaking age. T or F. 
 *  HMAX: logical parameter for output of recorded maximum surface elevation . T or F. 
 *  HMIN: logical parameter for output of recorded minimum surface elevation . T or F. 
 *  UMAX: logical parameter for output of recorded maximum velocity . T or F. 
 *  VORMAX: logical parameter for output of recorded maximum vorticity . T or F. 
 *  MFMAX: logical parameter for output of recorded maximum momentum flux . T or F. 
 *  WaveHeight: logical parameter for output of wave height, Hsig, Hrms, Havg. T or F.
 *  OUT_METEO: logical parameter for output of pressure field. T or F.
 *  ROLLER: logical parameter for output of roller-induced flux. T or F.
 *  UNDERTOW: logical parameter for output of undertow. T or F.

**OUTPUT FILES**

The output files are saved in the result directory defined by RESULT\_FOLDER in input.txt.  

 *Output file names*

A file name is a combination of variable name and an output series number such as eta\_00001, eta\_00002, .... The format  and read/write algorithm are  consistent with a depth file. 

  **CENTRAL module**

 * eta\_xxxxx : surface elevation
 * u\_xxxxx : velocity in the x direction
 * v\_xxxxx : velocity in the y direction
 * mask\_xxxxx:  masks for wetting (1) and drying (0)
 * mask9\_xxxxx:  masks for wetting (1) and drying (0) defined in 9 points
 * hmax\_xxxxx: maximum surface elevation
 * hmin\_xxxxx: minimum surface elevation
 * umax\_xxxxx: maximum velocity
 * MFmax\_xxxxx: maximum momentum flux
 * VORmax\_xxxxx: maximum vertical vorticiy
 * p\_xxxxx: volume flux in the x direction
 * q\_xxxxx: volume flux in the y direction
 * nubrk\_xxxxx: breaking induced eddy vviscosity (when viscosity breaker is on)
 * etat\_xxxxx: :math:`\eta_t`
 * age\_xxxxx: breaking age (in seconds) 
 * roller\_xxxxx: roller-induced mass flux
 * U\_undertow\_xxxxx: roller-induced extra undertow flux in the x direction
 * V\_undertow\_xxxxx: roller-induced extra undertow flux in the y direction

  **METEO module**

 * Pstorm\_xxxxx: air pressure 
 * Ustorm\_xxxxx: wind velocity in the x direction
 * Vstorm\_xxxxx: wind velocity in the y direction

  **VESSEL module**

 * Fves\_xxxxx: gradient of mass flux induced by vessel (panel source) 
 * Pves\_xxxxx: pressure specified for the pressure source

  **SEDIMENT module**

 * C\_xxxxx: sediment concentration (g/l)
 * Pick\_xxxxx: pickup rate
 * Depo\_xxxxx: deposition rate
 * DchgS\_xxxxx: depth change in suspended load
 * DchgB\_xxxxx: depth change in bed load
 * BedFx\_xxxxx: bedload flux in the x direction
 * BedFy\_xxxxx: bedload flux in the y direction 
 * dep\_xxxxx:  depth

 *Station files*

To get time series of surface elevation, u and v at interested locations, you can specify a station file which includes the locations for output. 

  * in input.txt, add NumberStations = <integer number of stations>
  * in input.txt, STATION\_FILE = <file name, e.g., gauges.txt>
  * format of STATION\_FILE: two integers for grid points in x and y, respectively.

  Example: refer to :ref:`example_station_file`

Output for stations is a series of numbered files such as sta\_0001, sta\_0002 .... (NOTE: four digit numbers here vs. five digit numbers for 2D output like eta\_00001).

 * ASCII format

The default format is ASCII.  The format and read algorithm are  consistent with a depth file.

A station file contains four columns, which are values of time (s), eta (m), u (m/s) and v (m/s), respectively. 


 * BINARY format

When FIELD\_IO\_TYPE = BINARY is specified in input.txt, the 2D output files such as eta\_00001, ... are in the binary format. Here's an example of reading in matlab:


>>fileID=fopen('eta\_00001');

>>eta=fread(fileID,[Mglob Nglob],'\*double');

>>fclose(fileID);

>>pcolor(eta),shading flat 

Station files do not have Binary format. 


 * Other format

Other formats such as NetCDF and HDF5 are also provided but not distributed in the master Github repository. 


