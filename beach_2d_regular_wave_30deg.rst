.. _section-beach-2d-reg:

Regular wave 30 deg oblique incidence
#####################################

.. figure:: images/simple_cases/wave_reg_30deg.jpg
    :width: 600px
    :align: center
    :height: 400px
    :alt: alternate text
    :figclass: align-center

The following sections will be modified in "input.txt" for this case. All other sections are defined in :ref:`section-beach-2d-basics` for this example.

  Set a descriptive title for your simulation:

  .. code-block:: rest

        !-----TITLE-----
         TITLE = 2D_beach_30deg
  
  Modify the initial wavemaker section on :ref:`section-beach-2d-basics` to generate monochromatic waves with incidence of 30.0:
  
  .. code-block:: rest
       
       WAVEMAKER = WK_REG
       DEP_WK = 8.0 
       Xc_WK = 150.0 
       Yc_WK = 0.0 
       Tperiod = 8.0 
       AMP_WK = 0.5 
       Theta_WK = 30.0    ! this line
       Delta_WK = 3.0

  (refer to :ref:`definition_wavemaker` for description of parameters)
 
