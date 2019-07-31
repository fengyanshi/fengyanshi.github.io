.. _sponge_definition:

Sponge Layer
************

For theory of sponge layers, see :ref:`section_sponge_layer`

**SPECIFICATION OF SPONGE LAYER**
 
* :code:`DIRECT_SPONGE`: logical parameter for L-D type sponge, T - sponge layer, F - no sponge layer.

  * :code:`R_sponge`: decay rate in L-D type sponge layer. Its values are between 0.85 :math:`\sim` 0.95. Default: 0.85.

  * :code:`A_sponge`: maximum damping magnitude in L-D type sponge. The value is :math:`\sim` 5.0. Default: 5.0
 
* :code:`FRICTION_SPONGE`: logical parameter for friction type sponge, T - sponge layer, F - no sponge layer.

  * :code:`CDsponge`: The maximum Cd for friction type sponge. Default: 10.0

* :code:`DIFFUSION_SPONGE`: logical parameter for diffusion type sponge, T - sponge layer, F - no sponge layer.
 
  * :code:`Csp`: The maximum diffusion coefficient for diffusion type sponge. Default: 1.0
  
* :code:`Sponge_west_width`: width (m) of sponge layer at west boundary.

* :code:`Sponge_east_width`:   width (m) of sponge layer at east boundary.

* :code:`Sponge_south_width`: width (m) of sponge layer at south boundary.

* :code:`Sponge_north_width`: width (m) of sponge layer at north boundary

   


