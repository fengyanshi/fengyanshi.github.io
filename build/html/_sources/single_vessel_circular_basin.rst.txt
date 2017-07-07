Single Vessel in a Circular Basin 
###################################

.. figure:: images/simple_cases/shipwake_150.jpg
    :width: 300px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

* Set up dimensions

  Mglob = 500

  Nglob = 500

* Depth file

  DEPTH_FILE = depth.txt

* Add a vessel

  VESSEL_FOLDER = ./

  NumVessel = 1

  In vessel_00001, specify:
  
  Title: Vessel # 1

  Blue_Star_I

  Length(m), Width(m), Alpha(m), Beta(m), P(unit)

  20.0  10.0, 0.5, 0.5, 1.0

  0.0000000e+00,   5.6000000e+02,   5.0000000e+02

  1.0000000e+00,   5.6374897e+02,   5.0255132e+02

  ...  

* Output
 
  ETA = T



