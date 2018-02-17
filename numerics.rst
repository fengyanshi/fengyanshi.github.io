Numerical Parameters
**********************

**SPECIFICATION OF NUMERICS**  


 *  Time\_Scheme: stepping option,  Runge\_Kutta or Predictor\_Corrector (not suggested for this version). Default: Runge\_Kutta.

 *  HIGH\_ORDER: spatial scheme option,  FOURTH for the fourth-order, THIRD for the third-order, and SECOND for the second-order (not suggested for Boussinesq modeling).  Default: FOURTH. 

 *  CONSTRUCTION: construction method,  HLL for HLL scheme, otherwise for averaging scheme. Default: HLL.

 *  CFL: CFL number, CFL :math:`\sim` 0.5 (default).

 *  FroudeCap: cap for Froude number in velocity calculation for efficiency. The value could be 1.0 :math:`\sim` 10.0. Default: 3.0

 *  MinDepth: minimum water depth (m) for wetting and drying scheme. Suggestion: MinDepth = 0.001 for lab scale and 0.01 for field scale. Defaut: 0.01.

 *  MinDepthFrc: merge to MinDepth for Version 3.1 or higher. 

