.. _section_non_erodible:

Non-erodible Bed
****************

A non-erodible bed can be specified in the morphological module to represent some non-erodible coastal structures such as breakwaters, sea walls, and concrete constructions. The spatial distribution of an erodible layer with variable thickness :math:`Z_s` (m) is defined in the computational domain with a separate input file. The non-erodible condition can be described as:

.. math:: P = \bar{P}, \hspace{1cm} \bar{Z}_b \leq Z_s

In the model input, a user can specify an erodible thickness :math:`Z_s` with :code:`HARD_BOTTOM = F` and :code:`HARD_BOTTOM FILE = your_filname.txt`, where zero or negative values represent non-erodible bed and positive values represent erodible bed up to :math:`Z_s` thickness. See :ref:`_definition_sediment` for more information.
