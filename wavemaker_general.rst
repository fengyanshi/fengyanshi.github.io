Wave-maker specification
****************************

**SPECIFICATION OF WAVEMAKER**

For theory about the wavemaker, see :ref:`section_wavemaker`

* :code:`WAVEMAKER`: wavemaker type. 

* :code:`WAVEMAKER = INI_REC`: initial rectangular hump 
     need :code:`Xc,Yc` and :code:`WID`

* :code:`WAVEMAKER = LEF_SOL`: left boundary solitary
     need :code:`AMP, DEP`, and :code:`LAGTIME`

* :code:`WAVEMAKER = INI_SOL`: initial solitary wave propagate in +x direction, WKN B solution
     need :code:`AMP, DEP`, and :code:`XWAVEMAKER`

* :code:`WAVEMAKER = INI_OTH`:  other initial distribution specified in the code by users

* :code:`WAVEMAKER = WK_REG`: Wei and Kirby 1999 internal wave maker
      need :code:`Xc_WK, Yc_WK, Ywidth_WK, Tperiod, AMP_WK, DEP_WK, Theta_WK, and Time_ramp` (factor of period)

* :code:`WAVEMAKER = WK_IRR`:  Wei and Kirby 1999 TMA spectrum wavemaker (internal)
      need :code:`Xc_WK, Yc_WK, Ywidth_WK, DEP_WK, Time_ramp, Delta_WK,  FreqPeak, FreqMin,FreqMax, Hmo, GammaTMA` (default: 3.3 ), :code:`ThetaPeak` (default: 0.0), :code:`Nfreq` (default: 45), :code:`Ntheta` (default: 24), :code:`EqualEnergy` (if :code:`TRUE`, this means that the frequency splitting is based on Equal-Energy, otherwise, based on Equal-Frequency space)
           
* :code:`WAVEMAKER = JON_2D`:  JONSWAP spectrum wavemaker (internal)
      need :code:`Xc_WK, Yc_WK, Ywidth_WK,
      DEP_WK, Time_ramp, Delta_WK,  FreqPeak, FreqMin,FreqMax,
      Hmo, GammaTMA` (default: 3.3 ), :code:`ThetaPeak` (default: 0.0), :code:`Nfreq` (default: 45), :code:`Ntheta` (default: 24)
            
* :code:`WAVEMAKER = JON_1D`:  JONSWAP 1D spectrum wavemaker (internal)
      need :code:`Xc_WK, Yc_WK, Ywidth_WK,
      DEP_WK, Time_ramp, Delta_WK,  FreqPeak, FreqMin, FreqMax,
      Hmo, GammaTMA` (default: 3.3 ), :code:`Nfreq` (default: 45)  
            
* :code:`WAVEMAKER = TMA_1D`:  TMA 1D spectrum wavemaker (internal)
      need :code:`Xc_WK, Yc_WK, Ywidth_WK,
      DEP_WK, Time_ramp, Delta_WK,  FreqPeak, FreqMin, FreqMax,
      Hmo, GammaTMA` (Note, still use TMA Gamma, default: 3.3 ), :code:`Nfreq` (default: 45)                                   

* :code:`WAVEMAKER = WK_TIME_SERIES`:
      provide an fft of a time series to get each wave component, and then use Wei and Kirby's (1999) wavemaker. For this internal wavemaker, the wave angle is zero (x direction) for all wave components. Need input :code:`WaveCompFile` (including 3 columns: :code:`per, amp, pha`) and :code:`NumWaveComp, PeakPeriod, DEP_WK, Xc_WK, Ywidth_WK`
 
* :code:`WAVEMAKER = WK_DATA2D`: 2D directional spectrum data specified in :code:`WaveCompFile`. Internal wavemaker. Need :code:`Xc_WK, Yc_WK, DEP_WK, Delta_WK`. 

  Format of :code:`WaveCompFile`:

  .. code-block:: rest

       62  35   - NumFreq NumDir 

       0.0925000011921 - PeakPeriod 

       0.0400 - Freq 

       0.0475 - Freq

       ...

       -0.05  - Dir (degree)

       0.0    - Dir (degree)

       ...

       0.01133044 0.00973217 ... (amplitude,m)

  An example for preparing WaveCompFile can be found in /simple_cases/beach_2d/spectral_data/. It is a case which converts wave data from FRF to the model input. Run the matlab script mk_2d_1d_spec_frf.m to generate a file called wave2d_frf.txt. In input.txt, specify :code:`WaveCompFile = ../spectral_data/MATLAB/wave2d_frf.txt`
  

  The read format in fortran:

  .. code-block:: rest

      OPEN(1,FILE=TRIM(WaveCompFile))

       READ(1,*)NumFreq,NumDir

       ALLOCATE (Amp_Ser(NumFreq,NumDir),  &

          Per_Ser(NumFreq),Theta_Ser(NumDir))

       READ(1,*)PeakPeriod  

       DO J=1,NumFreq

          READ(1,*)Per_Ser(J)  

       ENDDO

       DO I=1,NumDir

          READ(1,*)Theta_Ser(I)

       ENDDO

       DO I=1,NumDir

         READ(1,*)(Amp_Ser(J,I),J=1,NumFreq)

       ENDDO

     ! you dont have to input phase info. The program will skip the phase info
     ! if there is no more data below Amp_Ser
       DO I=1,NumDir

         READ(1,*,END=110)(Phase_2D(J,I),J=1,NumFreq) 

       ENDDO
       
      CLOSE(1)
 
* :code:`WAVEMAKER = LEFT_BC_IRR`: Wavemaker at the left boundary (ghost cells). This type of wavemaker reflects waves at the left boundary. Need :code:`WAVE_DATA_TYPE (DATA, TMA2D, JON2D, JON1D)` and other parameters as the same as in the internal wavemaker. Although it is an irregular wavemaker, it can generate regular waves using :code:`WAVE_DATA_TYPE = DATA` by specifying a single wave component.        
       
* :code:`WAVEMAKER = INI_GAUSSIAN or INI_GAU`: initial Gaussian hump. Need :code:`AMP, Xc, Yc, and WID`.          

**Definitions:**

 * :code:`WAVE_DATA_TYPE`: Type of wave data needed for :code:`LEFT_BC_IRR` WaveMaker. It can be DATA or other types used for internal wavemakers

 * :code:`AMP`: amplitude (m) of initial :math:`\eta`, if :code:`WAVEMAKER = INI_REC, WAVEMAKER = INI_SOL, WAVEMAKER = LEF_SOL`.

 * :code:`DEP`: water depth at wavemaker location, if :code:`WAVEMAKER = INI_SOL, WAVEMAKER = LEF_SOL`.

 * :code:`LAGTIME`, time lag (s) for the solitary wave generated on the left boundary, e.g., :code:`WAVEMAKER = LEF_SOL`. 
 
 * :code:`XWAVEMAKER`: x (m) coordinate for :code:`WAVEMAKER = INI\_SOL`.

 * :code:`Xc`: x (m) coordinate of the center of  a rectangular hump if :code:`WAVEMAKER = INI_REC`.

 * :code:`Yc`: y (m) coordinate of the center of  a rectangular hump if :code:`WAVEMAKER = INI_REC`.

 * :code:`WID`: width (m) of  a rectangular hump if :code:`WAVEMAKER = INI\_REC, or INI\_GAU`.

 * :code:`Time_ramp`: time ramp (s) for Wei and Kirby (1999) wavemaker. Default: 0.0.
 
 * :code:`Delta_WK`: width parameter :math:`\delta`  for Wei and Kirby (1999) wavemaker.    Need trial and error, usually, :math:`\delta` =  :math:`1.0 \sim 3.0`.  

 * :code:`DEP_WK`: water depth (m) for Wei and Kirby (1999) wavemaker.

 * :code:`Xc_WK`: x coordinate (m) for Wei and Kirby (1999) wavemaker.

 * :code:`Yc_WK`: y coordinate (m) for Wei and Kirby (1999) wavemaker.

 * :code:`Ywidth_WK`: width (m) in y direction for Wei and Kirby (1999) wavemaker. Default: LARGE (999999.0).

 * :code:`Tperiod`: period (s) of regular wave for Wei and Kirby (1999) wavemaker.

 * :code:`AMP_WK`: amplitude (m) of regular wave for Wei and Kirby (1999) wavemaker.

 * :code:`Theta_WK`: direction (degrees) of regular wave for Wei and Kirby (1999) wavemaker. Note: it may be adjusted if a periodic boundary condition is used. A warning will be given if adjustment is made. 
 
 * :code:`Nfreq`: number of frequency components. Default: 45.

 * :code:`Ntheta`: number of direction components. Default: 24.

 * :code:`FreqPeak`: peak frequency (1/s) for Wei and Kirby (1999) irregular wavemaker.

 * :code:`FreqMin`: low frequency cutoff (1/s) for Wei and Kirby (1999) irregular wavemaker.
 
 * :code:`FreqMax`: high frequency cutoff (1/s) for Wei and Kirby (1999) irregular wavemaker.

 * :code:`Hmo`: Hmo (m) for Wei and Kirby (1999) irregular wavemaker.

 * :code:`GammaTMA`: TMA parameter :math:`\gamma` for Wei and Kirby (1999) irregular wavemaker. :code:`GammaTMA = 3.3` if JONSWAP is used. 

 * :code:`ThetaPeak`: peak direction (degrees) for Wei and Kirby (1999) irregular wavemaker. 

 * :code:`Sigma_Theta`: parameter of directional spectrum for Wei and Kirby (1999) irregular wavemaker.

