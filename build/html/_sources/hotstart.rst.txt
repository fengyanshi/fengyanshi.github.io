.. _section-hotstart:

Hot Start
*********

**HOT START OR INITIAL CONDITION**
 
* :code:`INI_UVZ`: logical parameter for initial condition, default is FALSE
 
* :code:`ETA_FILE`: name of file for initial :math:`\eta`, e.g., :code:`ETA_FILE = /Users/results/eta_00100`, data could be the last results from a previous run. Data format is the same as the output/depth files in ASCII file format.

* :code:`U_FILE`:  name of file for initial u, e.g., :code:`U_FILE = /Users/results/u_00100`. If no :code:`U_FILE` specified, use zeros. 

* :code:`V_FILE`:  name of file for initial v, e.g., :code:`V_FILE = /Users/results/v_00100`. If no :code:`V_FILE` specified, use zeros. 

* :code:`MASK_FILE`:  name of file for initial MASK, e.g., :code:`MASK_FILE = /Users/results/mask_00100`. A :code:`MASK_FILE` could be from a model output and the format is REAL numbers. If there is no :code:`MASK_FILE`, MASK values will be re-specified according to ETA and DEPTH.  


