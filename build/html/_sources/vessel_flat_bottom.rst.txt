.. _section-vessel-flat:

Two vessels with different speeds 
#################################

The first example of adding vessel dynamics is for two vessels with different speeds over a flat bottom. The primary "input.txt" and vessel files are located in :code:`simple_cases/vessel_flat_bottom/`. Refer to :ref:`theory_shipwakes` for a review of vessel types.

**Model setup**

.. figure:: images/simple_cases/layout_two_vessels.jpg
    :width: 500px
    :align: center
    :height: 200px
    :alt: alternate text
    :figclass: align-center

**Setup in input.txt:**

 Set a descriptive title for your simulation:

 .. code-block:: rest
 
        !-----TITLE-----
         TITLE = vessel_flat

 If running in parallel, set the number of processors in X and Y:

 .. code-block:: rest

        !-----PARALLEL INFO-----
         PX = 4 
         PY = 1


 Set the bathmetry to a flat bottom of depth 10.0 m:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = FLAT
         DEPTH_FLAT = 10.0

 (refer to :ref:`definition_grid` for parameter definitions)


 Send the results to a folder named "output":
 
 .. code-block:: rest
 
        !-----PRINT-----
         RESULT_FOLDER = output/
         
 Set the dimensions of the domain to 500 X 100 (x and y directions, respectively):

 .. code-block:: rest

        !-----DIMENSION-----
         Mglob = 500
         Nglob = 100

 Set the total computation time, plot time, station print interval and screen interval to 50.0 s, 1.0, 50,000.0 s, and 1.0 s, respectively:

 .. code-block:: rest

        !-----TIME-----
         TOTAL_TIME = 50.0
         PLOT_INTV = 1.0
         PLOT_INTV_STATION = 50000.0
         SCREEN_INTV = 1.0

 Set the grid spacing in x and y to 1.0 m:

 .. code-block:: rest

        !-----GRID-----
         DX = 1.0
         DY = 1.0
 
 Instead of adding a wavemaker, you will add the number of vessels to include and the path to the vessel files:

 .. code-block:: rest

        !-----SHIP WAKES-----
         VESSEL_FOLDER = ./
         NumVessel = 2
 
 You will need two vessel files: :code:`vessel_00001` and :code:`vessel_00002` in the working folder. In :code:`vessel_00001`, specify:

  .. code-block:: rest

        Title: Vessel # 1
        Pressure, 1
        Length(m), Width(m), Alpha1(0.5),Alpha2(0.5), Beta(0.5), P(draft,m)
        10.0  5.0, 0.5, 0.5, 0.5, 2.0
        Time, X(m), Y(m)  (relative to the orgin of the coordinates)
        0.0   50.0   40.0
        100.0 1050.0 40.0
        
 In :code:`vessel_00002`, specify:

  .. code-block:: rest
 
        Title: Vessel # 2
        Pressure, 1
        Length(m), Width(m), Alpha1(0.5),Alpha2(0.5), Beta(0.5), P(draft,m)
        20.0  8.0, 0.5, 0.5, 0.5, 3.0
        Time, X(m), Y(m)  (relative to the orgin of the coordinates)
        0.0   450.0   60.0
        100.0 -50.0   60.0

  (refer to :ref:`theory_shipwakes` and :ref:`section-shipwakes-setup` for more information)

 Set the :code:`ETA` output parameter to true:
 
 .. code-block:: rest

        !-----OUTPUT-----
         ETA = T

**Postprocessing**

For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/vessel_flat_bottom/`. Using :code:`plot_wave_vessel.m` the model result should look like the figure below.

.. figure:: images/simple_cases/two_vessels.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center




