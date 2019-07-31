.. _section-shipwakes-setup:

Shipwakes Setup
***************

1) Specify a folder which contains a number of vessel files, :code:`vessel_00001, vessel_00002, ...`
   
   :code:`VESSEL_FOLDER = ./`

2) Specify the number of vessels (e.g., 5)

   :code:`NumVessel = 5`

3) In :code:`vessel_00001`, for example, provide vessel name, vessel type, vessel length, width, shape parameters, draft and time series of vessel path:  

   .. code-block:: rest

        Title: Vessel # 1  - (name)
        PRESSURE, 1  (pressure type, type I)
        Length(m), Width(m), Alpha1, Alpha2, Beta, P(unit) (comment, vessel parameters)
        20.0  10.0, 0.5, 0.5, 1.0    (vessel parameters)
        0.0000000e+00,   5.6000000e+02,   5.0000000e+02  (time, x, y)
        1.0000000e+00,   5.6374897e+02,   5.0255132e+02  (...)
        ...  

   In the time series, the first column is time in seconds, the second and the third are x and y in meters, respectively. 


**The following is an example which includes 5 vessels of different types**

This example can be found in :code:`/simple_cases/vessel_types_compare/`.

Figure: Vessel types (from bottom to top): 1) Pressure Type I, 2) Pressure Type I with large :math:`\alpha`, 3) Pressure Type II, 4) Slender Type I, 5) Slender Type II. 

.. figure:: images/simple_cases/5_vessels.jpg
    :width: 300px
    :align: center
    :height: 500px
    :alt: alternate text
    :figclass: align-center

*vessel_00001: Pressure Type I*

.. code-block:: rest

         Title: Vessel # 1
         PRESSURE, 1
         Length(m), Width(m), Alpha1, Alpha2 Beta, P(m)
         20.0  8.0, 0.0, 0.0, 0.5, 3.0
         Time, X(m), Y(m)  (relative to the origin of the coordinates)
         0.0    50.0  60.0
         100.0 1050.0 60.0

*vessel_00002: Pressure Type I with large* :math:`\alpha`

.. code-block:: rest

         Title: Vessel # 2
         PRESSURE, 1
         Length(m), Width(m), Alpha1, Alpha2, Beta, P(m)
         20.0  8.0, 0.9, 0.9, 0.5, 3.0
         Time, X(m), Y(m)  (relative to the origin of the coordinates)
         0.0    50.0  120.0
         100.0 1050.0 120.0

*vessel_00003: Pressure Type II*

.. code-block:: rest

         Title: Vessel # 3
         PRESSURE, 2
         Length(m), Width(m), a, b, c, P(m)
         10.0  5.0, 16.0, 2.0, 16.0, 2.0
         Time, X(m), Y(m)  (relative to the origin of the coordinates)
         0.0   50.0   180.0
         100.0 1050.0 180.0

*vessel_00004: Slender Type I*

.. code-block:: rest

         Title: Vessel # 4
         SLENDER, 1
         Length(m), Width(m), Alpha1, Alpha2, Beta, F(unit)
         10.0  5.0, 0.0, 0.0, 0.9, 12.0
         Time, X(m), Y(m)  (relative to the origin of the coordinates)
         0.0   50.0   240.0
         100.0 1050.0 240.0

*vessel_00005: Slender Type II*

.. code-block:: rest

         Title: Vessel # 5
         SLENDER, 2
         Length(m), Width(m), Alpha1, Alpha2, Beta, F(unit)
         10.0  5.0, 0.8, 0.8, 0.9, 40.0
         Time, X(m), Y(m)  (relative to the origin of the coordinates)
         0.0   50.0   300.0
         100.0 1050.0 300.0








