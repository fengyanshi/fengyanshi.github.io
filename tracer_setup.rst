.. _section-tracer-setup:

Lagrangian Tracer Setup
***********************

The formulas used for Lagrangian tracking can be found in :ref:`section-tracer-formula`.

To set up the Lagrangian tracer feature:

 1) Compile the code using the :code:`make` command with :code:`-DTRACKING` active in "Makefile". (Review compiling instructions :ref:`here <section-download>`)
 2) In "input.txt", specify:
    
    .. code-block:: rest

         TRACER_FILE = tracers.txt 
        
    'tracers.txt' (you can use other names) is the file that contains the initial positions of particles.

 3) In "tracers.txt", specify: 

    .. code-block:: rest

          give a header  ! the program does not read
          196            ! number of tracers 
          1.0            ! plot interval for output
          3.5500000e+02   4.7500000e+02   0.0000000e+00   0.0000000e+00
          3.5700000e+02   4.7500000e+02   0.0000000e+00   0.0000000e+00
          3.5900000e+02   4.7500000e+02   0.0000000e+00   0.0000000e+00
          3.6100000e+02   4.7500000e+02   0.0000000e+00   0.0000000e+00
          ...

   The first line: give a header

   The second line: give the number of tracers

   The third line: give time interval for output

   The following lines: specify x, y, 0, 0, where (x,y) are the inital positions of tracers (in meters). 

 .. NOTE:: The particle position :math:`(x,y)` is specified at the central point of a cell, the same as other model variables such as :math:`u,v,\eta` etc. The orgin (0,0) is at the central point of the bottom-left (south-west) corner cell.

