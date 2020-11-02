.. _definition_breakwater:

Breakwater and Obstacle
**************************

**INTRODUCTION**

Native to FUNWAVE are the addition of obstacles and/or breakwaters in the model domain. These features can be either fully reflective (i.e., impermeable) or partially reflecting / partially absorbing (e.g., permeable). There are three ways to add a breakwater or obstacle to the model:

#. Modify the bathymetry directly, generating a raise *impermeable* feature in the along-shore beach profile (or cross-shore for jetties, groins, etc.)

#. Generate a breakwater file that defines the width of a *dissipative sponge layer* at a location on the grid, and define the corresponding absorption strength of the sponge layer in the ``input.txt`` file. The dissipative sponge layer behaves as a frictional dissipative layer to the incoming waves.

#. Generate an obstacle file that specifies the location of an infinitely tall, *impermeable* wall (i.e., fully reflective) in the model domain.

More details about the specification of the breakwater and obstacle files are presented in the following section.

A potential fourth method for incorporating a breakwater in the model domain involves the combination of options one and two – modifying the bathymetry to some extent and adding/defining the dissipative sponge layer over the raised feature. This method would essentially simulate a permeable structure of variable strength or *porosity* with an impermeable core.

Several structure properties are available for simulation in the FUNWAVE numerical model. These properties include:

* Smooth versus rough slope

       * Through the incorporation of the bottom friction coefficient `Cd` over an impermeable feature defined via bathymetric modification, a rough structure surface can be added to the feature.

* Impermeable versus permeable

       * Utilizing a dissipative sponge layer of variable strength in the numerical domain allows for the simulation of a permeable or porous structure surface in the wave field.

* Emergent versus submerged

       * The height of the breakwater or coastal feature relative to the total water depth is variable, and as such the overall wave responses will differ greatly for a fully submerged breakwater compared to an emergent breakwater.

**SPECIFICATION OF OBSTACLES or BREAKWATER**

* :code:`OBSTACLE_FILE`: Name of obstacle file. 
       Obstacle file contains the same dimensions as the computational domain (Mglob, Nglob) with the same format. Values of 1 designate a water point, and values of 0 designate a permanent dry point. A full reflection condition is used at OBSTACLE points. 

* :code:`BREAKWATER_FILE`: Name of breakwater file. 
       Breakwater file contains the same dimenstions and format as the computational domain. Values of 0 designate non-breakwater points. The breakwater is specified in terms of its width (in meters). The width is not the breakwater width explicitly, but the width of a sponge layer placed at the breakwater points. For a field case, use 10m - 30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Breakwater absorption is made by using large bottom friction locally (large :math:`Cd`) around breakwater points. The maximum :math:`Cd` is specified by :code:`BreakWaterAbsorbCoef`. **Default:** no breakwater.

* :code:`BreakWaterAbsorbCoef`: Value of maximum :math:`Cd`.
        This parameter provides the maximum :math:`Cd` in the bottom friction formulation at breakwater locations. The **default** value is 10.0. 

        **Note**: for large waves (e.g., significant wave height > 10m) in the field case, a large parameter can cause imbalance of the momentum equations. Use a smaller parameter in a large wave case to avoid this issue. 



