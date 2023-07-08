.. _definition_breakwater:

Breakwater and Obstacle
**************************

**INTRODUCTION**

Native to FUNWAVE are the addition of obstacles and/or breakwaters in the model domain. These features can be either fully reflective (i.e., impermeable) or partially reflecting / partially absorbing (e.g., permeable). There are three ways to add a breakwater or obstacle to the model:

#. Modify the bathymetry directly, generating a raised *impermeable* feature in the along-shore beach profile (or cross-shore for jetties, groins, etc.). See an example of this at :ref:`example_bathy_breakwater`.

#. Generate a breakwater file that defines the width of a *dissipative sponge layer* at a location on the grid, and define the corresponding absorption strength of the sponge layer in the ``input.txt`` file. The dissipative sponge layer behaves as a friction-type layer to the incoming waves - similar to (but not exactly the same as) adding a strong bottom friction in the area. See an example of this at :ref:`example_partial_breakwater`.

#. Generate an obstacle file that specifies the location of an infinitely tall, *impermeable* wall (i.e., fully reflective) in the model domain. See an example of this at :ref:`example_obstacle`. 

More details about the specification of the breakwater and obstacle files are presented in the following section.

A potential fourth method for incorporating a breakwater in the model domain involves the combination of options one and two – modifying the bathymetry to some extent and adding/defining the dissipative sponge layer over the raised feature. This method would essentially simulate a permeable structure of variable strength or *porosity* with an impermeable core. 

Several structure properties are available for simulation in the FUNWAVE numerical model. These properties include:

* Smooth versus rough slope

       * Through the incorporation of the bottom friction coefficient `Cd` over an impermeable feature defined via bathymetric modification, a rough structure surface can be added to the feature.

* Impermeable versus permeable

       * Utilizing a dissipative sponge layer of variable strength in the numerical domain allows for the simulation of a permeable or porous structure surface in the wave field.

* Emergent versus submerged

       * The height of the breakwater or coastal feature relative to the total water depth is variable, and as such the overall wave responses will differ greatly for a fully submerged breakwater compared to an emergent breakwater.

These methods are not limited to breakwaters. Other structures of interest may include, but are not limited to, jetties, groins, revetments, and sea walls. These structure types and their configurations may be added to the numerical domain using similar techniques described above. Work is ongoing with the U.S. Army Engineer Research and Development Center to provide guidance and recommendations for these numerical parameters and how they relate to physical structure properties and expected wave responses. For more information, visit :ref:`info-structures`.

**SPECIFICATION OF OBSTACLES or BREAKWATER**

* :code:`OBSTACLE_FILE`: Name of obstacle file. 
       Obstacle file contains the same dimensions as the computational domain (Mglob, Nglob) with the same format. Values of 1 designate a water point, and values of 0 designate a permanent dry point. A full reflection condition is used at OBSTACLE points. 

* :code:`BREAKWATER_FILE`: Name of breakwater file. 
       Breakwater file contains the same dimenstions and format as the computational domain. Values of 0 designate non-breakwater points. The breakwater is specified in terms of its width (in meters). This width is not the breakwater width explicitly (from toe to toe), but rather the width of the sponge layer. Cells with a non-zero value represent the center of the sponge layer, where the value represents a width to the left and right of that cell (for 1D applications) or a radius around that cell (for 2D applications). Ex: if 1D, a width of 30m corresponds to a sponge layer width of 15m to the left and right of that cell; if 2D, a width of 30m corresponds to a circular sponge layer with radius 15m around the cell. No partial cells are considered.
	   
	   For a field case, use 10m - 30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Breakwater absorption is made by using large bottom friction locally (large :math:`Cd`) around breakwater points. The maximum :math:`Cd` is specified by :code:`BreakWaterAbsorbCoef`. **Default:** no breakwater.

* :code:`BreakWaterAbsorbCoef`: Value of maximum :math:`Cd`.
        This parameter provides the maximum :math:`Cd` in the bottom friction formulation at breakwater locations. The frictional dissipation is treated slightly differently than the quadratic drag formulation in the model. The **default** value is 10.0. 

        **Note**: for large waves (e.g., significant wave height > 10m) in the field case, a large parameter can cause imbalance of the momentum equations. Use a smaller parameter in a large wave case to avoid this issue. 



