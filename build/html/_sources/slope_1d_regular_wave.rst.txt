Regular wave 
#############

.. figure:: images/simple_cases/eta_1d_reg.jpg
    :width: 600px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

* Add wavemaker

 WAVEMAKER = WK_REG

 DEP_WK = 10.0 

 Xc_WK = 250.0 

 Yc_WK = 0.0 

 Tperiod = 12.0 

 AMP_WK = 0.5 

 Delta_WK = 3.0  ! the default is 0.5, set a larger number for nonlinear waves

* Add sponge layer

 FRICTION_SPONGE = T 

 DIRECT_SPONGE = T 

 Sponge_west_width =  180.0 
