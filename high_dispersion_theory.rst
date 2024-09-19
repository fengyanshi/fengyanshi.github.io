THEORY OF FULLY DISPERSIVE MODEL
=====================================

Equations
*************
The 3D equations, describing fully dispersive non-hydrodynamic motion, can be written in a generalized conservative form as
 
.. math:: \frac{\partial {\bf \Psi}}{\partial t} + \nabla \cdot {\bf \Theta}({\bf \Psi}) = {\bf S}
where :math:`\nabla = \left(\frac{\partial }{\partial x}, \frac{\partial }{\partial y}, \frac{\partial }{\partial \sigma} \right)`. :math:`{\bf \Psi}` and :math:`{\bf \Theta}({\bf \Psi})` are  the vector of conserved variables and  the flux vector function respectively.
  .. math:: 

     {\bf \Psi} = \begin{bmatrix}

                           D  \\ 

                           Du  \\ 

                           Dv  \\

                           D\omega 

                   \end{bmatrix} 


  .. math::

     {\bf \Theta} =  \begin{bmatrix}

                    Du {\bf i} + Dv {\bf j} + \omega {\bf k} \\
                    (Duu+(\frac{1}{2}g \eta^2+gh\eta)) {\bf i} + Duv{\bf j}  + u\omega {\bf k} \\
                    Duv {\bf i} + (Dvv +(\frac{1}{2}g \eta^2+gh\eta) ){\bf j}  + v\omega {\bf k}  \\
                    Duw  {\bf i} + Dvw{\bf j}  + w \omega {\bf k}

                  \end{bmatrix}

where  :math:`D = h + \eta`, :math:`h` is water depth and :math:`\eta` is surface elevation,  (:math:`u,v,w`) represent velocity components in the Cartesian coordinate system  (:math:`x^*, y^*, z^*`) and :math:`\omega` is the vertical velocity defined in the :math:`\sigma` coordinate image domain. The reason for using the :math:`\sigma` coordinate system will be described in the Flow Surface Technique in the next section.
 
The source term on the right hand side includes three source components:

  .. math::
      {\bf S} = {\bf S}_h +{\bf S}_p+{\bf S}_\tau

where :math:`{\bf S}_h, {\bf S}_p`, and  :math:`{\bf S}_\tau` represent the bottom slope term, dynamic pressure gradient and turbulent mixing respectively. Associated with the splitting method in the study, the dynamic pressure term is expressed below.

  .. math::

       {\bf S}_h = \begin{bmatrix}

           g\eta\frac{\partial{h}}{\partial{x}} \\ 
                        g\eta\frac{\partial{h}}{\partial{y}} \\
                          0

                   \end{bmatrix} 


  .. math::

      {\bf S}_p =  \begin{bmatrix}

                      -\frac{D}{\rho}(\frac{\partial p}{\partial x}+\frac{\partial p}{\partial \sigma} \frac{\partial \sigma}{\partial x^*})  \\  
                      -\frac{D}{\rho}(\frac{\partial p}{\partial y}+\frac{\partial p}{\partial \sigma} \frac{\partial \sigma}{\partial y^*})  \\
                       -\frac{1}{\rho}\frac{\partial p}{\partial \sigma}  

                    \end{bmatrix}

  .. math::

       {\bf S}_{\tau} =  \begin{bmatrix}

                            DS_{\tau x} \\ 
                            DS_{\tau y} \\ 
                            DS_{\tau z} 

                         \end{bmatrix}


where :math:`p` represents the dynamic pressure.

Flow Surface Technique
**************************

Different from a traditional CFD model where the water surface is governed by a separate surface equation such as in the Volume of Fluid method (VOF) or the Marker and Cell (MAC) method, a so-called``surface flow" technique was used by transforming the Navier-Stokes equations in Cartesian coordinates into the $\sigma$ coordinates. The governing equation for free surface can be written as

.. math::

      \frac{\partial D}{\partial t}+\frac{\partial }{\partial x} (D \int_0^1 u d \sigma)+\frac{\partial }{\partial y} (D \int_0^1 v d \sigma)=0
 
The use of :math:`\sigma` coordinate is consistent with FUNWAVE-TVD, in which the reference elevation :math:`z_\alpha` is in the :math:`\sigma` coordinate as in Kennedy et al. (2001).  

