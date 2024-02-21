Hydrodynamic Correction for High Concentration Sediment
*********************************************************

Following `Cao et al. (2004) <https://ascelibrary-org.udel.idm.oclc.org/doi/10.1061/%28ASCE%290733-9429%282004%29130%3A7%28689%29>`_, hydrodynamic corrections were made for high concentration sediment. Three extra terms were added into mass and momentum conservation equations, respectively. According to Cao et al.'s (5) and (6), which were based on SWE in x-direction:

.. math:: \frac{\partial H}{\partial t} + \frac{\partial Hu}{\partial x} = \frac{P-D}{1-n}

.. math:: \frac{\partial Hu}{\partial t} + \frac{\partial }{\partial x} \left(Hu^2+\frac{1}{2}g H^2\right) = gH \left(-\frac{\partial z}{\partial x} - S_f \right) - \frac{(\rho_s-\rho_w)gH^2}{2\rho}\frac{\partial c}{\partial x} - \frac{(\rho_0-\rho)(P-D)u}{\rho(1-n)}

where :math:`S_f` is the bottom friction term.  Notice that the definition of :math:`h` defined in Cao et al. is the total water level :math:`H=(h+\eta)`, we rewrote the momentum equation above using :math:`(h+\eta)` or :math:`H` instead of :math:`h`, which is the still water depth defined here. The 1D SWEs are consistent with the SWE form of FUNWAVE-TVD equations except the extra terms in the mass and momentum equations. The definitions of density of water-sediment mixture and saturated bed are

  Density of water-sediment mixture: :math:`\rho = \rho_w(1-c) + \rho_s c`

  Density of saturated bed: :math:`\rho_0 = \rho_w n + \rho_s (1-n)`

The FUNWAVE-TVD equations become

.. math:: \eta_t + \nabla \cdot {\bf M} = M_{ext}

.. math:: {\bf M}_t + \nabla \cdot \left( \frac{{\bf MM}}{H} \right) + \nabla \left(\frac{1}{2}g(\eta^2 + 2h\eta) \right) = H {\bf V}_{dis} + g\eta \nabla h + {\bf DC}_{ext} + {\bf EXG}_{ext}  

where :math:`{\bf V}_{dis}` represents the nonlinear dispersive terms; :math:`M_{ext}` is the additional term due to the total mass balance; :math:`{\bf DC}_{ext}` is the extra term representing the effect of spatial variation of sediment concentration; :math:`{\bf EXG}_{ext}` is the extra term caused by the momentum transfer due to sediment exchange between the water column and erodible bed. 

We define :math:`s=\rho_s/\rho_w` which is consistent with the previous definition in FUNWAVE-TVD (Tehranirad et al., 2020), and note that :math:`s` here is different from Cao et al. who defined it as :math:`s =\rho_s/\rho_w -1`. The extra term in the mass conservation equation is

.. math:: M_{ext} =  \frac{P-D}{1-n}

The extra terms in the momentum equation are

.. math:: {\bf DC}_{ext} = - \frac{(s-1)gH^2}{[1+c(s-1)]} \nabla c

and 

.. math:: {\bf EXG}_{ext} = - \frac{(s-1)(1-n-c)}{[1+c(s-1)](1-n)} (P-D) {\bf \bar{u}}

where :math:`{\bf \bar{u}}` represents the depth-averaged velocity and can be estimated by :math:`{\bf u}_\alpha` for simplicity. Notice that :math:`1-n-c \ge 0` in equations above.

To simulate the effects of the extra terms, we provide three logical parameters

.. code-block:: rest

     SedimentMassSource = T ! or F, if T extra term in mass equation calculated
     SedimentMomentDC = T ! or F, if T concentraton gradient term calculated
     SedimentMomentEXG = T ! or F, if T momentum exchange term calculated

The default values for all three parameters are F. 


    







