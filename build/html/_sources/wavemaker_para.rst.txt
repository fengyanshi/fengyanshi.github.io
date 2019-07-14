.. _definition_wavemaker:

Wave-maker
*****************

**SPECIFICATION OF WAVEMAKER**

For theory about wavemaker, see :ref:`section_wavemaker`

 *  WAVEMAKER: wavemaker type. 

 * WAVEMAKER = INI\_REC: initial rectangular hump 
     need Xc,Yc and WID

 * WAVEMAKER = LEF\_SOL: left boundary solitary
     need AMP,DEP, and LAGTIME

 * WAVEMAKER = INI\_SOL: initial solitary wave propagate in +x direction, WKN B solution
     need AMP, DEP, and XWAVEMAKER 

 * WAVEMAKER = INI\_OTH:  other initial distribution specified in the code by users

 * WAVEMAKER = WK\_REG: Wei and Kirby 1999 internal wave maker
      need Xc\_WK, Yc\_WK, Ywidth\_WK, Tperiod, AMP\_WK, DEP\_WK, Theta\_WK, and Time\_ramp (factor of period)

 * WAVEMAKER = WK\_IRR:  Wei and Kirby 1999 TMA spectrum wavemaker (internal)
      need Xc\_WK, Yc\_WK, Ywidth\_WK, DEP\_WK, Time\_ramp, Delta\_WK,  FreqPeak, FreqMin,FreqMax, Hmo, GammaTMA(default: 3.3 ), ThetaPeak (default: 0.0), Nfreq(default: 45), Ntheta(default: 24)
 
     EqualEnergy (=T means the frequency splitting is based on Equal-Energy, otherwise, based on Equal-Frequency space
           
 * WAVEMAKER = JON\_2D:  JONSWAP spectrum wavemaker (internal)
      need Xc\_WK, Yc\_WK, Ywidth\_WK,
      DEP\_WK, Time\_ramp, Delta\_WK,  FreqPeak, FreqMin,FreqMax,
      Hmo, GammaTMA(default: 3.3 ), ThetaPeak (default: 0.0),Nfreq(default: 45), Ntheta(default: 24)
            
 * WAVEMAKER = JON\_1D:  JONSWAP 1D spectrum wavemaker (internal)
      need Xc\_WK, Yc\_WK, Ywidth\_WK,
      DEP\_WK, Time\_ramp, Delta\_WK,  FreqPeak, FreqMin,FreqMax,
      Hmo, GammaTMA(default: 3.3 ), Nfreq(default: 45)  
            
 * WAVEMAKER = TMA\_1D:  TMA 1D spectrum wavemaker (internal)
      need Xc\_WK, Yc\_WK, Ywidth\_WK,
      DEP\_WK, Time\_ramp, Delta\_WK,  FreqPeak, FreqMin,FreqMax,
      Hmo, GammaTMA(Note, still use TMA Gamma, default: 3.3 ), Nfreq(default: 45)                                   

 * WAVEMAKER = WK\_TIME\_SERIES:
      fft  a time series to get each wave component and then use Wei and Kirby's ( 1999) wavemaker. Internal wavemaker The wave angle is zero (x direction) for all wave components. Need input WaveCompFile (including 3 columns: per,amp,pha) and NumWaveComp,PeakPeriod,DEP\_WK, Xc\_WK,Ywidth\_WK
 
 * WAVEMAKER = WK\_DATA2D:  2D directional spectrum data specified in WaveCompFile. Internal wavemaker. Need Xc\_WK, Yc\_WK, DEP\_WK, Delta\_WK. 

     Format of WaveCompFile:

       62  35   - NumFreq NumDir 

       0.0925000011921 - PeakPeriod 

       0.0400 - Freq 

       0.0475 - Freq
 
       ...
 
       -0.05  - Dir (degree)

       0.0    - Dir (degree)

       ...

       0.01133044 0.00973217 ... (amplitude,m)

    The read format in fortran:

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

     CLOSE(1)
 
 * WAVEMAKER = LEFT\_BC\_IRR: Wavemaker at the left boundary (ghost cells). This type of wavemaker reflects waves at the left boundary. Need WAVE\_DATA\_TYPE (DATA,TMA2D,JON2D,JON1D) and other parameters as the same as in the internal wavemaker. Although it is an irregular wavemaker, it can generate regular waves using WAVE\_DATA\_TYPE = DATA by specifying a single wave component.        
       
 * WAVEMAKER = INI_GAUSIAN or INI_GAU: initial Gausian hump, need AMP, Xc, Yc, and WID.          

 * Definations

   * WAVE_DATA_TYPE : Type of wave data needed for LEFT_BC_IRR WaveMaker. It can be DATA or other types used for internal wavemakers

   * AMP : amplitude (m) of initial :math:`\eta`, if  WAVEMAKER = INI\_REC, WAVEMAKER = INI\_SOL, WAVEMAKER = LEF\_SOL.

   *  DEP: water depth at wavemaker location, if WAVEMAKER = INI\_SOL, WAVEMAKER = LEF\_SOL.

   *  LAGTIME, time lag (s) for the solitary wave generated on the left boundary, e.g., WAVEMAKER = LEF\_SOL. 
 
   *  XWAVEMAKER: x  (m) coordinate for WAVEMAKER = INI\_SOL.


   *  Xc: x (m) coordinate of the center of  a rectangular hump if WAVEMAKER = INI\_REC.

   *  Yc: y (m) coordinate of the center of  a rectangular hump if WAVEMAKER = INI\_REC.

   *  WID: width (m) of  a rectangular hump if WAVEMAKER = INI\_REC, or INI\_GAU.


   *  Time\_ramp: time ramp (s) for Wei and Kirby (1999) wavemaker. Default: 0.0.
 
   *  Delta\_WK:  width parameter :math:`\delta`  for Wei and Kirby (1999) wavemaker.    Need trial and error, usually, :math:`\delta` =  :math:`0.3 \sim 0.6`. Default: 0.5. 

   *  DEP\_WK: water depth (m) for Wei and Kirby (1999) wavemaker.

   *  Xc\_WK: x coordinate (m) for Wei and Kirby (1999) wavemaker.

   *  Ywidth\_WK: width (m) in y direction for Wei and Kirby (1999) wavemaker. Default: LARGE (999999.0).

   *  Tperiod:  period (s) of regular wave for Wei and Kirby (1999) wavemaker.

   *  AMP\_WK: amplitude (m) of regular wave for Wei and Kirby (1999) wavemaker.

   *  Theta\_WK: direction (degrees) of regular wave for Wei and Kirby (1999) wavemaker. Note: it may be adjusted if a periodic boundary condition is used. A warning will be given if adjustment is made. 
 
   *  Nfreq: number of frequency components. Default: 45.

   *  Ntheta: number of direction components. Default: 24.

   *  FreqPeak: peak frequency (1/s) for Wei and Kirby (1999) irregular wavemaker.

   *  FreqMin: low frequency cutoff (1/s) for Wei and Kirby (1999) irregular wavemaker.
 
   *  FreqMax: high frequency cutoff (1/s) for Wei and Kirby (1999) irregular wavemaker.

   *  Hmo: Hmo (m) for Wei and Kirby (1999) irregular wavemaker.

   *  GammaTMA, TMA parameter :math:`\gamma` for Wei and Kirby (1999) irregular wavemaker. GammaTMA = 3.3 if JONSWAP is used. 

   *  ThetaPeak: peak direction (degrees) for Wei and Kirby (1999) irregular wavemaker. 

   *  Sigma\_Theta: parameter of directional spectrum for Wei and Kirby (1999) irregular wavemaker.
