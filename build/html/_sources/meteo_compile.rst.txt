Compile the code for meteotsunami case
########################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_meteo* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|            FLAG_4 = -DCARTESIAN 
|            FLAG_16 = -DMETEO
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_meteo*