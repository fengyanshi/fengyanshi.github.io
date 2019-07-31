.. _section-tohoku-lowres:

Tohoku Low Resolution 
#####################

.. figure:: images/simple_cases/tohoku_surface.jpg
    :width: 400px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center

Here you will add the initial conditions to describe the Tohoku tsunami. The tsunami source is constructed in Grilli et al. (2012), which is based on the 3D FEM model of Masterlark (2003), denoted UA source. The non-hydrostatic model NHWAVE (Ma et al., 2012) is used to simulate the first 5 min of tsunami generation, as in Grilli et al. (2012), using a smaller and finer local 1 km resolution Cartesian grid, based on the UA source. The NHWAVE results of u, v eta are used as the initial conditions for FUNWAVE-TVD.

 Set the initial deformation in UVZ:

 .. code-block:: rest

        !-----INITIAL UVZ-----
         INI_UVZ = T
         
         ! if true, input eta, u, v files names
         ETA_FILE = ../external_files/ETA_30min.txt
         U_FILE = ../external_files/U_30min.txt
         V_FILE = ../external_files/V_30min.txt

 Set the sponge layer width to 100,000 m on all boundaries, the shock-capturing breaking ratio to 0.6, and the bottom friction coefficient to 0.001:

 .. code-block:: rest

        !-----SPONGE LAYER-----
         DIRECT_SPONGE = T
         FRICTION_SPONGE = T
         Sponge_west_width =  100000.0    ! in meters
         Sponge_east_width =  100000.0
         Sponge_south_width = 100000.0
         Sponge_north_width = 100000.0
         
         SWE_ETA_DEP = 0.6
         Cd = 0.001

 Refer to :ref:`section-physics` and :ref:`sponge_definition` for parameter definitions.

 Set the CLF condition to 0.5 and maximum Froude number to 2.0:

 .. code-block:: rest

        !-----NUMERICS-----
         CFL = 0.5
         FroudeCap = 2.0

 Set the minimum depth of wetting-drying to 10.0, and the minimum depth for friction to 10.0:

 .. code-block:: rest

        !-----WET-DRY-----
         MinDepth = 10.0
         MinDepthFrc = 10.0

 Add a station file to write the output:

 .. code-block:: rest

        !-----OUTPUT-----
         NumberStations = 78
         STATIONS_FILE = stations-pacific.txt
         ETA = T
         Hmax = T








