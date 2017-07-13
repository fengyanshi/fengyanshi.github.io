Compile the code for inlet shoal case
######################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_surface_wave* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|            FLAG_3 = -DSAMPLES
|            FLAG_4 = -DCARTESIAN 
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_surface_wave*