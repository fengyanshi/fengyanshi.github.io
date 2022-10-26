.. _section-tide:

Tide and Surge Boundary Conditions
************************************

**SPECIFICATION OF TIDE AND SURGE OPEN BOUNDARY CONDITIONS** 

* :code:`TIDAL_BC_ABS`: logical parameter for tidal absorbing boundary conditions, T - tide and surge at open boundaries, F - no tide or surge.

* :code:`TIDAL_BC_GEN_ABS`: logical parameter for the combined tidal and absorbing-generating boundary conditions, T - ture, F - false.

* :code:`TideBcType`: string parameter for data types. Default: TideBcType = CONSTANT

* :code:`TideWest_ETA`: constant eta value at the WEST boundary.

* :code:`TideWest_U`: constant u value at the WEST boundary, defalut: 0.0. 

* :code:`TideWest_V`: constant v value at the WEST boundary, defalut: 0.0. 

* :code:`TideEast_ETA`: constant eta value at the EAST boundary.

* :code:`TideEast_U`: constant u value at the EAST boundary, defalut: 0.0. 

* :code:`TideEast_V`: constant v value at the EAST boundary, defalut: 0.0.

* :code:`TideSouth_ETA`: constant eta value at the SOUTH boundary.

* :code:`TideSouth_U`: constant u value at the SOUTH boundary, defalut: 0.0. 

* :code:`TideSouth_V`: constant v value at the SOUTH boundary, defalut: 0.0.

* :code:`TideNorth_ETA`: constant eta value at the NORTH boundary.

* :code:`TideNorth_U`: constant u value at the NORTH boundary, defalut: 0.0. 

* :code:`TideNorth_V`: constant v value at the NORTH boundary, defalut: 0.0.

* :code:`TideWestFileName`: file name for WEST boundary data.

* :code:`TideEastFileName`: file name for EAST boundary data.

* :code:`TideSouthFileName`: file name for SOUTH boundary data.

* :code:`TideNorthFileName`: file name for NORTH boundary data. 

Examples can be found in /simple_cases/, or see `Tidal module <https://fengyanshi.github.io/build/html/tide_module.html>`_  


 

