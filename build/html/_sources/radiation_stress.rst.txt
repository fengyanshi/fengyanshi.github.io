.. _section_radiation:

Calculation of radiation stresses
*************************************

**Momentum Balance at the wave-averaged scale**

The :math:`x` and :math:`y`-direction momentum balances can be examined using the concept of radiation stresses introduced by Longuet-Higgins and Stewart (1964). The major terms in the momentum balances can be presented by the wave-averaged, depth-integrated shallow water equations for time-steady flow,

.. math:: \frac{\partial \bar{P}\bar{P}/H}{\partial x} + \frac{\partial \bar{P}\bar{Q}/H}{\partial y}+ gH\frac{\partial \bar{\eta}}{\partial x}+ \frac{\partial S_{xx}}{\partial x} + \frac{\partial S_{xy}}{\partial y} + gH\frac{\partial \bar{\eta}}{\partial x} + \bar{\tau}_x+ R_x =0,

.. math:: \frac{\partial \bar{Q}\bar{Q}/H}{\partial y} + \frac{\partial \bar{P}\bar{Q}/H}{\partial x}+ gH\frac{\partial \bar{\eta}}{\partial y}+ \frac{\partial S_{yy}}{\partial y} +  \frac{\partial S_{xy}}{\partial x} + gH\frac{\partial \bar{\eta}}{\partial y} + \bar{\tau}_y+ R_y =0,

where :math:`\bar{()}` represents wave-averaging. :math:`H = h + \bar{\eta}`, is the wave-averaged water depth with :math:`h` and :math:`\eta` representing the still water depth and surface elevation, respectively.  In the Cartesian coordinates (:math:`x,y`), :math:`(\bar{P}, \bar{Q})` are wave-averaged volume fluxes in (:math:`x,y`) directions. (:math:`\bar{\tau}_x, \bar{\tau}_y)` represent the bottom friction. :math:`g` is the gravitational acceleration constant.  The calculation of  radiation stresses :math:`S_{xx} `, :math:`S_{yy}`, and :math:`S_{xy}` is desribed below. 
In the equations above, :math:`R_x` and :math:`R_y` are residual momentum terms in the momentum balances in :math:`x-` and :math:`y-` directions, respectively, including contributions from dispersive terms, diffusion terms, as well as numerical errors. 


**Calculation of radiation stresses**

The radiation stresses can be expressed by

.. math:: S_{xx} = \overline{\int_{-h}^\eta (u^2-w^2) dz } + \frac{1}{2} g \overline{\eta^2},

.. math:: S_{yy} = \overline{\int_{-h}^\eta (v^2-w^2) dz } + \frac{1}{2} g \overline{\eta^2},

.. math:: S_{xy} = \overline{\int_{-h}^\eta uv dz },

where :math:`(u,v,w)` represent velocity components in :math:`(x,y,z)` directions. The velocity components were estimated by modeled velocity field accurate up to :math:`O(\mu^2)`.  To make it convenient to remove wave-averaged current velocity from the instantaneous velocity, we used the depth-averaged velocity :math:`\tilde{\bf u} = \bf{u}_\alpha + {\bf \bar{u}}_2`, in which :math:`\bf{u}_\alpha` denotes the velocity at a reference elevation and :math:`{\bf \bar{u}}_2` is the depth averaged :math:`O(\mu^2)` contribution to the horizontal velocity field. 
The vertical component :math:`w` was estimated by :math:`w(x,y,z,t) = - \mu^2 \nabla \cdot [(h+z) {\bf u}_{\alpha}]`. The depth-averaged vertical velocity :math:`\tilde{w}` was roughly estimated as half of the vertical velocity at the surface, i.e., :math:`\tilde{w} = w(x,y,\eta,t)/2`. The final expressions of radiation stresses are 

.. math::
 S_{xx} = \overline{[(\tilde{u}-\tilde{u}_m)^2 - \tilde{w}^2] (h+\eta)} +\frac{1}{2} g \overline{\eta^2},
 
.. math::
 S_{yy} = \overline{[(\tilde{v}-\tilde{v}_m)^2 - \tilde{w}^2] (h+\eta)} +\frac{1}{2} g \overline{\eta^2},
 
.. math::
 S_{xy} = \overline{(\tilde{u}-\tilde{u}_m)(\tilde{v}-\tilde{v}_m) (h+\eta)},

where (:math:`\tilde{u}_m, \tilde{v}_m`) represent the wave-averaged, depth-averaged velocities in (:math:`x,y`) directions. As mentioned above, the use of depth-averaged wave velocity is for the purpose of removing wave-averaged current velocity from the wave component. Therefore, the ordering of the terms in the radiation stresses above is not consistent with the derivation of the fully nonlinear Boussinesq model (Wei et al., 1995). Errors may exist in :math:`O(\mu^4)` contributions. 

Calculations of time averaged quantities (:math:`\tilde{u}_m, \tilde{v}_m`),    :math:`(\bar{P}, \bar{Q})` and the radiation stresses, :math:`S_{xx}`, :math:`S_{xy}`, :math:`S_{yy}`, are integrated in specified time segments, such as 20 wave periods. In the calculations of the instantaneous wave velocity, such as :math:`\tilde{u} - \tilde{u}_m`, the averaged value :math:`\tilde{u}_m` is from the averaging in the last time segment. 

**Output of radiation stress and other momentum balance terms**

To make outputs of radiation stress and other momentum balance terms, set

:code:`Radiation = T`
 
:code:`T_INTV_mean = 200.0`

(average every 200 s)

:code:`STEADY_TIME=1000.0`

(make averaging after 1000 s)

List of terms (left column:file names with < > for file numbers, right column: terms):

* :code:`DxSxx_< >` :   :math:`\frac{\partial S_{xx}}{\partial x}`

* :code:`DySxy_< >` :   :math:`\frac{\partial S_{xy}}{\partial y}`

* :code:`DxSxy_< >` :   :math:`\frac{\partial S_{xy}}{\partial x}`

* :code:`DySyy_< >` :   :math:`\frac{\partial S_{yy}}{\partial y}`

* :code:`DxUUH_< >` :   :math:`\frac{\partial \bar{P}\bar{P}/H}{\partial x}`

* :code:`DyUVH_< >` :   :math:`\frac{\partial \bar{P}\bar{Q}/H}{\partial y}`

* :code:`DxUVH_< >` :   :math:`\frac{\partial \bar{P}\bar{Q}/H}{\partial x}`

* :code:`DyVVH_< >` :   :math:`\frac{\partial \bar{Q}\bar{Q}/H}{\partial y}`

* :code:`PgrdX_< >` :   :math:`gH\frac{\partial \bar{\eta}}{\partial x}`

* :code:`PgrdY_< >` :   :math:`gH\frac{\partial \bar{\eta}}{\partial y}`

**Example**

An example of the momentum balance calculation can be found in :code:`/simple_cases/short_crest_radiation/` or Zhang et al. (2022). 



