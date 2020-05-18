.. _definition_sediment:

Sediment Transport and Morphological Change
********************************************

  Theory: :ref:`section_sed_equation`
  
  Numerical scheme: :ref:`section_sed_numerical`

**NUMERICAL SCHEME**

* :code:`Sed_Scheme`: numerical scheme for solving the advection-diffusion equation

 * :code:`Sed_Scheme = TVD`: TVD scheme

 * :code:`Sed_Scheme = Upwinding`: Upwinding scheme (default)

**SEDIMENT PARAMETERS**

* :code:`D50`: median grain diameter :math:`D_{50}`, defalt :math:`D_{50} = 0.5mm`

* :code:`Sdensity`: gravity of sediment :math:`s`, defalt :math:`s = 2.68`

* :code:`n_porosity`: porosity of sediment :math:`n`, defalt :math:`n=0.47`

* :code:`WS`: settling velocity :math:`w_f`, defalt :math:`w_f = 0.125` m/s

* :code:`Shields_cr`: critical Shields parameter for suspended load :math:`\theta_{cr}`, defalt :math:`\theta_{cr} = 0.05`

* :code:`Shields_cr_bedload`: Shields parameter for bedload :math:`\theta_{cr}^{b}`, defalt :math:`\theta_{cr}^{b} = 0.047` based on Meyer-Peter and Muller (1984)

* :code:`Kappa1`: Runge-Kutta parameter :math:`\kappa_1`, defalt :math:`\kappa_1 = 0.3333`, 4th-order

* :code:`Kappa2`: Runge-Kutta parameter :math:`\kappa_2`, defalt :math:`\kappa_1 = 1.0`, 4th-order

* :code:`MinDepthPickup`: the minimum depth for sediment pickup action. The purpose of this parameter is to avoid over-shooting at a very small depth. Default: :code:`MinDepthPickup = 0.1m`.

**MORPHOLOGICAL CHANGE**

* :code:`Bed_Change`: logical parameter,  T: update depth, F: no bed change.

* :code:`Hard_bottom`: logical parameter,  T: hard bed, no erosion allowed, F: sediment bed

* :code:`Hard_bottom_file`: the file contains the distribution of the erodible layer thickness, :math:`Z_s`. A negative value represents 'non-erodible'. For example, :math:`Z_s = 0.1` means the bed can be eroded at most 0.1 m. If you set -0.1 (m) at a grid point, the bed at this point will not be eroded. In practice, the bed can still be eroded when a deposition makes the  bottom level greater than 0.1 m (above the initial level). Therefore, specify a smaller value, such as -100.0, if you want to make this point non-erodible. The format is the same as the depth file.

.. note:: The previous version before 3.4 used the hard bottom masks rather than erodible thickness.  

* :code:`Morph_step`: ratio of Boussinesq model time step to the morphological updating step, :math:`dt_{morph}`, defalt: :math:`dt_{morph}` = 25

**AVALANCHE**

* :code:`Avalanche`: logical parameter,  T: consider avalanche, F: not consider avalanche

* :code:`Tan_phi`: tangent of the repose angle :math:`\tan \phi`, defalt :math:`\tan \phi = 0.7`, or 35 deg


**OUTPUT**

* :code:`PLOT_INTV_SEDIMENT`: time interval for plotting sediment transport variables, defalt is the same as the Boussinesq model

* :code:`C_xxxxx`: Sediment concentration (g/l) at xxxxx output step

* :code:`Pick_xxxxx`: sediment pickup value at xxxxx output step

* :code:`Depo_xxxxx`: sediment deposition value at xxxxx output step

* :code:`DchgS_xxxxx`: depth change (without considering porosity ) due to suspended load UPTO xxxxx output step

* :code:`DchgB_xxxxx`: depth change (without considering porosity ) due to  bedload UPTO xxxxx output step

* :code:`BedFx_xxxxx`: bedload flux in x

* :code:`BedFy_xxxxx`: bedload flux in y

* :code:`dep_xxxxx`: depth (with considering porosity) UPTO xxxxx output step









