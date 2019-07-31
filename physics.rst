.. _section-physics:

Physics (dispersion, breaking, friction)
****************************************

**SPECIFICATION OF PHYSICS**
  
* :code:`DISPERSION`: logical parameter for inclusion of dispersion terms.  T - calculate dispersion, F - no dispersion terms. Default: T.

* :code:`Gamma1`: parameter for linear dispersive terms. 1.0 - inclusion of linear dispersive terms, 0.0 - no linear dispersive terms. Default: 1.0.

* :code:`Gamma2`: parameter for nonlinear dispersive terms. 1.0 - inclusion of nonlinear dispersive terms, 0.0 - no nonlinear dispersive terms. Default: 1.0.

  :code:`Gamma1 = 1.0, Gamma2 = 0.0` for NG's equations.

  :code:`Gamma1 = 1.0, Gamma2 = 1.0` for the fully nonlinear Boussinesq equations.
  
* :code:`Gamma3`: parameter for linear shallow water equations (:code:`Gamma3 = 1.0`). When :code:`Gamma3 = 0.0, Gamma1` and :code:`Gamma2` automatically become zero. Default: 1.0.

* :code:`Beta_ref`:  parameter :math:`\beta` defined for the reference level. :math:`\beta` = -0.531 for NG's and FUNWAVE equations. Default: -0.531.

* :code:`VISCOSITY_BREAKING`: logical parameter for viscous breaking. When this option is selected, :code:`Cbrk1` and :code:`Cbrk2` are needed. Default is shock-capturing type breaking.

 * :code:`Cbrk1`: parameter :math:`C1` in Kennedy et al. (2000). Default: 0.45

 * :code:`Cbrk2`: parameter :math:`C2` in Kennedy et al. (2000). Default: 0.35

 .. note::  :code:`Cbrk1` and :code:`Cbrk2` were re-calibrated in Choi et al. (2018). :math:`C1` is around 0.45 in FUNWAVE-TVD, instead of :math:`C1 = 0.65` used in Kennedy et al. 


* :code:`SWE_ETA_DEP`: ratio of height/depth for switching from Boussinesq to NSWE for shock-capturing breaking. The value is :math:`\sim` 0.80. 

**SPECIFICATION OF ROLLER EFFECTS**

* :code:`ROLLER_EFFECT`: logical parameter for roller effects. If it is set :code:`TRUE`, the roller and undertow effects will be taken into account into the sediment (suspended load) transport processes. 

**SPECIFICATION OF FRICTION**
  
* :code:`FRICTION_MATRIX`: logical parameter for homogeneous and inhomogeneous frction feild.  T - inhomogeneous, F - homogeneous. Default: F.

* :code:`FRICTION_FILE`: name of friction file if :code:`FRICTION_MATRIX = T`; the file dimensions should be :code:`Mglob x Nglob` with the first point as the south-west corner. The read format in the code is shown below:

  .. code-block:: rest

       DO J=1,Nglob
       
        READ(1,*)(Cd(I,J),I=1,Mglob)a
        
       ENDDO

* :code:`Cd_fixed`: fixed bottom friction coefficient.

* :code:`SHOW_BREAKING`: logical parameter to calculate breaking index. Note that, if :code:`VISCOSITY_BREAKING` is not selected, breaking is calculated using shock wave capturing scheme. The index calculated here is based on Kennedy et al. (2000). 


* :code:`WAVEMAKER_Cbrk`: breaking parameter inside wavemaker. For some cases, the wave breaks inside the wavemaker. This parameter provides :code:`Cbrk` inside the wavemaker domain. For most of cases, set :code:`WAVEMAKER_Cbrk = Cbrk1` or higher. Default: LARGE.

