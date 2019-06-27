Hot Start
************
**HOT START OR INITIAL CONDITION**
 
 *  INT\_UVZ : logical parameter for initial condition, default is FALSE
 
 
 *  ETA\_FILE: name of file for initial :math:`\eta`, e.g., ETA\_FILE= /Users/results/eta_00100, data could be the last results from a previous run. Data format is the same as the output/depth files.

 *  U\_FILE:  name of file for initial u, e.g.,U\_FILE= /Users/results/u_00100. If no U\_FILE specified, use zeros. 

 *  V\_FILE:  name of file for initial v, e.g., V\_FILE= /Users/results/v_00100. If no V\_FILE specified, use zeros. 

 *  MASK\_FILE:  name of file for initial MASK, e.g., MASK\_FILE= /Users/results/mask_00100. A MASK\_FILE could be from a model output and the format is REAL numbers. If there is no MASK\_FILE, MASK values will be re-specified according to ETA and DEPTH.  


