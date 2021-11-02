Wave-maker with wave coherence specification 
***********************************************************
Please refer to `Salatin, R., Chen, Q., Bak, A. S., Shi, F., & Brandt, S. R. (2021). Effects of wave coherence on longshore variability of nearshore wave processes. Journal of Geophysical Research: Oceans, 126, e2021JC01764 <https://doi.org/10.1029/2021JC017641>`_

1. WK\_NEW\_IRR
----------------

WK_NEW_IRR is a directional wavemaker to generate waves with analytic spectra and user specified degree of wave coherence. Input file is similar to the WK\_IRR case. In WK\_IRR, default values are (Nfreq = 45) and (Ntheta = 24). However, in WK_NEW_IRR, default values are (Ntheta = 25) and (Nfreq = 1125). For Ntheta, it is better to choose an odd value to make sure mean direction has wave components. Nfreq of new wavemaker is also equal to Nfreq*Ntheta of WK_IRR (25*45 = 1125) since each wave frequency has only one wave component associated with that. Moreover, alpha_c defines the percentage of coherence, and its value is ranging from 0.0 to 100.0 with a default value of 0.0. Additionally, alpha_c = 100.0 also resembles the WK_IRR wavemaker.

Note: Currently, WK\_NEW\_IRR wavemaker is only capable of generating spectra with equal frequency method. Equal energy method will be developed soon. 

Input.txt .. code-block:: rest

        !-----WAVEMAKER-----         WAVEMAKER = WK_NEW_IRR         DEP_WK = 8.0         Xc_WK = 150.0         Yc_WK = 0.0         FreqPeak = 0.1         FreqMin = 0.04         FreqMax = 0.25         Hmo = 1.0         GammaTMA = 5.0         ThetaPeak = 0.0         Sigma_Theta = 10.0         Nfreq = 1125    ! 45Nfreq*25Ntheta (similar to WK_IRR default values)         Ntheta = 25     ! odd number is recommended (thus mean dir will have a component!)         Delta_WK = 0.5         alpha_c = 50.0  ! degree of coherence in percentage(if a value was not specified,          then alpha_c = 0.0).The corresponding examples for this wavemaker can be found in the following directories: * simple_cases/wave_coherence/Case_NEWIRR_000P_Coherence * simple_cases/wave_coherence/Case_NEWIRR_050P_Coherence * simple_cases/wave_coherence/Case_NEWIRR_100P_Coherence

2. WK\_NEW\_DATA2D
-----------------------

WK\_NEW\_DATA2D is a new wavemaker similar to WK\_DATA2D. The difference is that instead of a gridded spectrum, information of individual waves are provided in the wave2d.txt file. In this file, number of frequencies, wave frequencies, wave directions, wave amplitudes, and phase values are given. In case the phase values were not given to the model, the model will generate them. Directory of this file is mentioned in the input.txt file. Please refer to Salatin et al. (2021) for more information on wave coherence and new wavemakers.

Input.txt .. code-block:: rest

        !-----WAVEMAKER-----         WAVEMAKER = WK_NEW_DATA2D         WaveCompFile = wave2d.txt         DEP_WK = 8.0          Xc_WK = 150.0          Yc_WK = 0.0          Delta_WK = 0.5Wave2d.txt .. code-block:: rest
           2        - NumFreq           8.0      - PeakPeriod             0.125    - Freq wave 1           0.125    - Freq wave 2          12.000    - Dire wave 1         -12.000    - Dire wave 2           0.3	   - Amp wave 1           0.3	   - Amp wave 2           0.0	   - Phase wave 1          20.0       - Phase wave 2The corresponding examples for this wavemaker can be found in the following directories:
 * simple_cases/wave_coherence/Case_DATA2D_000_Spectrum * simple_cases/wave_coherence/Case_DATA2D_050_Spectrum * simple_cases/wave_coherence/Case_DATA2D_100_Spectrum * simple_cases/wave_coherence/Case_DATA2D_1Wave * simple_cases/wave_coherence/Case_DATA2D_2Waves_Coherent * simple_cases/wave_coherence/Case_DATA2D_2Waves_NonCoherent


Examples (2D Beach):
--------------------------
Model setup can be accessed from: `2D beach <https://fengyanshi.github.io/build/html/beach_2d.html>`_. Two example sets are provided for the new wavemakers. First set is for WK\_NEW _IRR and WK _NEW _DATA2D with a full spectrum. While the initial one can generate the wavemaker with given parameters in the input file, for the latter a MATLAB code is provided to generate the analytic spectrum and save as wave2d.txt file.
The MATLAB code can be accessed from:
       simple_cases/wave_coherence/Spectrum_Generator_for_WKDATA2D\Main.m
Moreover, a separate MATLAB code is also provided to transform LOG.txt file of the WK\_NEW\_IRR into wave2d.txt file for WK\_NEW\_DATA2D and is accessible through:
      simple_cases\wave_coherence\Spectrum_Generator_for_WKDATA2\generate_data2d_input_from_wknewirr_LOG.m
Since the input spectra for both wavemakers are the same and results are identical, only the results for WK\_NEW\_IRR are given below. Second example set is for one regular wave, two coherent waves, and two noncoherent waves with very close frequencies. The wave parameters are given by the user to WK\_NEW\_DATA2D wavemaker.
Example Set 1:
------------------
Three levels of coherence (0, 50, and 100% from left to right) can be seen in the input analytic spectra. These spectra are plotted with the MATLAB code in the following directory which uses output LOG.txt file.
    simple_cases/wave_coherence/PostProcessing/LOG_READ.m

.. figure:: images/simple_cases/coher_angle_phase.png
    :align: left
    :figclass: align-left

Surface Elevation snapshots at t = 600 Tp for three levels of coherence (0, 50, and 100% from left to right).

.. figure:: images/simple_cases/coher_surface_ele.png
    :align: left
    :figclass: align-left

Hrms with spin-off = 120 Tp and Averaging time = 880 Tp for three levels of coherence (0, 50, and 100% from left to right). Uniformity in wave height is dependent on df (frequency bin resolution), as well. As number of frequency bins increases and consequently, df decreases, averaging time should also increase to result in more longshore uniform wave processes with no wave coherence.

.. figure:: images/simple_cases/coher_wave_height.png
    :align: left
    :figclass: align-left

Current field with spin-off = 120 Tp and Averaging time = 880 Tp for three levels of coherence (0, 50, and 100% from left to right). Uniformity in current field is dependent on df (frequency bin resolution), as well. As number of frequency bins increases and consequently, df decreases, averaging time should increase to result in longshore uniform wave processes with no wave coherence.

.. figure:: images/simple_cases/coher_current.png
    :align: left
    :figclass: align-left


Example Set 2:
---------------------
This example is 2D Beach with one and two wave components given to the model as user input. Users can extend the number of waves with any wave frequency, direction, and amplitude. Users can also specify phase info for the wave components in the wave2d.txt file. If phase values not specified in the wave input file, FUNWAVE-TVD will assign the random phase values.Surface Elevation snapshots for one wave (left), two coherent waves (middle), and two noncoherent waves with very close frequencies (right) at t = 62.5 Tp... figure:: images/simple_cases/coh_vs_noncoh_ele.png
    :align: left
    :figclass: align-left

Hrms for one wave (left), two coherent waves (middle), and two noncoherent waves with very close frequencies (right) with spin-off = 12.5 Tp and Averaging time period = 50 Tp. 

.. figure:: images/simple_cases/coh_vs_noncoh_height.png
    :align: left
    :figclass: align-left

Current field for one wave (left), two coherent waves (middle), and two noncoherent waves with very close frequencies (right) with spin-off = 12.5 Tp and Averaging time period = 50 Tp. 

.. figure:: images/simple_cases/coh_vs_noncoh_cur.png
    :align: left
    :figclass: align-left








