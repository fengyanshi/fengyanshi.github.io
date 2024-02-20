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

*Non-cohesive*

* :code:`D50`: median grain diameter :math:`D_{50}`, default :math:`D_{50} = 0.5mm`

* :code:`Sdensity`: gravity of sediment :math:`s`, default :math:`s = 2.68`

* :code:`n_porosity`: porosity of sediment :math:`n`, default :math:`n=0.47`

* :code:`WS`: settling velocity :math:`w_f`, default :math:`w_f = 0.125` m/s

* :code:`Shields_cr`: critical Shields parameter for suspended load :math:`\theta_{cr}`, default :math:`\theta_{cr} = 0.05`

* :code:`Shields_cr_bedload`: Shields parameter for bedload :math:`\theta_{cr}^{b}`, default :math:`\theta_{cr}^{b} = 0.047` based on Meyer-Peter and Muller (1984)

* :code:`Kappa1`: Runge-Kutta parameter :math:`\kappa_1`, default :math:`\kappa_1 = 0.3333`, 4th-order

* :code:`Kappa2`: Runge-Kutta parameter :math:`\kappa_2`, default :math:`\kappa_1 = 1.0`, 4th-order

* :code:`MinDepthPickup`: the minimum depth for sediment pickup action. The purpose of this parameter is to avoid over-shooting at a very small depth. Default: :code:`MinDepthPickup = 0.1m`.

*Cohesive*

* :code:`CohesiveSediment` : flag for cohesive sediment, default FALSE

* :code:`k_coh`: diffusion coefficient, default :math:`k = 10E-6` (different from the non-cohesive sediment transport)

* :code:`Tau_cr_coh`: critical shear stress for erosion, default :math:`\tau_{cr} = 0.001`

* :code:`Tau_crd_coh`: critical shear stress for deposition, default :math:`\tau_{cd} = 0.001`

* :code:`a_coh, b_coh, n_coh` and :math:`m_coh`: Empirical parameters used to calculate settling velocity, default values are :math:`a = 0.1`, :math:`b = 2.0`, :math:`n = 0.5`, and :math:`m = 1.5`

* :code:`E_coh`: erodibility parameter, default :math:`E = 0.0001`

* :code:`alpha_coh`: alpha-coefficient used to calculate the erosion rate for soft bed, default :math:`\alpha = 1.0` (if :code:`SoftBed = T`)

**MORPHOLOGICAL CHANGE**

* :code:`Bed_Change`: logical parameter,  T: update depth, F: no bed change.

* :code:`Hard_bottom`: logical parameter,  T: hard bed, no erosion allowed, F: sediment bed

* :code:`Hard_bottom_file`: the file contains the distribution of the erodible layer thickness, :math:`Z_s`. Zero or a negative value represents 'non-erodible'. For example, :math:`Z_s = 0.1` means the bed can be eroded at most 0.1 m. The format is the same as the depth file.

.. note:: The previous version before 3.4 used the hard bottom masks rather than erodible thickness.  

* :code:`Morph_step`: ratio of Boussinesq model time step to the morphological updating step, :math:`dt_{morph}`, default: :math:`dt_{morph}` = 25

**AVALANCHE**

* :code:`Avalanche`: logical parameter,  T: consider avalanche, F: not consider avalanche

* :code:`Tan_phi`: tangent of the repose angle :math:`\tan \phi`, default :math:`\tan \phi = 0.7`, or 35 deg


**OUTPUT**

* :code:`PLOT_INTV_SEDIMENT`: time interval for plotting sediment transport variables, default is the same as the Boussinesq model (:code:`PLOT_INTV`)

* :code:`C_xxxxx`: Sediment concentration (g/l) at xxxxx output step

* :code:`Pick_xxxxx`: sediment pickup value at xxxxx output step

* :code:`Depo_xxxxx`: sediment deposition value at xxxxx output step

* :code:`DchgS_xxxxx`: depth change (without considering porosity) due to suspended load UPTO xxxxx output step

* :code:`DchgB_xxxxx`: depth change (without considering porosity) due to  bedload UPTO xxxxx output step

* :code:`BedFx_xxxxx`: bedload flux in x

* :code:`BedFy_xxxxx`: bedload flux in y

* :code:`dep_xxxxx`: depth (with considering porosity) UPTO xxxxx output step

* :code:`BedStr_xxxxx`: bed shear stress (non-dimensional) UPTO xxxxx output step; multiply by :math:`\rho_w` to convert to physical value of :math:`\tau_b`









