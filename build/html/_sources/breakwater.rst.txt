Breakwater and Obstacle
**************************

**SPECIFICATION OF OBSTACLES or BREAKWATER**

 *  OBSTACLE\_FILE: name of obstacle file. 1 - water point, 0 - permanent dry point. Data dimension is (Mglob . Nglob). Data format is the same as the depth data. Full reflection condition is used at OBSTACLE points. 

 * BREAKWATER\_FILE: name of breakwater file. The file contains width (m) at the breakwater points with the same format as the depth file. Zero for non-breakwater poionts. The width is not the breakwater width but the width of a sponge layer placed at the breakwater points. For a field case, use 10m-30m for weak absorption and >30m for strong absorption. Calibration may be needed case by case. Default: no breakwater.



