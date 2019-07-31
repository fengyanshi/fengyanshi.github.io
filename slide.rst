.. _section-landslide:

Landslide
*********

Add the following to "input.txt":

* :code:`SlideModel`: logical parameter for landslide model. T or F.

* :code:`SLIDE_FILE`: name of file contains landslide parameters

  A sample:

  .. code-block:: rest
   
        slide_file      ! not read by model

        Grilli          ! slide name

        Length(m), Width(m), Alpha(m), Beta(m), P(unit)   ! not read by model

        0.395  0.68 1.0 1.0 0.082

        Time, X(m), Y(m)  ! relative to the orgin of the coordinates (not read by model)

        0.0000    2.0340    1.8500

        0.0100    2.0341    1.8500

        0.0200    2.0342    1.8500

        0.0300    2.0345    1.8500



