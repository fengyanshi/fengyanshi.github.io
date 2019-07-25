.. _section-1d-jonswap:

JONSWAP spectral waves 
######################

.. figure:: images/simple_cases/eta_1d_irr.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

The following section will be modified in "input.txt" for this case. All other sections are defined in :ref:`section-1d-basics` for this example.

 Add an irregular wavemaker in a water depth of 10 m located 250.0 m from the left boundary that produces a JONSWAP spectrum with minimum, maximum, and peak frequencies of 0.03, 0.3, and 0.0667 Hz, respectively, and significant wave height of 1.0 m:

 .. code-block:: rest
 
        !-----WAVEMAKER -----
         WAVEMAKER = JON_1D
         DEP_WK = 10.0 
         Xc_WK = 250.0 
         Yc_WK = 0.0 
         FreqPeak = 0.0667
         FreqMin = 0.03 
         FreqMax = 0.3 
         Hmo = 1.0

 Default option for energy splitting: EqualEnergy (refer to :ref:`info_equal_energy` for more information).
 
 Refer to :ref:`definition_wavemaker` for parameter definitions, and :ref:`example_breaking` for sample wave breaking scheme.

