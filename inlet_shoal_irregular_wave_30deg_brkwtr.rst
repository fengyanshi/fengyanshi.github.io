.. _section-inlet-irr30-brk:

30 deg irregular waves, a submerged/emerged breakwater
######################################################

.. figure:: images/simple_cases/eta_inlet_shoal_irr_30deg_brk.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Replace the obstacle from :ref:`section-inlet-irr30-obs` with a submerged breakwater in "input.txt". Refer to :ref:`section-inlet-basics` for domain setup.

 Set descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = inlet_irr_30deg_brk
 
 Comment out the :code:`OBSTACLE_FILE` and replace the :code:`DEPTH_FILE` with a bathymetry file representative of a submerged breakwater:

 .. code-block:: rest

        !-----DEPTH-----
         DEPTH_TYPE = DATA
         DEPTH_FILE = ../bathy/dep_shoal_inlet_brk.txt

         ! OBSTACLE_FILE = ../bathy/obs_shoal_inlet.txt

 Refer to :ref:`example_bathy_breakwater` for more information.


