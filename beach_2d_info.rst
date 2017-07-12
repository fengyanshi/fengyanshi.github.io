Basics for model setup
##########################

* computational domain

.. figure:: images/simple_cases/layout_2dbeach.jpg
    :width: 500px
    :align: center
    :height: 220px
    :alt: alternate text
    :figclass: align-center

Basic info

 Dimensions 250 X 500

 DX = DY = 2.0 m

 Wavemaker located at x = 150.0 m

 Sponge layer: x = 0.0 -- 100.0 m

* input.txt
  several input files in the folder /simple_cases/beach_2d/input_files/ for different cases. When run a case, copy one of them to "input.txt"

  input_reg.txt -- monochromatic wave, normal incidence

  input_reg_30deg.txt -- monochromatic wave, 30-degree incidence

  input_irr.txt -- irregular waves, peak direction - 0.0 

  input_irr_30deg.txt -- irregular waves, peak direction - 30.0 

* postprocessing

  matlab examples of postprocessing are located in /simple_cases/beach_2d/postprocessing/
