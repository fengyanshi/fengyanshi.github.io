Spherical Coordinates
***********************

*****************************
Input for Spherical mode
*****************************

All input parameters, except the following grid information, are the same as for the Cartesian code.

 * Lon\_West: longitude (degrees) of west boundary.
 * Lat\_South: latitude (degrees) of south boundary.
 * Dphi: :math:`d\phi` (degrees)
 * Dtheta: :math:`d\theta` (degrees) 

 In addition, it is not necessary to specify  Gamma2 (for nonlinear dispersive terms) in the spherical code.  

 Another feature of the spherical code is that a computational grid can be a stretched grid. For a stretched grid, a user should set  StretchGrid = T and provide grid files for DX and DY and a file for Coriolis parameters at each grid point.  For example,

 DX\_FILE = dx\_str.txt

 DY\_FILE = dy\_str.txt

 CORIOLIS\_FILE = cori\_str.txt

However, use of a stretched grid is not recommended in terms of decrease in numerical accuracy for  higher order numerical schemes. 
