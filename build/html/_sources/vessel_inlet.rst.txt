.. _section-vessel-inlet:

Interaction between wind waves and ship-wakes in an inlet system 
################################################################

In this example, you will add a vessel to the :ref:`section-inlet-irr30` example. You will use the :code:`input_irr_30deg_ship.txt` input file located in :code:`/simple_cases/inlet_shoal/input_files/` -- remember to rename this file, or copy the file contents, into a file named "input.txt". The bathymetry to use is :code:`/simple_cases/inlet_shoal/bathy/dep_shoal_inlet.txt`.

**Computational domain**

.. figure:: images/simple_cases/ship_inlet_path.jpg
    :width: 250px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

**Setup "input.txt"**

Refer to :ref:`section-inlet-basics` for the domain setup, and :ref:`section-inlet-irr30` for wavemaker setup.

 Set descriptive title for this simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = vessel_inlet

 Add a vessel with the following characteristics:

 .. code-block:: rest

        !-----SHIP WAKES-----
         VESSEL_FOLDER = ./
         NumVessel = 1
         
 In :code:`vessel_00001`, specify:

  .. code-block:: rest

        Title: Vessel # 1
        Pressure, 1
        Length(m), Width(m), Alpha1(m),Alpha2(m), Beta(m), P(unit)
        10.0  5.0, 0.5, 0.5, 0.5, 2.0
        Time, X(m), Y(m)  (relative to the origin of the coordinates)
        0.0   900.0   0.0
        150.0 900.0   0.0
        250.0 900.0   1000.0
        1000.0 -6600  1000.0

 (refer to :ref:`theory_shipwakes` and :ref:`section-shipwakes-setup` for more information)

**Postprocessing**

For postprocessing examples, MATLAB and Python scripts are located in :code:`/simple_cases/inlet_shoal/postprocessing/`.

.. figure:: images/simple_cases/ship_inlet_waves.jpg
    :width: 400px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center




