Compile the code for spherical case
######################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_spherical* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL
|   if Z_alpha 
|            FLAG_9 = -DZALPHA

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_spherical*