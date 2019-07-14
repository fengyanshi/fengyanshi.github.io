Single Vessel in a Circular Basin 
###################################

* computational domain

.. figure:: images/simple_cases/depth_vessel.jpg
    :width: 400px
    :align: center
    :height: 350px
    :alt: alternate text
    :figclass: align-center

* input.txt
  is in the folder /simple_cases/vessel_island_beach/

* Bathymetry file

  in the folder /simple_cases/simple_cases/vessel_island_beach/depth.txt

**In input.txt:**

|  **Parallel info (if use parallel)**
|   PX = 2
|   PY = 2

|  **Depth**
|   DEPTH_TYPE = DATA
|   DEPTH_FILE = depth.txt

  (refer to :ref:`definition_grid`)

|  **Set up dimensions**
|   Mglob = 500
|   Nglob = 500

|  **Dimensions**
|   DX = 2.0
|   DY = 2.0

|  **Time**
|   TOTAL_TIME = 300.0
|   PLOT_INTV = 1.0
|   SCREEN_INTV = 1.0

|  **Add a vessel**
|   VESSEL_FOLDER = ./
|   NumVessel = 1
|
|   In vessel_00001, specify:  
|   Title: Vessel # 1
|   Pressure, 1
|   Length(m), Width(m), Alpha1(m), Alpha2(m), Beta(m), P(unit)
|   20.0  10.0, 0.5, 0.5, 0.5, 1.0
|   0.0000000e+00,   5.6000000e+02,   5.0000000e+02
|   1.0000000e+00,   5.6374897e+02,   5.0255132e+02
|   ...  

  (refer to :ref:`section-shipwakes-setup`)

|  **Output**
|   RESULT_FOLDER = output/
|   ETA = T

|  **postprocessing**
|   matlab examples of postprocessing are located in /simple_cases/vessel_island_beach/

.. figure:: images/simple_cases/shipwake_150.jpg
    :width: 300px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center




