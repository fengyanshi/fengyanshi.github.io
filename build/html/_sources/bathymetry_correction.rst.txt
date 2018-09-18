Bathymetry Correction
***********************

Large bathymetric slopes may induce computational errors in Boussinesq models. They can even  cause numerical instabilities for cases with a bathymetry containing a large amount of big slope points (slope>1.0). In that case, you should smoothen the bathymetry or use the following option in input.txt

 BATHY\_CORRECTION = T

 SmoothBelowDepth = --1.0 (for example)

 SlopeCap = 1.0  (for example)

SmoothBelowDepth = --1.0 means that the smoothening process will perform from --1.0 m (1.0 m above the still water level) to the sea bed (figure below). 

SlopeCape = 1.0 means that the smoothening process will perform around the points where slope > 1.0. 

.. figure:: images/smoothen.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center
