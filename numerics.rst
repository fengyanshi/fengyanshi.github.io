.. _section-numerics:

Numerical Parameters
********************

**SPECIFICATION OF NUMERICS**  


* :code:`Time_Scheme`: stepping option, :code:`Runge_Kutta` or :code:`Predictor_Corrector` (not suggested for this version). Default: :code:`Runge_Kutta`.

* :code:`HIGH_ORDER`: spatial scheme option, :code:`FOURTH` for the fourth-order, :code:`THIRD` for the third-order, and :code:`SECOND` for the second-order (not suggested for Boussinesq modeling).  Default: :code:`FOURTH`. 

* :code:`CONSTRUCTION`: construction method, :code:`HLL` for HLL scheme, otherwise for averaging scheme. Default: HLL.

* :code:`CFL`: CFL number, CFL :math:`\sim` 0.5 (default).

* :code:`FroudeCap`: cap for Froude number in velocity calculation for efficiency. The value could be 1.0 :math:`\sim` 10.0. Default: 3.0

* :code:`MinDepth`: minimum water depth (m) for wetting and drying scheme. Suggestion: :code:`MinDepth = 0.001` for lab scale and 0.01 for field scale. Defaut: 0.01.

* :code:`MinDepthFrc`: merge to :code:`MinDepth` for Version 3.1 or higher. If both :code:`MinDepth` and :code:`MinDepthFrc` are specified, the model takes the Maximum value of :code:`MinDepth` and :code:`MinDepthFrc`.  

