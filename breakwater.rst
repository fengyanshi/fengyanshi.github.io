.. _definition_breakwater:

Breakwater and Obstacle
**************************

**SPECIFICATION OF OBSTACLES or BREAKWATER**

* :code:`OBSTACLE_FILE`: Name of obstacle file. 
       Obstacle file contains the same dimensions as the computational domain (Mglob, Nglob) with the same format. Values of 1 designate a water point, and values of 0 designate a permanent dry point. A full reflection condition is used at OBSTACLE points. 

* :code:`BREAKWATER_FILE`: Name of breakwater file. 
       Breakwater file contains the same dimenstions and format as the computational domain. Values of 0 designate non-breakwater points. The breakwater is specified in terms of its width (in meters). The width is not the breakwater width explicitly, but the width of a sponge layer placed at the breakwater points. For a field case, use 10m - 30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Breakwater absorption is made by using large bottom friction locally (large :math:`Cd`) around breakwater points. The maximum :math:`Cd` is specified by :code:`BreakWaterAbsorbCoef`. **Default:** no breakwater.

* :code:`BreakWaterAbsorbCoef`: Value of maximum :math:`Cd`.
        This parameter provides the maximum :math:`Cd` in the bottom friction formulation at breakwater locations. The **default** value is 10.0. 

        **Note**: for large waves (e.g., significant wave height > 10m) in the field case, a large parameter can cause imbalance of the momentum equations. Use a smaller parameter in a large wave case to avoid this issue. 



