Physics (dispersion, breaking, friction)
*********

**SPECIFICATION OF PHYSICS**
  
 *  DISPERSION: logical parameter for inclusion of dispersion terms.  T - calculate dispersion, F - no dispersion terms. Default: T.

 *  Gamma1: parameter for linear dispersive terms. 1.0 - inclusion of linear dispersive terms, 0.0 - no linear dispersive terms. Default: 1.0.

 *  Gamma2: parameter for nonlinear dispersive terms. 1.0 - inclusion of nonlinear dispersive terms, 0.0 - no nonlinear dispersive terms. Default: 1.0.

  Gamma1=1.0, Gamma2=0.0 for  NG's equations.

  Gamma1=1.0, Gamma2=1.0 for the fully nonlinear Boussinesq equations.
  
 *  Gamma3: parameter for linear shallow water equations (Gamma3 = 1.0). When Gamma3 = 0.0, Gamma1 and Gamma2 automatically become zero. Default: 1.0.

 *  Beta\_ref:  parameter :math:`\beta` defined for the reference level. :math:`\beta` = -0.531 for NG's and FUNWAVE equations. Default: -0.531.

 *  VISCOSITY\_BREAKING : logical parameter for viscous breaking. When this option is selected, Cbrk1 and Cbrk2 needed. Default is shock-capturing type breaking

 *  SWE\_ETA\_DEP: ratio of height/depth for switching from Boussinesq to NSWE for shock-capturing breaking.  The value is :math:`\sim` 0.80. 

**SPECIFICATION OF FRICTION**
  
 *  FRICTION\_MATRIX: logical parameter for homogeneous and inhomogeneous frction feild.  T - inhomogeneous, F - homogeneous. Default: F.

 *  FRICTION\_FILE: file file if  FRICTION\_MATRIX= T , file dimension should be Mglob x Nglob with the first point as the south-west corner.  The read format in the code is shown below.

       DO J=1,Nglob
       
        READ(1,*)(Cd(I,J),I=1,Mglob)
        
       ENDDO

 *  Cd\_fixed: fixed bottom friction coefficient.

*  SHOW\_BREAKING: logical parameter to calculate breaking index. Note that, if VISCOSITY\_BREAKING is not selected,  breaking is calculated using shock wave capturing scheme. The index calculated here is based on Kennedy et al. (2000). 

 *  Cbrk1: parameter C1 in Kennedy et al. (2000). Default: 0.65

 *  Cbrk2:  parameter C2 in Kennedy et al. (2000). Default: 0.35

 *  WAVEMAKER\_Cbrk: breaking parameter inside wavemaker. For some cases, wave breaks inside the wavemaker. This parameter provides Cbrk inside the wavemaker domain. For most of cases, set WAVEMAKER\_Cbrk = Cbrk1 or higher. Default: LARGE.

