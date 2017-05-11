Basics for model setup
##########################

* computational domain

.. figure:: images/simple_cases/tohoku_dem.jpg
    :width: 500px
    :align: center
    :height: 400px
    :alt: alternate text
    :figclass: align-center

Basic info

 Computational domain covers a region of the Pacific Ocean from 60°S to 60°N in the south-north direction, and from 132°E to 68°W in the west-east direction. The example is a 30min x 30min resolution case. The 2-min resolution result can be found in Kirby et al. (2013). 

 Dimensions 320 X 240

 DX = DY = 0.5 deg

 Tsunami source: the tsunami source is constructed in Grilli et al. (2012), which is based on the 3D FEM model of Masterlark (2003), denoted UA source. The non-hydrostatic model NHWAVE (Ma et al., 2012) is used to simulate the first 5 min of tsunami generation, as in Grilli et al. (2012), using a smaller and finer local 1 km resolution Cartesian grid, based on the UA source. The NHWAVE results of u, v eta are used as the initial conditions for FUNWAVE-TVD. 

* input.txt

  located in /simple_cases/tohoku/work/
  

* bathymetry
  
  located in /simple_cases/external_files/depth_30min.txt
  
* postprocessing

  matlab examples of postprocessing are located in /simple_cases/tohoku/postprocessing/

