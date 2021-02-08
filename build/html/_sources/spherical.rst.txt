.. _section-spherical:

Spherical Coordinates
*********************

************************
Input for Spherical mode
************************

All input parameters, except the following grid information, are the same as for the Cartesian code.

* :code:`Lon_West`: longitude (degrees) of west boundary.
* :code:`Lat_South`: latitude (degrees) of south boundary.
* :code:`Dphi`: :math:`d\phi` (degrees)
* :code:`Dtheta`: :math:`d\theta` (degrees) 
* :code:`ArrTimeMinH`: threshold to detect tsunami wave (default is 0.0001m), for output files of tsunami arrival time with :code:`OUT_Time = T`.   

In addition, it is not necessary to specify :code:`Gamma2` (for nonlinear dispersive terms) in the spherical code.  

Another feature of the spherical code is that a computational grid can be a stretched grid. For a stretched grid, a user should set :code:`StretchGrid = T` and provide grid files for :code:`DX` and :code:`DY` and a file for Coriolis parameters at each grid point. For example,

 :code:`DX_FILE = dx_str.txt`

 :code:`DY_FILE = dy_str.txt`

 :code:`CORIOLIS_FILE = cori_str.txt`

However, use of a stretched grid is not recommended in terms of decrease in numerical accuracy for  higher order numerical schemes. 
