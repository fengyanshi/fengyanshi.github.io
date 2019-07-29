<<<<<<< HEAD
.. _section-rip-2d-compile:

Compile the code for 2D beach case
##################################

**Makefile**

See an example of a complete "Makefile" :ref:`here <subsection-compile>`. 

For this example, you will need to update the :code:`EXEC` variable, and make sure the appropriate :code:`FLAGS` are active in the "Makefile":

.. code-block:: rest

     #---------BEGIN MAKEFILE-------------
        ...
        ...
        EXEC    = funwave_surface_wave          # for example

     #------------------------------------
     #  PRECISION ...
     #
     #------------------------------------
     ## FLAGS
     ## Flag numbers are arbitrary, but necessary

        FLAG_1 = -DDOUBLE_PRECISION
        FLAG_4 = -DCARTESIAN 

     #  if parallel add
        FLAG_2 = -DPARALLEL
     
     #  if intel compiler add
        FLAG_6 = -DINTEL

        ...

     #------------------------------------
     # mpi defs
     #------------------------------------
     ## COMPILER INFO

        ...

        FC       = mpif90       # for example

=======
.. _section-rip-compile:

Compile the code for 2D rip current case
########################################

**Makefile**

See an example of a complete "Makefile" :ref:`here <subsection-compile>`.

For this example, you will need to update the :code:`EXEC` variable, and make sure the appropriate :code:`FLAGS` are active in the "Makefile":

.. code-block:: rest

    #---------BEGIN MAKEFILE-------------
        ...
        ...
        EXEC    = funwave_surface_wave          # for example

     #------------------------------------
     #  PRECISION ...
     #
     #------------------------------------
     ## FLAGS
     ## Flag numbers are arbitrary, but necessary

        FLAG_1 = -DDOUBLE_PRECISION
        FLAG_4 = -DCARTESIAN 

     #  if parallel add
        FLAG_2 = -DPARALLEL
     
     #  if intel compiler add
        FLAG_6 = -DINTEL

        ...

     #------------------------------------
     # mpi defs
     #------------------------------------
     ## COMPILER INFO

        ...

        FC       = mpif90       # for example

>>>>>>> 3f596b802f4114f304438e686793b43dcca22daf
The compiled executable file that's generated is "funwave_surface_wave.exe".
