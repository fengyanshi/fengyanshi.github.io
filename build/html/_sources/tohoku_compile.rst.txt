.. _section-tohoku-compile:

Compile the code for spherical case
###################################

**Makefile**

See an example of a complete "Makefile" :ref:`here <subsection-compile>`.

For this example, you will need to update the :code:`EXEC` variable, and make sure the appriopriate :code:`FLAGS` are active in the "Makefile". To activate spherical coordinates, simply comment out the :code:`-DCARTESIAN` FLAG:

.. code-block:: rest

   #---------BEGIN MAKEFILE-----------
        ...
        ...
        EXEC   = funwave_spherical      # for example

   #-----------------------------------
   #    PRECISION ...
   #
   #-----------------------------------
   ## FLAGS
   ## Flag numbers are arbitrary, but necessary 

        FLAG_1 = -DDOUBLE_PRECISION
   #     FLAG_# = -DCARTESIAN

   #  if parallel add
        FLAG_2 = -DPARALLEL
   #  if intel compiler add
        FLAG_6 = -DINTEL
   #  if Z_alpha 
        FLAG_9 = -DZALPHA
        
        ...

   #----------------------------------
   # mpi defs
   #----------------------------------
   ## COMPILER INFO

        ...

        FC = mpif90     # for example

The compiled executable file is "funwave_spherical.exe".

