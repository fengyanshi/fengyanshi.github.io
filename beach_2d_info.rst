Basics for model setup
######################

**Computational domain**

.. figure:: images/simple_cases/layout_2dbeach.jpg
    :width: 500px
    :align: center
    :height: 220px
    :alt: alternate text
    :figclass: align-center

**Basic info**

* Dimensions: 500 x 250 (x and y directions):
   .. code-block:: rest

        Mglob = 250 ! y-dir
        Nglob = 500 ! x-dir

        DX = 2.0
        DY = 2.0


* Wavemaker: located at x = 150.0 m:
   .. code-block:: rest

        Xc_WK = 150.0

  with Sponge layer: x = 0.0 -- 100.0 m on the west boundary:
     .. code-block:: rest

          Sponge_west_width = 100.0

  Several "input.txt" files are located in the folder :code:`/simple_cases/beach_2d/input_files/` listing wavemaker parameters for different cases. When running one of the cases listed below, copy the wavemaker parameters from the respective file to the primary *input.txt* file:

  * Case 1: monochromatic wave with normal incidence -- "input_reg.txt"

  * Case 2: monochromatic wave with 30-degree incidence -- "input_reg_30deg.txt"

  * Case 3: irregular waves with peak direction = 0.0 -- "input_irr.txt"

  * Case 4: irregular waves with peak direction = 30.0 -- "input_irr_30deg.txt"

* Postprocessing

  Example MATLAB postprocessing scripts are located in :code:`/simple_cases/beach_2d/postprocessing/`
