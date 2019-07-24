.. _definition_meteo:

Wind and Pressure Field
************************

**SPECIFICATION OF WIND EFFECT**

 .. NOTE:: Use :code:`FLAG_xx = -DMETEO` in "Makefile" when compiling. Review compiling instructions :ref:`here <section-download>`.


* :code:`WindForce`: logical parameter representing if wind effect is taken into account. T or F. If :code:`WindConstantField = T, WindForce = T` automatically.

* :code:`AirPressure`: logical parameter representing if pressure effect is taken into account. T or F. If :code:`MeteoGausian = T, AirPressure = T` automatically.

* :code:`WindWaveInteraction`: logical parameter representing if wave-wind interaction (Chen et al. 2003) based on the formula presented in the :ref:`METEO module <section_meteo_module>` page. The parameter :code:`WindCrestPercent` will be used.  
* :code:`Cdw`: wind stress coefficient for the quadratic formula if :code:`WindForce = T`. Default: 0.002.

* :code:`WindCrestPercent`: ratio of the forced wave crest height to the maximum surface elevation, if :code:`WindForce = T`. Default: 1.0 (100\%) (for storm surges). 

* :code:`WindConstantField`: logical parameter for constant wind field. T or F.
    
* :code:`CONSTANT_WIND_FILE`: file name for the constant wind field. The following is an example of data format:

  Wind data:

  .. code-block:: rest

        100  ! number of data

        0.0 ,    10.0 0.0   !  time(s), wu, wv (m/s)

        2000.0,   10.0,  0.0

        8000.0,  10.0,   0.0

        ... 

  For example, for constant wind field, "input.txt" will look like:

  .. code-block:: rest

        Cdw = 0.002

        WindConstantField = T

        WindWaveInteraction = T

        WindCrestPercent = 0.5

        CONSTANT_WIND_FILE = wind.txt 

* :code:`WindHollandModel`: logical parameter for Holland model. T or F. 

* :code:`STORM_FILE`: name of file contains paramters used for Holland hurricane model.

  A sample: 

  .. code-block:: rest

    STORM FILE ! (model does not read)

    Sandy      ! storm name

    time(s),     x(m), y(m),    pn(mb),   pc(mb),   A,    B  ! (model does not read)

    0.0,  800000.0, 400000.0,   1005.0, 950.0, 23.0, 1.50    ! time, x,y, pn, pc, A, B

    120000.0,  800000.0, 1500000.0,  1005.0, 950.0, 23.0, 1.50 

**SPECIFICATION OF METEOTSUNAMI**

Pressure Source (Gaussian distribution -- elipse)

 **Add to "input.txt"**

 .. code-block:: rest

        MeteoGaussian = T
        METEO_GAUSSIAN_FILE = meteo_data.txt    ! (for example)

 You will need specify your pressure source in the file: "meteo_data.txt" (for example):

 .. code-block:: rest

        Meteo data file
        NJ
        time, x, y, dP(mb), SigmaX, SigmaY, Angle(0 = +x direction)
        0.0       0.0 25000.0   5.0 10000.0 100000.0 0.0
        36000.0  720000.0 25000.0  5.0 10000.0 10000.0 0.0     

 **Output section of "input.txt"**

 .. code-block:: rest

        RESULT_FOLDER = output/   ! this parameter is located in the PRINT section of "input.txt"
        ETA = T
        Hmax = T
        Hmin = T
        OUT_METEO = T    ! (T will have output of pressure distribution)

