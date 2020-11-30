.. _section_non_erodible:

Non-erodible Bed
****************

Non-erodible bed
can be specified in the morphological module to represent some non-erodible coastal structures such as breakwaters, sea walls, and concrete constructions. An erodible layer with a thickness of :math:`Z_s` is defined in a computational domain. The non-erodible condition can be described as:

.. math:: P = \bar{P}, \hspace{1cm} \bar{Z}_b \leq Z_s

In the model input, a user can specify a erodible thickness :math:`Z_s`. A negative value represents erodible. 
