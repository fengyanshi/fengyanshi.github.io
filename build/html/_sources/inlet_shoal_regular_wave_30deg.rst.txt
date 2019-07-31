.. _section-inlet-reg30:

Regular wave 30 deg oblique incidence
#####################################

.. figure:: images/simple_cases/eta_inlet_shoal_reg_30deg.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Update the title and incident wave angle in "input.txt" for this example. The domain setup was defined in :ref:`section-inlet-basics`, and the baseline case can be reviewed at :ref:`section-inlet-reg`.

 Set descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = inlet_reg_30deg

 Set the incident wave angle to 30 deg:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = WK_REG
         DEP_WK = 10.0 
         Xc_WK = 250.0 
         Yc_WK = 0.0 
         Tperiod = 12.0 
         AMP_WK = 1.0 
         Theta_WK = 30.0     ! here

 (refer to :ref:`definition_wavemaker` for parameter definitions)


