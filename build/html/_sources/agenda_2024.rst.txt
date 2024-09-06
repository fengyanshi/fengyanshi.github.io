
.. _workshop24_agenda:

AGENDA - FUNWAVE-TVD WORKSHOP 2024

**Monday July 22nd:** 

Ice-breaker social:  5:30pm-7:30pm, Embassy Suites by Hilton

**Day 1: Tuesday July 23rd**
 * 8:00 am Registration and breakfast (on your own)
 * 9:00-9:05 Welcome (Jack Puleo, Department Chair)
 * 9:05-9:15 Introductions (Lead: Malej/Torres)
 * 9:15-9:30 Goals for the workshop and logistics - Shi/Malej/Torres (TBD)
 * 9:30-10:00  Finite difference calculations of weakly and fully-nonlinear wave shoaling and breaking - Jim Kirby
 * 10:00-10:30 FUNWAVE-TVD update - Fengyan Shi
 * 10:30-11:00 Break (group photo)
 * 11:00-11:30 Model development and applications for the US Army Corps of Engineers - Matt Malej
 * 11:30-12:00 Short discussion
 * 12:00-1:30 Lunch (on your own)
 * 1:30-3:00 Training Session #1， Lead: Shi
 * 3:00-3:30 Break
 * 3:30-5:00 Training Session #2,  Lead: Torres
 * 6:30         Group dinner (under name: Marissa Torres)
     * 20 people at Deer Park Tavern 108 W Main St  
     * 25-30 people @ Iron Hill Brewery 147 E Main St

**Day 2: Wednesday July 24th**
===================================

 * 8:00 am  Breakfast (on your own)
 * 9:00-9:30 Jim Chen (Northeastern U.) Detecting wave coherence based on observation of alongshore swash variation
 * 9:30-10:00 Ryan Schanta (UD), Predicting Nonlinear Wave Properties using Convolutional Neural Networks Trained on FUNWAVE Outputs
 * 10:00-10:30 Yashar Rafati (HDR), FUNWAVE Modeling for the Design of Harbors and Coastal Infrastructure in the US Southwest
 * 10:30-11:00 Break
 * 11:00-11:30 Chris Malone (UD/Moffatt Nichol), Simulation of tsunami-induced sediment transport and coastal morphology change 
 * 11:30-12:00 Said Parlad (UNIVPM, Italy), Reconstruction of Nearshore Wave Propagation by Combining Remote Sensing Tools and Model Chain
 * 12:00-1:30 Lunch (on your own)
 * 1:30-3:00 Training Session #3 - Lead: Shi
 * 3:00-3:30 Break
 * 3:30-5:00 Training Session #4 - Lead: Lam
 * 7:00       Group dinner (under name: Marissa Torres) 
    * 25-30 people at Iron Hill Brewery 147 E Main St

**Day 3: Thursday July 25th**
==============================

 * 8:00 am Breakfast (on your own)
 * 9:00-9:30 Danial Golbaz (UD), Rain impacts on wave dynamics: the precipitation module in FUNWAVE-TVD
 * 9:30-10:00  Zaid Abdallah Khalil AL Husban (UD), Modeling the effects of Nor'easters on southern Delaware Bay shoreline
 * 10:00-10:30  Michael Lam (ERDC/CHL), Ship-induced Waves and Assessment of Erosion/Scour Hotspots and Potential Impacts to Hurricane-Flood Protection System in SNWW (Houston-Galveston)
 * 10:30-11:00 Break
 * 11:00-11:30 Marissa Torres (ERDC/CRREL), Leveraging FUNWAVE for natural and nature-based features applications
 * 11:30-12:00 Modeling tips (Torres/Shi)
 * 12:00-1:30 Lunch
 * 1:30-3:00 Group session – Defining problems and Future Model Development Efforts and Enhancements (Lead: Shi/Malej/Lam/Torres), followd by problem-solving in groups (Training session #5)
 * 3:00-3:30 Break
 * 3:30-5:00 Problem-solving in groups and conclusions (Training session #6)


**Training Session Topics**
==============================

TUESDAY: Training Session #1 (Hands-on afternoon sessions) [Lead:  Shi]

 * FUNWAVE-TVD and Parallel Computing (MPI) - Documentation Wiki 
 * Latest stable version (3.6) + beta version - current capabilities and those in development 
 * Where do I get the code? - Version Control (Github)
 * Sandbox for USACE and DoD member with GUI
 * How to build (compile/link) and install FUNWAVE-TVD on different machines for parallel computation?


TUESDAY: Training Session #2 [Lead:  Torres]

 * How to run FUNWAVE-TVD? Navigating the basic sections within the INPUT file for different simulations (numerics, physics, input, output, etc.).
 * Setting up (Linux/Mac OS X and HPC machines with PBS scheduler), running, and post-processing your first FUNWAVE-TVD simulation (1D beach runup or levee overtopping with shoaling and wetting/drying).

    PROGRESSION (for those participants needed additional challenge) - use the levee bathymetry to simulate a regular monochromatic wave overtopping the levee

 * 2D plane beach case with various wave conditions (different wavemakers)

 1) monochromatic waves 
 2) Irregular waves

    PROGRESSION (for those participants needed additional challenge) - Analysis of wave-averaged properties. 


WEDNESDAY: Training Session #3 [Lead: Shi]

 Wave simulation on 2D random bathymetry with complex shoreline geometries

 1) Inlet problem (to include post-processing analysis of Harbor Resonance)
 2) Obstacles and Breakwaters (partially absorbing and reflecting inner boundaries) 

    PROGRESSION (for those participants needed additional challenge) - Set up your own surface wave case

WEDNESDAY: Training Session #4 [Lead: Lam]

 * Ship-wakes

   1) Setup with multiple vessels (paths, size, velocities)
   2) A vessel moving on random bathymetry 


    PROGRESSION (for those participants needed additional challenge) - Try the case of the circular island and set up a different path. 


THURSDAY: Training Session #5 [Lead: Shi/Torres/Malej/Lam]

 * Group projects
         *  Wind waves
         * Sediment transport
         * Ship wakes
         * Tsunami
         * USACE-specific projects


