Compile the code for tracking
###################################

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_tracking* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|            FLAG_4 = -DCARTESIAN 
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL
|            FLAG_18 = -DTRACKING

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_tracking*