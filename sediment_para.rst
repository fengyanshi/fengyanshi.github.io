.. _definition_sediment:

Sediment Transport and Morphological Change
********************************************

  Theory: :ref:`section_sed_equation`
  
  Numerical scheme: :ref:`section_sed_numerical`

**NUMERICAL SCHEME**

* Sed\_Scheme: numerical scheme for solving the advection-diffusion equation

* Sed\_Scheme = TVD: TVD scheme

* Sed\_Scheme = Upwinding: Upwinding scheme (defalt)

**SEDIMENT PARAMETERS**

* D50: median grain diameter :math:`D_{50}`, defalt :math:`D_{50} = 0.5mm`

* Sdensity: gravity of sediment :math:`s`, defalt :math:`s = 2.68`

* n\_porosity: porosity of sediment :math:`n`, defalt :math:`n=0.47`

* WS: settling velocity :math:`w_f`, defalt :math:`w_f = 0.125` m/s

* Shields\_cr: critical Shields parameter for suspended load :math:`\theta_{cr}`, defalt :math:`\theta_{cr} = 0.05`

* Shields\_cr_bedload: Shields parameter for bedload :math:`\theta_{cr}^{b}`, defalt :math:`\theta_{cr}^{b} = 0.047` based on Meyer-Peter and Muller (1984)

* Kappa1: Runge-Kutta parameter :math:`\kappa_1`, defalt :math:`\kappa_1 = 0.3333`, 4th-order

* Kappa2: Runge-Kutta parameter :math:`\kappa_2`, defalt :math:`\kappa_1 = 1.0`, 4th-order

* MinDepthPickup: the minimum depth for sediment pickup action. The purpose of this parameter is to avoid over-shooting at a very small depth. Default: MinDepthPickup = 0.1m.  

**MORPHOLOGICAL CHANGE**

* Bed\_Change: logical parameter,  T: update depth, F: no bed change.

* Hard\_bottom: logical parameter,  T: hard bed, no erosion allowed, F: sediment bed

* Hard\_bottom\_file: the file contains the distribution of hard bed points (0:hard bed, 1: sediment bed). The format is the same as the depth file

* Morph\_step: ratio of Boussinesq model time step to the morphological updating step, :math:`dt_{morph}`, defalt: :math:`dt_{morph}` = 25

**AVALANCHE**

* Avalanche: logical parameter,  T: consider avalanche, F: not consider avalanche

* Tan\_phi: tangent of the repose angle :math:`\tan \phi`, defalt :math:`\tan \phi = 0.7`, or 35 deg


**OUTPUT**

* PLOT\_INTV\_SEDIMENT: time interval for plotting sediment transport variables, defalt is the same as the Boussinesq model

* C\_xxxxx: Sediment concentration (g/l) at xxxxx output step

* Pick\_xxxxx: sediment pickup value at xxxxx output step

* Depo\_xxxxx: sediment deposition value at xxxxx output step

* DchgS\_xxxxx: depth change (without considering porosity ) due to suspended load UPTO xxxxx output step

* DchgB\_xxxxx: depth change (without considering porosity ) due to  bedload UPTO xxxxx output step

* BedFx\_xxxxx: bedload flux in x

* BedFy\_xxxxx: bedload flux in y

* dep\_xxxxx: depth (with considering porosity) UPTO xxxxx output step









