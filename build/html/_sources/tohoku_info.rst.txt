.. _section-tohoku-basics:

Basics for model setup
######################

In the directory :code:`simple_cases/tohoku_tsunami/work/`, you will find the primary "input.txt" file for this example. Several external files are needed to define the initial conditions of the Tohoku tsunami. These files can be found in :code:`simple_cases/tohoku_tsunami/external_files/`.

**Computational domain**

.. figure:: images/simple_cases/tohoku_dem.jpg
    :width: 600px
    :align: center
    :height: 400px
    :alt: alternate text
    :figclass: align-center

**Setup in "input.txt"**

See an example of a complete "input.txt" :ref:`here <section-definitions>`.

For this example, you will set the following in "input.txt". **Remember that all parameters are case sensitive**.

 Set a descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = tohoku_tsunami

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 2
         PY = 2

 Set the bathymetry by using the provided depth file:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = DATA
         DEPTH_FILE = ../external_files/depth_30min.txt

 Send the results to a folder named "output":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output/

 The computational domain covers a region of the Pacific Ocean from 60°S to 60°N in the south-north direction, and from 132°E to 68°W in the west-east direction. The example is a 30min x 30min resolution case. The 2-min resolution result can be found in Kirby et al. (2013). Set the dimensions of the domain to 320 x 420:

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 320
         Nglob = 240
         
 Set the computational time, plot time, station printing interval and screen interval to 86,400.0 s, 3600.0 s, 1.0 s, and 3600.0 s, respectively.

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 86400.0
         PLOT_INTV = 3600.0
         PLOT_INTV_STATION = 1.0
         SCREEN_INTV = 3600.0

 Set the grid dimensions in spherical coordinates:

 .. code-block:: rest

        !-----GRID-----
         Lon_West = 132.0
         Lat_South = -60.0
         Dphi = 0.5
         Dtheta = 0.5

 Tsunami source: the tsunami source is constructed in Grilli et al. (2012), which is based on the 3D FEM model of Masterlark (2003), denoted UA source. The non-hydrostatic model NHWAVE (Ma et al., 2012) is used to simulate the first 5 min of tsunami generation, as in Grilli et al. (2012), using a smaller and finer local 1 km resolution Cartesian grid, based on the UA source. The NHWAVE results of u, v eta are used as the initial conditions for FUNWAVE-TVD. 

 The remaining parameters are defined in :ref:`section-tohoku-lowres`.

  
**Postprocessing**

 For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/tohoku_tsunami/postprocessing/`.

