Morphological Evolution
**************************

Morphological evolution is computed using the sediment continuity equation, in which the time-averaged pickup and deposition rates are used. The sediment continuity equation is written as

.. math:: \frac{d \bar{Z}_b}{dt} = \frac{1}{1-n}(\bar{P} - \bar{D})

where :math:`\bar{Z}_b` are the time-averaged depth changes with positive values for erosion and negative values for deposition, :math:`\bar{P}` and :math:`\bar{D}` are the time averaged pickup and deposition rates averaged over :math:`dt_{\mbox{morph}}`. In Tehranirad et al. (2016),   :math:`dt_{\mbox{morph}} = 5 \sim 20` is recommended to be small enough to capture bed changes induced by tsunami waves. In ship-wake applications, :math:`dt_{\mbox{morph}}` should be smaller than the long wave cases. A specific range of morphological time step (:math:`dt_{\mbox{morph}}`) for ship-wake applications, however, needs a further investigation based on numerical simulations carried out against measured data. 


