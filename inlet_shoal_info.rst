.. _section-inlet-basics:

Basics for model setup
######################


In the directory :code:`/simple_cases/inlet_shoal/input_files/`, you will find multiple instances of input files that are specific to different variations of this example, e.g., regular ("input\_reg.txt) versus irregular ("input\_irr.txt") wavemaker configuration. It should be noted that the model will accept only the file named "input.txt". Therefore, if you want to switch wavemaker cases, you will need to modify the primary "input.txt" file.


**Computational domain**

.. figure:: images/simple_cases/inlet_shoal.jpg
    :width: 400px
    :align: center
    :height: 500px
    :alt: alternate text
    :figclass: align-center

**Setup in "intput.txt"**

See an example of a complete "input.txt" :ref:`here <section-definitions>`.

For this example, you will set the following in "input.txt". **Remember that all parameters are case sensitive**.

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 8
         PY = 16

 Set the bathymetry to match the figure above using the depth file provided in :code:`/simple_cases/inlet_shoal/bathy`:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = DATA
         DEPTH_FILE = ../bathy/dep_shoal_inlet.txt

 Refer to :ref:`definition_grid` for parameter definitions. For optional bathymetry correction, review :ref:`bathymetry_correction`.

 Send the results to a folder named "output":

 .. code-block:: rest

        !-----PRINT-----
         RESULT_FOLDER = output/

 Set the dimensions of the domain to 512 X 1024 (x and y directions, respectively):

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 512
         Nglob = 1024

 Set the total computational time, plot time, and screen interval to 1200.0 s, 30.0 s, and 30.0 s, respectively. If printing to a station file, set the print time to 0.5 s:

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 1200.0
         PLOT_INTV = 30.0
         SCREEN_INTV = 30.0
         PLOT_INTV_STATION = 0.5

 Set the grid spactin in x and y to 2.0 m:

 .. code-block:: rest

        !-----GRID-----
         DX = 2.0 m
         DY = 2.0 m

 **Wavemaker**

 Wavemaker parameters will be defined on the respective case pages: :ref:`section-inlet-reg`, :ref:`section-inlet-reg30`, :ref:`section-inlet-irr`, :ref:`section-inlet-irr30`, :ref:`section-inlet-irr30-obs`, :ref:`section-inlet-irr30-brk`, and :ref:`section-inlet-irr30-brk-ref`.

 Set the periodic boundary condition to TRUE:

 .. code-block:: rest

        !-----PERIODIC BOUNDARY CONDITION-----
         PERIODIC = T
         
 (refer to :ref:`info_periodic` for an example)

 Set the sponge layer width to 180 m on the left boundary:

 .. code-block:: rest

        !-----SPONGE LAYER-----
         DIFFUSION_SPONGE = F
         FRICTION_SPONGE = T
         DIRECT_SPONGE = T
         Csp = 0.0
         CDsponge = 1.0
         Sponge_west_width = 180.0
         Sponge_east_width = 0.0
         Sponge_south_width = 0.0
         Sponge_north_width = 0.0

 (refer to :ref:`info_sponge` for example of 2D sponge case)
 
 **Keep the default values** for the :code:`PHYSICS, NUMERICS, WET-DRY,` and :code:`BREAKING` sections. Refer to :ref:`section-definitions` for a description of all parameters.

 Set the wave average properties as follows:

 .. code-block:: rest

        !-----WAVE AVERAGE-----
         T_INTV_mean = 240.0
         STEADY_TIME = 480.0

 Set the following output files to TRUE:

 .. code-block:: rest

        !-----OUTPUT-----
         ETA = T
         MASK = T
         WaveHeight = T

 (refer to :ref:`definition_output` for parameter definitions)

Several "input.txt" files are located in the folder :code:`/simple_cases/inlet_shoal/input_files/` for different cases. When running on of the cases listed below, copy the wavemaker parameters from the respective file to the primary "input.txt" file:

 * Case 1: monochromatic wave, normal incidence -- "input_reg.txt"

 * Case 2: monochromatic wave, 30-degree incidence -- "input_reg_30deg.txt" 

 * Case 3: irregular waves, peak direction - 0.0  -- "input_irr.txt" 

 * Case 4: irregular waves, peak direction - 30.0 -- "input_irr_30deg.txt"

 * Case 5: irregular waves, peak direction - 30.0, plus an obstacle (breakwater) -- "input_irr_30deg_obs.txt" 

 * Case 6: irregular waves, peak direction - 30.0, plus submerged breakwater with partial reflection (full reflection if removing breakwater file (brk_shoal_inlet.txt) in the input file) -- "input_irr_30deg_brkwtr.txt"

Similarly, additional bathymetry files are provided in the folder :code:`/simple_cases/inlet_shoal/bathy/` to represent each case above. 

  
 * dep_shoal_inlet.txt  -- basic bathymetry

 * dep_shoal_inlet_brk.txt  -- bathymetry with a breakwater geometry

 * brk_shoal_inlet.txt -- same format as bathymetry file but only contains breakwater width info

 * obs_shoal_inlet.txt -- same format as bathymetry file but only contains 0 or 1, with 0 indicating an obstacle point

**Postprocessing**

  For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/inlet_shoal/postprocessing/`.

