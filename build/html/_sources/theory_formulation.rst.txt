**INTRODUCTION**
=================================

*************************
**What is FUNWAVE--TVD**
*************************
FUNWAVE--TVD is the TVD version of the fully nonlinear Boussinesq wave model (FUNWAVE) initially developed by Kirby et al. (1998). The development of the present version was motivated by recent needs for modeling of  surfzone--scale optical properties in a Boussinesq model framework,  and  modeling of  Tsunami wave in both a regional/coastal scale for prediction of coastal inundation and a basin scale for wave propagation.  This version  features  several theoretical and numerical improvements, including 1) a more complete set of fully nonlinear Boussinesq equations; 2) MUSCL--TVD solver with adaptive Runge--Kutta time stepping; 3) Shock--capturing wave breaking scheme; 4) wetting--drying moving boundary condition with incorporation of HLL construction method into the scheme; 5) an option for parallel computation.  
The documentation provides derivations of the conservation form of theoretical equations, re--arrangement of pressure gradient term in order to obtain a numerically well--balanced form, detailed numerical schemes, users' manual and examples.


****************************************
**Formulations and Numerical Schemes**
****************************************
A complete set of fully nonlinear Boussinesq equations and derivations of the conservation form of theoretical equations can be found in Shi et al. (2012) (`doi:10.1016/j.ocemod.2011.12.004 <http://www.sciencedirect.com/science/article/pii/S1463500311002010>`_). 

Formulations in the spherical cooridinates can be found in Kirby et al. (2013) (`doi:10.1016/j.ocemod.2012.11.009 <http://www.sciencedirect.com/science/article/pii/S1463500312001692>`_).

********************
**Functions**
********************

Wave breaking
#################

There are two breaking algorithms implemented in the model. One takes the advantage of the shock--capturing scheme in TVD. 
It  follows the approach of Tonelli and Petti (2009),  who successfully used the ability of  NSWE  with a TVD scheme to model moving hydraulic jumps. Thus, the fully nonlinear Boussinesq equations are switched  to NSWE at cells where the Froude number exceeds  a certain threshold. Following Tonelli and Petti, the ratio of wave height to total water depth is chosen as  the criterion to switch from Boussinesq to NSWE, with  threshold value  set to 0.8,  as suggested by Tonelli and Petti. 

The other one is the original eddy--viscosity scheme used in the previous version of FUNWAVE (Kennedy et al., 2000). To fit the eddy--viscosity method in the TVD scheme, the artificial eddy viscosity terms.

.. math:: {\bf R}_{bx} = \frac{\partial }{\partial x} (\nu \frac{\partial P}{\partial x}) + \frac{\partial }{\partial y} (\nu \frac{\partial P}{\partial y} )

.. math:: {\bf R}_{by} = \frac{\partial }{\partial y} (\nu \frac{\partial Q}{\partial y}) + \frac{\partial }{\partial x} (\nu \frac{\partial Q}{\partial x}) 

Note that the form is slightly different from that in Kennedy et al. (2000). The present form was found to give a more stable numerical solution as the cross--derivatives removed. In the present form, :math:`\nu` is the artificial eddy viscosity defined by

.. math:: \nu = B \delta_b^2 (h+\eta) \eta_t

where :math:`\delta_b = 1.2`. In Kennedy et al. (2000), :math:`B` varies smoothly from 0 to 1 so as to avoid an impulsive start of breaking and the resulting instability. In the present TVD model, because there is no instability problem found, we adopt a constant value :math:`B=1` as breaking is initiated

.. math:: B =  1 \ \ \  \eta_t \ge  \eta_t^* 
.. math:: B =  0 \ \ \  \eta_t <  \eta_t^*

The parameter :math:`\eta_t^*` determines the onset and cessation of breaking. Following Kennedy et al., a breaking event begins when :math:`\eta_t` exceeds some initial threshold value :math:`\eta_t^{(I)}`, as breaking develops, the wave will continue to break until :math:`\eta_t` drops below :math:`\eta_t^{(F)}`. However, we do not use the smooth transition as in Kennedy et al. because the present TVD scheme did not encounter any instability problem.  The default values of :math:`\eta_t^{(I)}` and :math:`\eta_t^{(F)}` are :math:`0.65\times 2  \sqrt{gh}` and  :math:`0.15 \sqrt{gh}` as in the previous FUNWAVE version (i.e., Cbrk1 = 0.65 and Cbrk2=0.15 in the present version, see the example in the next section). However, the recent tests showed :math:`\eta_t^{(I)}` should be slightly larger to match the laboratory data. 


Sponge layer
#################

* Larsen and Dancy (L--D type, 1983)

The sponge layer technique introduced by Larsen and Dancy (L--D type, 1983) is implemented in the code. In this method, the variables :math:`\phi`( i.e., :math:`\eta, u, v`) are directly attenuated at every time step:

.. math:: \phi = \phi /C_s

where :math:`C_s` is a damping coefficient function defined by

.. math:: C_s = \alpha_s^{\gamma_x^{i-1}}, \ \ \ \ \ i=1,2, ..., n

where :math:`\alpha_s` and :math:`\gamma_s` are two free parameters. :math:`i` represents grid numbers. Chen et al. (1999) suggested that :math:`\alpha_s =2`, \gamma_s = 0.88 - 0.92`, and :math:`n=50 - 100`. The length of the sponge layer is usually taken to be one or two times the typical wavelength. Chen et al also pointed out that the damping coefficients for optimal absorption are somewhat case--sensitive. 

Recently, some problem was found in application of L--D type sponge layer for long--term simulations. The direct damping method combined with the TVD scheme  generates sawtooth noises with a :math:`2 dx` wave length. The sawtooth noises are usually not noticeable due to small magnitudes. However, they grow gradually with time and may become significant in a long term simulation. If this problem occurs, we suggest using the following friction--type or viscous type sponge layers. Using the combination of L--D and friction/viscous sponge layers may remove the sawtooth noises and also make the wave damping more efficient. 


* Friction type and Diffusion type

The friction--type and viscous type sponge layers directly use the friction terms and diffusion terms existing in the model. The source term for the friction--type sponge can be described as

.. math:: 
  F_{frc} = - C_{sponge} |{\bf u_\alpha}|  (u_\alpha, v_\alpha) h

Note that depth :math:`h` is added in the formula above to make the source term depth--independent in terms of the flux--type momentum equations. For the diffusion--type sponge, the description of diffusion term follows exactly the eddy--viscosity breaking formulation with spatial varying viscosity coefficients :math:`\nu_{sponge}`.  Both coefficients are smoothly ramped in space at the sponge layer boundaries. For example, for a sponge layer on the left end of the domain,  :math:`C_{sponge}` can be written as

.. math:: C_{sponge} = C_{max} \left (1-  \mbox{tanh} \frac{10 (i-1)}{I_{\mbox{width}}-1} \right)

where :math:`C_{max}` is the maximum value of :math:`C_{sponge}` used in the sponger layer. :math:`i` and :math:`I_{\mbox{width}}` represent point number and the layer width in points. Similar expressions can be obtained for sponge layers on three other ends of the domain as well as  the viscous sponge layer. 

The width of the sponge layer is usually taken to be two or three wave lengths for the friction--type and viscous sponge layers. Narrow sponge layers can be used for L--D type sponge layer with a good efficiency but sawtooth noises generated by the method is a concern for long--term simulation. 

Boundary conditions
###################

* Wall boundary condition

A mirror boundary condition is used for a fully reflective wall. 

* Periodic boundary condition

The periodic boundary condition in y (south/north) direction was implemented in the  code. 

Wave--maker
##############

* Internal wavemaker theory

Internal wavemaker was implemented based on Wei and Kirby's (1999) two--way internal wavemaker and Chawla and Kirby's (2000) one--way internal wavemaker (under development). Here, we briefly summarize the formulations used in the wavemakers. Detailed theory can be found in Wei and Kirby (1999) and Chawla and Kirby (2000).    

Wei and Kirby (1999) followed the approach of Larsen and Dancy (1983) who used an ad--hoc source mechanism where water mass is added and subtracted along a straight source/sink line inside the computing domain. This approach works well in a staggered--grid differencing scheme, where water is essentially being added to or drained from a single grid block. In applying this technique to the Boussinesq model on an unstaggered grid, however, Wei and Kirby found that use of a single source line accused high frequency noise, leading to blowup of the model. They then used a partially distributed mass source :math:`f(x,y,t)`

.. math:: f(x,y,t) = g(x) s(y,t)

where :math:`g(x)` is a Gaussian shape function and :math:`s(y,t)` the input time series of the magnitude of source function with an assumption that the center of the source region is parallel to the y--axis. The functions :math:`g(x)` and :math:`s(y,t)` are defined as

.. math:: g(x) = \mbox{exp}[-\beta(x-x_s)^2]

.. math:: s(y,t) = D \mbox{sin} (\lambda y -\omega t)
 
where :math:`\beta` is the shape coefficient for the source function, and :math:`x_s` is the central location of the source in the :math:`x` direction, for a source oriented parallel to the :math:`y` axis, as shown in Figure.  :math:`D` is the magnitude of the source function, :math:`\lambda = k \mbox{sin} (\theta)` the wavenumber in the :math:`y` direction, and :math:`k` is the linear wavenumber. 

For a monochromatic wave or a single wave component of a random wave train, the magnitude :math:`D` of source function can be determined by

.. math:: D = \frac{2 a_0 \cos (\theta) (\omega^2 - \alpha_1 g k^4 h^3) }{\omega k I [1-\alpha(kh)^2]}

where :math:`\alpha = -0.390, \alpha_1 = \alpha + 1/3`, and :math:`I` is the integral given by

.. math:: I = \int^\infty_{-\infty} \exp (-\beta x^2) \exp (-ilx) dx = \sqrt{\frac{\pi}{\beta}} \exp(- l^2/4\beta)

where :math:`l=k\cos (\theta)` is the wavenumber in :math:`x` direction. In theory, the shape coefficient :math:`\beta` can be any number. The larger the value :math:`\beta` is, the narrower the source function becomes. The definition of the source function width :math:`W` is not unique, and here we define :math:`W` to be the distance between two coordinates :math:`x_1` and :math:`x_2` where the corresponding source function heights are equal to :math:`\exp (-5) = 0.0067` times the maximum height :math:`D`. Then :math:`x_1` and :math:`x_2` must satisfy the quadratic equation

.. math:: \beta (x-x_s)^2 = 5

from which the width of source function is given by

.. math:: W = |x_2 - x_1| = 2\sqrt{\frac{5}{\beta}}

In the previous version of FUNWAVE (Kirby et al., 1998), it is suggested that :math:`W` equals about half of the wavelength for monochromatic wave. If :math:`L` is the wavelength, the requirement of :math:`W=\delta L/2` (where :math:`\delta` is of order 1) results in

.. math:: \beta = \frac{5}{(\delta L/4)^2} = \frac{80}{\delta^2 L^2}

For random waves, the value of $\beta$ is determined according to the peak frequency component and then used for all components in the wave train. FUNWAVE--TVD follows the criteria for determining :math:`\beta` though a narrow :math:`W` does not seem to cause any problem. 


.. figure:: images/wavemaker.jpg
    :width: 300px
    :align: center
    :height: 250px
    :alt: alternate text
    :figclass: align-center

For the irregular wavemaker, an extension was made to incorporate an  alongshore periodicity into wave generation,  in order to eliminate a boundary effect on wave simulations. The technique exactly follows the strategy in Chen et al. (2003), who adjusted the distribution of wave directions in each frequency bin to obtain alongshore periodicity. This approach is effective in modeling of  breaking wave--induced nearshore circulation such as alongshore currents and rip currents. 

* Regular wave generation

The generation of monochromatic wave using the internal wavemaker is straightforward. Following the formulations given in 3.7.1, the magnitude of source function :math:`D` is calculated by D equation shown above for given wave amplitude :math:`a_0`, wave angle :math:`\theta`, water depth :math:`h` and wave period. The source function can be obtained using the Source function above. 


* Irregular wave generation using directional spectral data

Irregular waves can be generated by integrating wave components split by frequency and direction and with random phases Each wave component contains wave amplitude :math:`a_0` converted from wave energy, wave angle :math:`\theta` and wave period. The source function for each component can be obtained using the source function. 


* Irregular wave generation using analytical spectrum function

The input for the wavemaker can be wave bulk parameters or directional spectral data. TMA shallow--water spectrum, JONSWAP spectrum and a wrapped--normal directional--spreading function are used to simulate a directional sea state. The combined spectrum function can be expressed as

.. math:: S(f,h,\theta) = E(f,h) G(\theta)

:math:`E` is the energy density distribution as follows

.. math:: E (f,h) = \alpha g^2 f^{-5} (2 \pi)^{-4} \Phi (2\pi f, h) e^{-5/4(f/f_p)^{-4}} \gamma^{e^{[-(f/f_p -1)^2 /2\sigma^2]}} 

in which :math:`f_p` is the peak frequency.  :math:`\gamma` presents a frequency spreading parameter, and :math:`\alpha` and :math:`\sigma` are coefficients which may be found in Bouws et al. (1985).  $\alpha$ is obtained using the input :math:`H_{mo}/H_{sig}`, 

.. math:: \sigma = 0.07  \ \ \ \  f \leq f_p 

.. math:: \sigma = 0.09  \ \ \ \  f > f_p


:math:`\Phi` = 1.0 for the JONSWAP spectrum. For TMA,  :math:`\Phi` may be expressed as

.. math:: \Phi (2 \pi f, h) =\frac{1}{2} \omega_h^2 \ \ \ \  \omega_h \leq 1

.. math:: \Phi (2 \pi f, h) = 1-\frac{1}{2}(2-\omega_h)^2 \ \ \ \ 2 > \omega_h >1
.. math:: \Phi (2 \pi f, h) = 1    \ \ \ \  \omega_h \geq 2

where 

.. math:: \omega_h = 2 \pi f (\frac{h}{g})^{1/2}


here :math:`G(\theta)` is the wrapped normal directional spreading function written as

.. math:: G(\theta) = \frac{1}{2\pi} +\frac{1}{\pi} \sum^N_{n=1} e^{[-\frac{( \sigma_{\theta})^2}{2}]} \cos n\theta 

where :math:`\sigma_{\theta}` denotes circular deviation of the wrapped normal
spreading function. To avoid the computational underflow, :math:`N = 20` in the model.

In the spectral wavemaker, the directional spectrum is first divided into :math:`1000` frequency components and then reconstructed into a user--specified number of components with the equal energy. The directional components s evenly split in each frequency. The source function technique (Wei, et al., 1999) is then used for each component and the final surface elevation function can be written as

.. math:: \eta = \sum^M_{m=1} C_m \cos \omega _m t + \sum^M_{m=1} S_m \sin \omega _m t

where

.. math:: C_m  = \sum^k_{n=1} D_{mn} \cos (k_{mn}y + \varepsilon_{mn})

.. math:: S_m =  \sum^k_{n=1} D_{mn} \sin (k_{mn}y + \varepsilon_{mn})

in which y--axis is oriented along the main axis of the wave maker. :math:`D_{mn}, k _{mn}` and :math:`\varepsilon_{mn}` are respectively the amplitude, wave number in the y direction and phase of a component. The phase can be random. 

The model also provides an option for 1--D spectral wave generation (uni--directional). 


METEO module
####################

The METEO module was initially developed for simulations of meteotsnamis. It now includes subroutines for simulating the wind effects on waves, storm surges, landslide-generated tsunamis and processes related to atmospheric pressure effects. 

* Wind effect on waves

Wind effects are modeled using the wind stress forcing proposed by Chen et al. (2004). The wind stress is expressed by

.. math:: {\bf R}_w = \frac{\rho_a}{\rho} C_{dw} |{\bf U}_{10} - {\bf C}| ({\bf U}_{10} - {\bf C})

where :math:`\rho_a` and :math:`\rho` represent air density and  water density, respectively, :math:`\bf C` is wave celerity.  The wind stress is only applied on wave crests. A free parameter representing a ratio of the forced crest height to maximum surface elevation is implemented in the model. 

* Holland model

Holland model is an analytic model of wind and pressure profiles described based on Hurricanes. The pressure distribution can be expressed by 

.. math:: p = p_c + (p_n-p_c) exp(-A/r^B)

where :math:`p` is the pressure at radius :math:`r`, :math:`p_c` and :math:`p_n` are the central pressure and the ambient pressure, respectively. :math:`A` and :math:`B` are scaling paramters from the model input. The velocity distribution can be described by

.. math:: V_c = [AB(p_n-p_c)exp(-A/r^B)/\rho_a r^B]^{1/2}

Based on the formulations above, it is easy to obtain the following storm parameters

The radius of maximum winds (RMW) is

.. math:: R_w = A^{1/B}

The maximum wind speed

.. math:: V_m = C(p_n-p_c)^{1/2}

where 

.. math:: C = (B/\rho_a e)^{1/2}


* Storm surge

To calculate storm surges, wind stress is applied

.. math:: {\bf R}_w = \frac{\rho_a}{\rho} C_{dw} |{\bf U}_{10}| ({\bf U}_{10})

Note that :math:`\bf C` is not used, compared to the formula for 'Wind effect on waves'. 

* Landslide-generated tsunami

Landslide-generated tsunami can be calculated using the same approach as the meteotsunami. Details will be reported by Woodruff (2017). 


Post Calculations
####################

* Wave height calculation


For spectral wave simulations, both average wave height and root-mean-square wave height are calculated using zero-crossing at each grid point. Significant wave height is evaluated using Goda's (2000) formula

.. math:: H_{1/3} = 4.004\sqrt{m_0}

where

.. math:: m_0 = \frac{1}{t_2-t_1} \int^{t_2}_{t_1} \eta^2 dt






