Compile the code for shipwake + sediment case
###############################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_vessel* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|            FLAG_4 = -DCARTESIAN 
|            FLAG_12 = -DVESSEL
|            FLAG_16 = -DSEDIMENT
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_vessel*
