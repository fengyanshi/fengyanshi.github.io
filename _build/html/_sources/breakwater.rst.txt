Breakwater and Obstacle
**************************

**SPECIFICATION OF OBSTACLES or BREAKWATER**

 *  OBSTACLE\_FILE: name of obstacle file. 1 - water point, 0 - permanent dry point. Data dimension is (Mglob . Nglob). Data format is the same as the depth data. Full reflection condition is used at OBSTACLE points. 

 * BREAKWATER\_FILE: name of breakwater file. The file contains width (m) at the breakwater points with the same format as the depth file. Zero for non-breakwater poionts. The width is not the breakwater width but the width of a sponge layer placed at the breakwater points. For a field case, use 10m-30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Default: no breakwater. Breakwater absorption is made by using large bottom friction locally (large Cd) around breakwater points. The maximum Cd is specified by BreakWaterAborbCoef. 

 * BreakWaterAborbCoef: This parameter provides the maximum Cd in the bottom friction formulation at breakwater locations. The default value is 10.0. Note: for large waves (e.g. significant wave height > 10m) in the field case, a large parameter can cause imbalance of the momentum equations. Use a smaller parameter in a large wave case to avoid this issue. 



