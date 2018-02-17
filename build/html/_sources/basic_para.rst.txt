Basics
********

Most model parameters are specified in the file called input.txt, except some parameters extended from a specific module.

 .. note::   all parameter names are capital sensitive.

**TITLE**:    title of your case, only used for log file.

**SPECIFICATION OF MULTI-PROCESSORS**

 *  PX:  processor numbers in X
 *  PY :  processor numbers in Y  

 .. note:: PX and PY must be consistency with number of processors defined in mpirun command, e.g., mpirun -np n (where n = px . py). For versions 3.0 or lower, PX (PY) should be a common factor of Mglob(Nglob).  
