Meteotsunami: Gausian pressure and flat bottom  
################################################

* Model setup

.. figure:: images/simple_cases/meteo_layout.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Model configuration: Model dimensions: 100 km x 600 km. Water depth is 40 m in the whole domain. Pressure source is an elliptical shape Gaussian distribution described in the section of METEO-MODULE in
`INTRODUCTION <theory_formulation.html>`_. The moving speed of the source is specified as 20 m/s which is close to the critical speed to make Proudman Resonance. 

* input.txt
  is in the folder /simple_cases/meteo_tsunami/

**In input.txt:**

|  **Parallel Info (if use parallel)**  
|   PX = 4 
|   PY = 1

|  **Depth**
|   DEPTH_TYPE = FLAT

  DEPTH_FLAT = 40.0

|  **Dimensions**
|   Mglob = 600
|   Nglob = 100

|  **Grid sizes**
|   DX = 500.0
|   DY = 500.0

|  **Set up time**
|   TOTAL_TIME = 30000.0
|   PLOT_INTV = 360.0
|   PLOT_INTV_STATION = 50000.0
|   SCREEN_INTV = 360.0

|  **Add pressure source (Gausian distribution (elipse))**
|   MeteoGausian = T
|   METEO_GAUSIAN_FILE = meteo_data.txt
   
|   You need specify your pressure source in the file: meteo_data.txt in the current directory. 
|   Meteo data file
|   NJ
|   time, x, y, dP(mb), SigmaX, SigmaY, Angle(0 = +x direction)
|   0.0       0.0 25000.0   5.0 10000.0 100000.0 0.0
|   36000.0  720000.0 25000.0  5.0 10000.0 10000.0 0.0     

|  **Output**
|   RESULT_FOLDER = output/
|   ETA = T
|   Hmax = T
|   Hmin = T
|   OUT_METEO = T (T will have output of pressure distribution)

|  **post-processing**
|   plot_wave.m in /simple_cases/meteo_tsunami/
|   Model result

.. figure:: images/simple_cases/resonance.jpg
    :width: 300px
    :align: center
    :height: 600px
    :alt: alternate text
    :figclass: align-center

The figure shows Proudman Resonance produced by the moving pressure source. 




