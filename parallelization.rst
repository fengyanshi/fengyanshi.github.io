.. _section-parallel:

Parallelization
***************

**SPECIFICATION OF MULTI-PROCESSORS**

*  :code:`PX`:  number of processors to use in X
*  :code:`PY`:  number of processors to use in Y  

 .. note:: :code:`PX` and :code:`PY` must be consistent with the number of processors defined in :code:`mpirun` command, e.g., :code:`mpirun -np n` (where n = px * py). For versions 3.0 or lower, :code:`PX (PY)` should be a common factor of :code:`Mglob(Nglob)`. 

