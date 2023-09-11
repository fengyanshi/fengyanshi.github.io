Compile the code for a precipitation case
###########################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_precip* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|            FLAG_4 = -DCARTESIAN 
|            FLAG_16 = -DPRECIPITATION
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL

|  COMPILER
|            FC       = mpif90 (for example)

