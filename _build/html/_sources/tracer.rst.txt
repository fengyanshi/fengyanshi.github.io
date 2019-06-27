.. _section-tracer-formula:

Lagrangian Tracking Module 
****************************

Lagrangian tracking module is implemented using the individual-based particle-tracking method which treats  particles as if they exactly follow the fluid dynamics. In the current version, the Lagrangian evolution of the position of a particle is expressed as

.. math:: d {\bf x}/dt = {\bf u}_\alpha ({\bf x}) 

where :math:`{\bf x}` is the particle's position and :math:`{\bf u}_\alpha` is the fluid velocity at the reference level. The accuracy of the calculated particle trajectory depends on both the magnitude of the time-step and the order-accuracy of the velocity field. The time step used to update the particle position is the same as the time step used in solving the Boussinesq equation, which is assumed to be small. The first order discrete form of the above equation is used in the model. 
  
The particle position :math:`(x,y)` is specified at the central point of a cell, the same as other model variables such as :math: `u,v,\eta` etc. The orgin (0,0) is at the central point of the bottom-left (south-west) corner cell. A linear interpolation is used to get the instantaneous velocity at the particle position. In particular, an interpolation value is obtained from the values at three nearest points. The areas of four triangles constructed by the four points (3 nearest points and the particle point itself) can be calculated using 

.. math:: S_{\alpha \beta \gamma} = \left | \begin{array}{ccc} x_\alpha & y_\alpha & 1 \\  x_\beta & y_\beta & 1 \\ x_\gamma & y_\gamma & 1 \end{array} \right|

where :math:`S_{\alpha \beta \gamma}` represents the area of the triangle :math:`(\alpha \beta \gamma)`, counter-clockwise. The interpolation value is evaluated using

.. math:: F_A = (F_1 S_{23A} + F_2S_{31A} + F_3S_{12A})/S_{123}

where :math: `F_1, F_2, F_3` and :math: `F_A` represent values at points (1,2,3) and the partical point A, respectively. 

To set up particle tracking in the model, see :ref:`section-tracer-setup`

* Animation: Tsunami waves  debris tracking (path) 

.. raw:: html

 <iframe width="560" height="315" src="https://www.youtube.com/embed/rJXbP-IZaXU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
