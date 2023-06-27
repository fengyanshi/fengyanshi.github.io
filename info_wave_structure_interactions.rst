.. _literature_interactions:

**************************************
Wave Response with Coastal Structures
**************************************

Ongoing work with the U.S. Army Engineer Research and Development Center (ERDC) has focused on connecting traditional coastal engineering practices with high-fidelity numerical modeling for the benefit of providing rapid screening of coastal structure alternatives in the planning, engineering, and design phase of a new or existing project. Wave response with coastal structures and general wave-driven processes are very complex and can occur across multiple temporal and spatial scales. With FUNWAVE-TVD, users will soon be able to assess the interaction of nearshore wave processes (e.g., runup, overtopping, reflection and diffraction) with a submerged or emergent coastal feature quickly and efficiently. Coastal features include, but are not limited to, breakwaters, jetties, groins, revetments, seawalls, levees, and dikes. In partnership with Engineering with Nature®, natural and nature-based features are also being considered for implementation in FUNWAVE-TVD.

Getting Started
===============
Users are advised to take care when starting a wave modeling study specific to assessing wave responses on or around a coastal feature. A fundamental level of understanding of the model is required to produce accurate predictions and have reliability in the results. To help you get started, consider the following best practices:

* **Range of validity**: Verify that the wave and water level conditions at your field site or in your study are within the valid range of wave climates that can be resolved in FUNWAVE-TVD. The wavelength :math:`\lambda` must be at least twice the water depth :math:`h` (:math:`\lambda > 2h`) or the produce of the wavenumber :math:`k` and water depth must be less than pi (:math:`kh < \pi`) (Torres et. al. 2022).

* **Energy content**: Consider the desired wave height and energy density that needs to interact with the structure. Even for regular wave (monochromatic) simulations, the total wave energy is expected to decrease over the domain due to numerical dissipation (Torres et. al. 2022). It is recommended to perform a sensitivity analysis of your simulation setup to determine the optimal input wave height, domain size, and domain resolution (among other parameters) for your specific application.

* **Model domain setup**: Some recommendations to consider when setting up the model domain include
	* The spatial resolution :math:`DX, DY` should be at least 60 points per wavelength for the wavelength most needed to be resolved (this could be the peak wavelength of a wave spectrum or the shortest wavelength expected to be produced): :math:`DX < \lambda/60`
	* The ratio of spatial resolution to water depth should be greater than 1/15 for model stability: :math:`DX/h > 1/15`
	* To help reduce wave reflections in the domain, boundary sponge layers should have a width of at least half of the peak or longest expected wavelength.

For those interested in coastal engineering applications, detailed guidance and information on the performance of nearshore coastal structures are best represented by the `Coastal Engineering Manual (2001) <https://www.publications.usace.army.mil/USACE-Publications/Engineer-Manuals/u43544q/636F617374616C20656E67696E656572696E67206D616E75616C/>`_ and `EurOtop manual (2018) <http://www.overtopping-manual.com/>`_, among others. 

Stay tuned for more guidance and recommendations regarding implementing coastal features in FUNWAVE-TVD and computing wave responses of interest in post-processing from the ERDC. This research is being funded by the Coastal Inlets Research Program (CIRP), `cirp.usace.army.mil/<https://cirp.usace.army.mil/>`_.

============
References
============
Torres, M. J., M. Y.-H. Lam, and M. Malej. 2022. Practical Guidance for Numerical Modeling in FUNWAVE-TVD. ERDC TN-22-1. Hanover, NH: U.S. Army Engineer Research and Development Center. DOI: `https://hdl.handle.net/11681/45641 <https://hdl.handle.net/11681/45641>`_.