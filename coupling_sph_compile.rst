Compile the code for tracking
###################################

**GRID A**

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_nocoupling* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_nocoupling*

**GRID B**

|  **Makefile**

|  EXEC FILE
|            EXEC          = *funwave_coupling* (for example)

|  FLAGS
|            FLAG_1 = -DDOUBLE_PRECISION
|   if parallel add
|            FLAG_2 = -DPARALLEL
|   if intel compiler add
|            FLAG_6 = -DINTEL
|            **FLAG_7 = -DCOUPLING**

|  COMPILER
|            FC       = mpif90 (for example)

  The compiled exe file is *funwave_coupling*