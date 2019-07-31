.. _definition_output:

Output
******

**SPECIFICATION OF RESULT FOLDER**   
  
* :code:`RESULT_FOLDER`: result folder name, e.g., :code:`RESULT_FOLDER = /Users/tmp/`

**SPECIFICATION OF OUTPUT VARIABLES**

* :code:`NumberStations`: number of station for output. If NumberStations :math:`> 0`, need input i,j in :code:`STATION_FILE`
* :code:`DEPTH_OUT`: logical parameter for output depth. T or F. 
* :code:`U`: logical parameter for output u. T or F. 
* :code:`V`: logical parameter for output v. T or F. 
* :code:`ETA`: logical parameter for output :math:`\eta`. T or F. 
* :code:`MASK`: logical parameter for output wetting-drying MASK. T or F. 
* :code:`MASK9`: logical parameter for output MASK9 (switch for Boussinesq/NSWE). T or F. 
* :code:`SourceX`: logical parameter for output source terms in x direction. T or F. 
* :code:`SourceY`:  logical parameter for output source terms in y direction. T or F. 
* :code:`P`:  logical parameter for output of  momentum flux in x direction. T or F. 
* :code:`Q`:  logical parameter for output of  momentum flux in y direction. T or F. 
* :code:`Fx`: logical parameter for output of numerical flux F in x direction. T or F. 
* :code:`Fy`: logical parameter for output of numerical flux F in y direction. T or F. 
* :code:`Gx`: logical parameter for output of numerical flux G in x direction. T or F. 
* :code:`Gy`: logical parameter for output of numerical flux G in y direction. T or F. 
* :code:`AGE`: logical parameter for output of breaking age. T or F. 
* :code:`HMAX`: logical parameter for output of recorded maximum surface elevation . T or F. 
* :code:`HMIN`: logical parameter for output of recorded minimum surface elevation . T or F. 
* :code:`UMAX`: logical parameter for output of recorded maximum velocity . T or F. 
* :code:`VORMAX`: logical parameter for output of recorded maximum vorticity . T or F. 
* :code:`MFMAX`: logical parameter for output of recorded maximum momentum flux . T or F. 
* :code:`WaveHeight`: logical parameter for output of wave height, Hsig, Hrms, Havg. T or F.
* :code:`OUT_METEO`: logical parameter for output of pressure field. T or F.
* :code:`ROLLER`: logical parameter for output of roller-induced flux. T or F.
* :code:`UNDERTOW`: logical parameter for output of undertow. T or F.

**OUTPUT FILES**

The output files are saved in the result directory defined by :code:`RESULT_FOLDER` in "input.txt". Output file names are a combination of variable name and an output series number such as :code:`eta_00001, eta_00002, ....`. The format and read/write algorithm are consistent with a depth file. 

* CENTRAL module

 * :code:`eta_xxxxx`: surface elevation
 * :code:`u_xxxxx`: velocity in the x direction
 * :code:`v_xxxxx`: velocity in the y direction
 * :code:`mask_xxxxx`:  masks for wetting (1) and drying (0)
 * :code:`mask9_xxxxx`:  masks for wetting (1) and drying (0) defined in 9 points
 * :code:`hmax_xxxxx`: maximum surface elevation
 * :code:`hmin_xxxxx`: minimum surface elevation
 * :code:`umax_xxxxx`: maximum velocity
 * :code:`MFmax_xxxxx`: maximum momentum flux
 * :code:`VORmax_xxxxx`: maximum vertical vorticiy
 * :code:`p_xxxxx`: volume flux in the x direction
 * :code:`q_xxxxx`: volume flux in the y direction
 * :code:`nubrk_xxxxx`: breaking induced eddy vviscosity (when viscosity breaker is on)
 * :code:`etat_xxxxx`: :math:`\eta_t`
 * :code:`age_xxxxx`: breaking age (in seconds) 
 * :code:`roller_xxxxx`: roller-induced mass flux
 * :code:`U_undertow_xxxxx`: roller-induced extra undertow flux in the x direction
 * :code:`V_undertow_xxxxx`: roller-induced extra undertow flux in the y direction

* METEO module

 * :code:`Pstorm_xxxxx`: air pressure 
 * :code:`Ustorm_xxxxx`: wind velocity in the x direction
 * :code:`Vstorm_xxxxx`: wind velocity in the y direction

* VESSEL module

 * :code:`Fves_xxxxx`: gradient of mass flux induced by vessel (panel source) 
 * :code:`Pves_xxxxx`: pressure specified for the pressure source

* SEDIMENT module

 * :code:`C_xxxxx`: sediment concentration (g/l)
 * :code:`Pick_xxxxx`: pickup rate
 * :code:`Depo_xxxxx`: deposition rate
 * :code:`DchgS_xxxxx`: depth change in suspended load
 * :code:`DchgB_xxxxx`: depth change in bed load
 * :code:`BedFx_xxxxx`: bedload flux in the x direction
 * :code:`BedFy_xxxxx`: bedload flux in the y direction 
 * :code:`dep_xxxxx`:  depth

**Station files**

To get time series of surface elevation, u and v at interested locations, you can specify a station file which includes the locations for output. 

  * in "input.txt", add :code:`NumberStations = <integer number of stations>`
  * in "input.txt", :code:`STATION_FILE = <file name, e.g., gauges.txt>`
  * format of :code:`STATION_FILE`: two integers for grid points in x and y, respectively.

  Example: refer to :ref:`example_station_file`

Output for stations is a series of numbered files such as :code:`sta_0001, sta_0002 ....` (NOTE: four digit numbers here vs. five digit numbers for 2D output like :code:`eta_00001`).

 * ASCII format
   
   The default format is ASCII.  The format and read algorithm are  consistent with a depth file.

   A station file contains four columns, which are values of time (s), eta (m), u (m/s) and v (m/s), respectively. 


 * BINARY format

   When :code:`FIELD_IO_TYPE = BINARY` is specified in "input.txt", the 2D output files such as :code:`eta_00001, ...` are in the binary format. Here's an example of reading in:
 
   MATLAB:

   .. code-block:: python

          fileID = fopen('eta_00001');

          eta = fread(fileID,[Mglob Nglob],'*double');

          fclose(fileID);

          pcolor(eta),shading flat 

   PYTHON:

   .. code-block:: python

          def readBathyData(outputDir, args):
          """Function that reads in FUNWAVE's bathy data from: dep.out in output directory."""
          
          bathyFileName = os.path.join(outputDir, 'dep.out')

          # read in and convert into 2D numpy array if binary fieldiotype                                                                                                    
          fieldIOType = args.fieldiotype # 'ascii' or 'binary'                                                                                                               

          if fieldIOType == 'ascii':
             bathy = np.loadtxt(bathyFileName)
             (Ny, Nx) = bathy.shape # [Nglob,Mglob]                                                                                                                         

          else:
             Ny = args.nglob    # if not included in args, manually set Nx, Ny
             Nx = args.mglob
             fin = open(bathyFileName, mode='rb')
             dataType = np.dtype(['elev', '<f8', Ny*Nx])
             bathyNotParsed = np.fromfile(fin, dtype=dataType)
             bathy = np.zeros([Ny,Nx])
             for j in range(Nx):
              for i in range(Ny):
                  bathy[i,j] = bathyNotParsed[0][0][(j*Ny)+i]
                  return bathyta = np.loadtext('eta_00001')

          plt.plot()

  Station files do not have Binary format. 

 * Other format

   Other formats such as NetCDF and HDF5 are also provided but not distributed in the master Github repository. 


