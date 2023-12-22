.. _definition_breakwater:

Breakwater and Obstacle
**************************

**INTRODUCTION**

Native to FUNWAVE are the addition of obstacles and/or breakwaters in the model domain. These features can be either fully reflective (i.e., impermeable) or partially reflecting / partially absorbing (e.g., permeable). There are three ways to add a breakwater or obstacle to the model:

#. Modify the bathymetry directly, generating a raised *impermeable* feature in the along-shore beach profile (or cross-shore for jetties, groins, etc.). See an example of this at :ref:`example_bathy_breakwater`. Variable bottom friction can be added to increase roughness on and around the structure. 

#. Generate a breakwater file that defines the width of a *dissipative sponge layer* at a location on the grid, and define the corresponding absorption strength of the sponge layer in the ``input.txt`` file (``BreakWaterAbsorbCoef``). The internal sponge layer behaves as a dissipative surface felt throughout the water column, like a wire mesh of variable density. See an example of this at :ref:`example_partial_breakwater`.

#. Generate an obstacle file that specifies the location of an infinitely tall, *impermeable* wall (i.e., fully reflective) in the model domain. See an example of this at :ref:`example_obstacle`. 

These methods are not limited to breakwaters. Other structures of interest may include, but are not limited to, jetties, groins, revetments, and sea walls. These structure types and their configurations may be added to the numerical domain using similar techniques described above. Work is ongoing with the U.S. Army Engineer Research and Development Center to provide guidance and recommendations for these numerical parameters and how they relate to physical structure properties and expected wave responses. For more information, visit :ref:`info-structures`.

**SPECIFICATION OF OBSTACLES or BREAKWATER**

* :code:`OBSTACLE_FILE`: Name of obstacle file. 
       Obstacle file contains the same dimensions as the computational domain (Mglob, Nglob) with the same format. Values of 1 designate a water point, and values of 0 designate a permanent dry point. A full reflection condition is used at OBSTACLE points. 

* :code:`BREAKWATER_FILE`: Name of breakwater file. 
       Breakwater file contains the same dimenstions and format as the computational domain. Values of 0 designate non-breakwater points. The breakwater is specified in terms of its width (in meters). This width is not the breakwater width explicitly (from toe to toe), but rather the width of the sponge layer. Grid points with a non-zero value represent the center of the sponge layer, where the value represents a width to the left and right of that point (for 1D applications) or a radius around that grid point (for 2D applications). Ex: if 1D, a width of 30m corresponds to a sponge layer width of 15m to the left and right of that point; if 2D, a width of 30m corresponds to a circular sponge layer with radius 15m around the point. Overlapping grid points do not compound sponge strength.
	   
	   For a field case, use 10m - 30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Breakwater absorption is made by using large bottom friction locally (large :math:`Cd`) around breakwater points. The maximum :math:`Cd` is specified by :code:`BreakWaterAbsorbCoef`. **Default:** no breakwater.

* :code:`BreakWaterAbsorbCoef`: Value of maximum :math:`Cd`.
        This parameter provides the maximum :math:`Cd` in the bottom friction formulation at breakwater locations. The frictional dissipation is treated slightly differently than the quadratic drag formulation in the model. The **default** value is 10.0. 

        **Note**: for large waves (e.g., significant wave height > 10m) in the field case, a large parameter can cause imbalance of the momentum equations. Use a smaller parameter in a large wave case to avoid this issue. 



