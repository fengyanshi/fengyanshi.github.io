Wave Breaking
***************

There are two breaking algorithms implemented in the model. One takes the advantage of the shock--capturing scheme in TVD. 
It  follows the approach of Tonelli and Petti (2009),  who successfully used the ability of  NSWE  with a TVD scheme to model moving hydraulic jumps. Thus, the fully nonlinear Boussinesq equations are switched  to NSWE at cells where the Froude number exceeds  a certain threshold. Following Tonelli and Petti, the ratio of wave height to total water depth is chosen as  the criterion to switch from Boussinesq to NSWE, with  threshold value  set to 0.8,  as suggested by Tonelli and Petti. 

The other one is the original eddy--viscosity scheme used in the previous version of FUNWAVE (Kennedy et al., 2000). To fit the eddy--viscosity method in the TVD scheme, the artificial eddy viscosity terms.

.. math:: {\bf R}_{bx} = \frac{\partial }{\partial x} (\nu \frac{\partial P}{\partial x}) + \frac{\partial }{\partial y} (\nu \frac{\partial P}{\partial y} )

.. math:: {\bf R}_{by} = \frac{\partial }{\partial y} (\nu \frac{\partial Q}{\partial y}) + \frac{\partial }{\partial x} (\nu \frac{\partial Q}{\partial x}) 

Note that the form is slightly different from that in Kennedy et al. (2000). The present form was found to give a more stable numerical solution as the cross--derivatives removed. In the present form, :math:`\nu` is the artificial eddy viscosity defined by

.. math:: \nu = B \delta_b^2 (h+\eta) \eta_t

where :math:`\delta_b = 1.2`. In Kennedy et al. (2000), :math:`B` varies smoothly from 0 to 1 so as to avoid an impulsive start of breaking and the resulting instability. In the present TVD model, because there is no instability problem found, we adopt a constant value :math:`B=1` as breaking is initiated

.. math:: B =  1 \ \ \  \eta_t \ge  \eta_t^* 
.. math:: B =  0 \ \ \  \eta_t <  \eta_t^*

The parameter :math:`\eta_t^*` determines the onset and cessation of breaking. Following Kennedy et al., a breaking event begins when :math:`\eta_t` exceeds some initial threshold value :math:`\eta_t^{(I)}`, as breaking develops, the wave will continue to break until :math:`\eta_t` drops below :math:`\eta_t^{(F)}`. However, we do not use the smooth transition as in Kennedy et al. because the present TVD scheme did not encounter any instability problem.  The default values of :math:`\eta_t^{(I)}` and :math:`\eta_t^{(F)}` are :math:`0.65\times 2  \sqrt{gh}` and  :math:`0.15 \sqrt{gh}` as in the previous FUNWAVE version (i.e., Cbrk1 = 0.65 and Cbrk2=0.15 in the present version, see the example in the next section). However, the recent tests showed :math:`\eta_t^{(I)}` should be slightly larger to match the laboratory data. 
