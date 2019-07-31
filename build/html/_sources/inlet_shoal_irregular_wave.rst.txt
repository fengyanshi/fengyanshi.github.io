.. _section-inlet-irr:

Irregular wave 
################

.. figure:: images/simple_cases/eta_inlet_shoal_irr.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center


Update the wavemaker type and add the appropriate parameters in the wavemaker section of "input.txt" for this example. The domain setup was defined in :ref:`section-inlet-basics`, and the baseline case can be reviewed at :ref:`section-inlet-reg`.

 Set descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = inlet_irr

 Add an irregular wavemaker with the following conditions:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = WK_IRR
         DEP_WK = 10.0
         Xc_WK = 250.0
         Yc_WK = 0.0
         Ywidth_WK = 20000.0
         FreqPeak = 0.0893
         FreqMin = 0.03
         FreqMax = 0.3
         Hmo = 1.00
         GammaTMA = 3.3
         ThetaPeak = 0.0
         Sigma_Theta = 10.0

 Default option for energy splitting is EqualEnergy (refer to :ref:`info_equal_energy` for more information). Review wavemaker parameter definitions :ref:`here <definition_wavemaker>`.


