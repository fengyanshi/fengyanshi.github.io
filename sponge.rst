Sponge Layer
***************

**SPECIFICATION OF SPONGE LAYER**
 
 *  DIRECT\_SPONGE: logical parameter for L-D type sponge, T - sponge layer, F - no sponge layer.
 
 *  FRICTION\_SPONGE: logical parameter for friction type sponge, T - sponge layer, F - no sponge layer.
 
 *  DIFFUSION\_SPONGE: logical parameter for diffusion type sponge, T - sponge layer, F - no sponge layer.
 
   *  Csp: The maximum diffusion coefficient for diffusion type sponge. Default: 1.0
 
   *  CDsponge: The maximum Cd for friction type sponge. Default: 10.0
 
   *  Sponge\_west\_width: width (m) of sponge layer at west boundary.

   *  Sponge\_east\_width:   width (m) of sponge layer at east boundary.

   *  Sponge\_south\_width: width (m) of sponge layer at south boundary.

   *  Sponge\_north\_width width (m) of sponge layer at north boundary

   *  R\_sponge: decay rate in L-D type sponge layer. Its values are between 0.85 :math:`\sim` 0.95. Default: 0.85.

   *  A\_sponge: maximum damping magnitude in L-D type sponge. The value is :math:`\sim` 5.0. Default: 5.0



