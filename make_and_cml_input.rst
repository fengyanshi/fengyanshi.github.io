====================================
Introduction to FUNWAVE-TVD Makefile
====================================

:Author: Zhouteng Ye

Quick start
===========

How to make
-----------

**To whom load has the experience with GNU make, simply skip this
section.**

In FUNWAVE-TVD, the makefile is used to compile the FORTRAN code to an
executable.

If the makefile is named with ``Makefile``, then in the terminal, ``cd``
into the path of the ``Makefile`` and simply type

::

   make

and the makefile will be executed (if not, make sure you have
``GNU make`` installed)

If the the name of the makefile is not ``Makefile``, for example,
``foo``, then corresponding command to execute the ``foo`` makefile is

::

   make -f foo

Sometimes the makefile has different options from the command line
input. For example in FUNWAVE-TVD, there are options like ``clean``,
``clobber``. To execute the specific options, for example, ``clean``,
execute with

::

   make clean

for ``Makefile``

::

   make -f foo clean

for ``foo``.

**The following of the will assume the name of the makefile is Makefile
so that there is no -f option.**

If you are interested in how Makefile works and practice some simple
examples, you can refer to the the `3 <#appendix>`__.

Two ways of compiling
---------------------

Compile in src directory
~~~~~~~~~~~~~~~~~~~~~~~~

This is the way FUNWAVE-TVD used to work, the whole compile process is
taken in ``src`` directory. To compile in this way, either copy the
``Makefile`` from ``GNUMake/Old_Version_Makefiles`` to ``src`` and type

.. code:: shell

   make 

The executable will be generated in ``src`` path.

Compile in any location (Recommended)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

copy one of the makefile in ``GNUMake`` directory to the location where
you would like to compile FUNWAVE-TVD. By setting up the **common
variables** in makefile and **defined flags**, then type

.. code:: shell

   make 

to compile. A work directory will be generated and the executable will
be in the work directory (if the ``WORK_DIR =.`` in makefile, then the
work directory will be the current path).

Example of compile and run FUNWAVE-TVD
--------------------------------------

In ``simple_cases/surface_wave_1d``, an example ``Makefile`` could be
found. In the example makefile, the **common variable** is

.. code:: shell

   FUNWAVE_DIR = ../../..
   WORK_DIR    = .
   COMPILER    = gnu
   PARALLEL    = true
   PRECISION   = single
   EXEC        = funwave

The ``FUNWAVE_DIR`` is set with a *relative path*, the *absolute path*
is more recommended in practical usage. The ``WORK_DIR =.`` so that no
new directory will be created. The ``COMPILER = gnu``,
``PARALLEL = true`` and ``PRECISION = single`` so that this case will be
compiled by ``gnu compiler`` and ``mpi library`` with simple precision.
The final executable name will be ``funwave--gnu-parallel-single``.

Compile the executable
~~~~~~~~~~~~~~~~~~~~~~

``cd`` into ``simple_cases/surface_wave_1d`` directory and typing

.. code:: shell

   make

in , an executable named ``funwave--gnu-parallel-single`` will be
created.

Run the executable
~~~~~~~~~~~~~~~~~~

To run the executable without specify the file name, run

.. code:: shell

   mpirun -np xxx ./funwave--gnu-parallel-single 

``xxx`` is the number of the processor, which should be consistent to
the value of ``PX x PY`` in the input file. In this case, the input file
is ``input.txt``.

To specify the input file when running executable, executed with

.. code:: shell

   mpirun -np xxx ./funwave--gnu-parallel-single FILENAME

``FILENAME`` is the name of the input file.

In this case, we use the ``input_solitary.txt`` as the input file.
``PX = 4`` and ``PY = 1``, so that the number of the processor is 4. The
corresponding bash command would be

.. code:: shell

   mpirun -np 4 ./funwave--gnu-parallel-single input_solitary.txt

Clean the compiler files
~~~~~~~~~~~~~~~~~~~~~~~~

To clean all the compiler related files, including objective files,
module files and pre-processor FORTRAN files. Execute with

.. code:: shell

   make clean

To clean all the ``compiler related files`` and ``the executable``,
execute with

.. code:: shell

   make clobber

To clean up the whole work directory (**Be careful with this option**),
execute with

.. code:: shell

   make extra-clobber

Common variables explained
--------------------------

An example of the **common variables** makefile

.. code:: shell

   FUNWAVE_DIR = /home/FUNWAVE-TVD
   WORK_DIR    = funwave-work
   COMPILER    = gnu
   PARALLEL    = true
   EXEC        = funwave
   PRECISION   = single

-  **FUNWAVE_DIR**:

   The path to FUNWAVE directory, can be either absolute path or
   reference path. To set to current directory, set ``FUNWAVE_DIR = .``

-  **WORK_DIR**:

   The path to the work directory. A new directory will be created named
   $(WORK_DIR) To set to current directory, set ``WORK_DIR = .``

-  **COMPILER**:

   Supported compiler: ``gnu``, ``intel``, and ``pgi``

-  **PARALLEL**:

   parallel flags for the model, either ``true`` or ``false``

-  **PRECISION**:

   precision of the model, either ``single`` or ``double``

-  **EXEC**:

   The name for executable. By default, the name of the executable will
   be "funwave-SUFFIX". ``SUFFIX`` is a self-explanatory string
   depending on the values of the variables above. If the name of the
   executable is not ``funwave``, for example, ``foo``, then the
   executable name will be ``foo`` without any suffix.

Defined flags explained (unfinished)
------------------------------------

-  **FLAG_1 = -DCOUPLING**

-  **FLAG_2 = -DZALPHA**

-  **FLAG_3 = -DMANNING**

-  **FLAG_4 = -DVESSEL**

-  **FLAG_5 = -DMETEO**

-  **FLAG_6 = -DWIND**

-  **FLAG_7 = -DSEDIMENT**

-  **FLAG_8 = -DCHECK_MASS_CONSERVATION**

-  **FLAG_9 = -DTMP**

-  **FLAG_10 = -DTRACKING**

Limitations of the Common variables
-----------------------------------

Compiler and MPI supported by the **basic options**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The combination of ``COMPILER`` and ``PARALLEL`` decides the name of the
compiler command as below

+--------------------------+----------+----------+-----------+
|                          | gnu      | intel    | pgi       |
+==========================+==========+==========+===========+
| PARALLEL=false           | gfortran | ifort    | pgfortran |
+--------------------------+----------+----------+-----------+
| PARALLEL=true (openmpi)  | mpif90   | mpif90   | mpif90    |
+--------------------------+----------+----------+-----------+
| PARALLEL=true (mpich)    | mpif90   | mpif90   | mpif90    |
+--------------------------+----------+----------+-----------+
| PARALLEL=true (intelmpi) | mpif90   | mpiifort |           |
+--------------------------+----------+----------+-----------+

the version of mpi can be specified by ``MPI`` in ``uncommon variables``
category. the

Customize the makefile
======================

For some specific requirement, for example, computational environment,
external libraries, one can either customize the main makefile or the
essential makefile. Multiple versions of the makefiles and essential
makefiles are

Uncommon variables explained
----------------------------

-  **SPHERICAL = false**

   Should be ``true`` or ``false``. If ``true``, FUNWAVE-TVD will be
   compiled with spherical coordinate, if ``false`` (by default),
   FUNWAVE-TVD will be compiled wit Cartesian grid.

-  **DEBUG**

   Should be ``true`` or ``false``. The value of ``DEBUG`` Determine the
   debug and optimization flags as below

   +-------+------------------------+--------------+
   |       | DEBUG=true             | DEBUG=false  |
   +=======+========================+==============+
   | gnu   | -O0 -g -Wall -fPIC     | -O2 -fPIC    |
   +-------+------------------------+--------------+
   | intel | -O0 -check -warn -fPIC | -O2 -fPIC    |
   +-------+------------------------+--------------+
   | pgi   | -O0 -fPIC              | -O2 -fPIC -w |
   +-------+------------------------+--------------+

-  **MPI**

   As mentioned before, the value of the ``MPI`` is referred to
   `1.6.1 <#FCOPTION>`__.

-  **DEF_FC**

   Use Defined compiler name for specific machine. If ``DEF_FC`` is
   empty, the compiler name would be determined by the ``COMPILER``,
   ``MPI`` and ``PARALLEL`` (see `1.6.1 <#FCOPTION>`__). If ``DEF_FC``
   has its value, for example, ``DEF_FC = ftn``, then the code will be
   compiled with ``fnt``.

-  **DEF_FC_FLAG**

   User Defined compiler flags. If ``DEF_FC`` is empty, **DEF_FC_FLAG**
   will do nothing to the makefile. While ``DEF_FC`` is non-empty,
   compiler flags will no long determined by **DEBUG**, but uses the
   value of **DEF_FC_FLAG**.

-  **INCS**

   Include file list (usually external libraries)
-  **LIBS**

   External libraries

Customized main makefile
------------------------

To customize the main makefile, simply adjust the uncommon variables.
This is an easy way to do customization.

**Some notes to the modification**

-  To add ``INC`` or ``LIBS``, one can add the value at the end or the
   line, or add new lines for any of the value in ``LIBS``. For example,
   for some machine, the parallel intel compile is executed with
   ``ifort`` and ``-lmpi`` flag, then adding a new line with
   ``MPILIB = -lmpi`` will work.

-  Be careful with ``intel compiler`` case. FUNWAVE-TVD actually has a
   ``-DINTEL`` flag, if the compiler actually relies on intel
   compiler(In some machine, sgi or Cray actually uses intel compiler),
   this flag should always be turned on.

   If the ``DEF_FC`` actually uses intel compiler, set
   ``COMPILER = intel``.

Customized the essential makefile
---------------------------------

There are different sections in the essential makefile. If you are
familiar with GNU make, this way brings more flexibility.

**Some notes to the modification**

-  In this case, the ``intel compiler`` should also be taken care with
   as FUNWAVE-TVD has a ``-DINTEL`` flag, if the compiler actually
   relies on intel compiler(In some machine, sgi or Cray actually uses
   intel compiler), this flag should always be turned on.

   If you modify the Choice of ``COMPILER`` in the essential makefile,
   the following lines should be modified as well.

.. code:: shell

   ifeq ($(COMPILER),$(filter $(COMPILER), intel, sgi))
     FLAG_INTEL = -DINTEL
   endif

Convert from old version makefile to current version.
-----------------------------------------------------

It is easy to convert the old version makefiles to the current version.
The main difference are ``FC``, ``Defined flags``, ``LIBS`` and
``INCS``. The following two examples shows how to modify the current
version that works equivalent to the old version makefile.

**NOTE: I do not have the access to ONYX or Topaz, the two examples are
remaining to be tested. (July 25, 2019, Zhouteng Ye)**

Example of editing main makefile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

make a copy of ``Makefile`` named ``Makefile_ONYX`` and edit

.. code:: shell

   DEF_FC = fnt
   DEF_FC_FLAG = -module -O2 -g -fPic

Since ``DEF_FC`` is not empty, the fortran compiler would be the value
of ``DEF_FC`` and corresponding flags will be ``DEF_FC_FLAG``.

Example of editing essential makefile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

make a copy of ``Make_Essential`` named ``Make_Essential_Topaz`` and
edit the ``Fortran compiler`` section as below.

.. code:: shell

   ifneq ($(DEF_FC),$(filter $(DEF_FC), ''))
     FC = $(DEF_FC)
   else
   ifeq ($(COMPILER),$(filter $(COMPILER), intel))
     USE_MOD = -module $(MOD_DIR)
     FC = ifort
     MPILIB = -lmpi -Bdynamic
   else ifeq ($(COMPILER),$(filter $(COMPILER), sgi))
     USE_MOD = -module $(MOD_DIR)
     FC = mpiifort
     MPILIB = -Bdynamic
   else
   $(error Fatal ERROR: COMPILER=$(COMPILER) and DEF_FC is empty, Please correct the COMPILER or customize the DEF_FC.)
   endif
   endif

Since both sgi and intel actually uses intel compiler, the following
part should be modified as well

.. code:: shell

   ifeq ($(COMPILER),$(filter $(COMPILER), intel, sgi))
     FLAG_INTEL = -DINTEL
   endif

and in the main file, edit

.. code:: shell

   include $(FUNWAVE_DIR)/GNUMake/Essential/Make_Essential_Topaz

Now you should be able to choose ``intel`` or ``sgi`` from the
``COMPILER`` in the main makefile. When ``COMPILER = sgi``,
``FC = mpiifort``; when ``COMPILER = intel``, ``FC = ifort`` and
``MPILIB = -lmpi``. It should be noted that in this example,
``PARALLEL`` does nothing with the choice of compiler.

Debug during customization
--------------------------

The following two commands would be useful while modifying the main
makefile and essential makefile.

-  **make check-env** Print the compier version and mpi version

-  **make print-foo** Check the value of ``foo`` in Makefile (Or
   Makefile_Essential) For example, ``make print $(EXEC)`` and you will
   see the final ``$(EXEC)`` name

Appendix: Compile a project with Makefile
=========================================

Starting with an example project with 2 files

``pre_processor.f90``

.. code:: fortran

   program main
     Implicit None
   #if defined (double_precision)
     Integer, Parameter :: SP = 8
   #else
     Integer, Parameter :: SP = 4
   #endif

     Real(SP) :: test = 1.0_sp / 3.0_sp

   #if defined (method_1)
     print *, 'method_1, test = ', test
   #elif defined (method_2)
     print *, 'method_2, test = ', test
   #elif defined (method_3)
     print *, 'method_3, test = ', test
   #endif
   end program main

``sub.f90``

.. code:: fortran

   #if defined (method_1)
   subroutine sub
     print *,'method_1' 
   end subroutine sub
   #elif defined (method_2)
   subroutine sub
     print *,'method_2' 
   end subroutine sub
   #else
   subroutine sub
     print *,'method_3' 
   end subroutine sub
   #endif

To compile the code with ``method_1``, one way is to apply pre-processor
to each ``.f95`` and compile the files to ``.o`` file and link the two
``.o`` files into an executable bu the following commands.

.. code:: bash

   cpp -P -Ddouble_precision -Dmethod_1 pre_processor.f95 pre_processor.f90
   gfortran -c -O3 pre_processor.f90 -o pre_processor.o
   cpp -P -Ddouble_precision -Dmethod_1 sub.f95 sub.f90
   gfortran -c -O3 sub.f90 -o sub.o
   gfortran -O3 -o run pre_processor.o sub.o

What if we have many files in a project? Do we have to modify the
compile command every time a modification is made to the project? If you
use makefile, that would never happen.

In some aspect of view, Makefile is a way to assign rules to the compile
process. In this way, when you modify your project with the rule written
in makefile, you will not have to always modify the makefile.

**if you are new to makefile, I recommend not only to execute file, but
also see the popup scripts on screen and the new files generated by the
makefile**

First makefile
--------------

In the first makefile, the only rule is ``run`` and ``clean``, the
``run`` part is exactly to execute the command line one by one. and the
clean part will clean up all the pre processor files ``.f90``, objective
file ``.o`` and the executable ``run``.

``Makefile-1``

.. code:: makefile

   run:
     cpp -P -Ddouble_precision -Dmethod_1 pre_processor.f95 pre_processor.f90
     gfortran -c -O3 pre_processor.f90 -o pre_processor.o
     cpp -P -Ddouble_precision -Dmethod_1 sub.f95 sub.f90
     gfortran -c -O3 sub.f90 -o sub.o
     gfortran -O3 -o run pre_processor.o sub.o

   clean:
     rm pre_processor.f90
     rm pre_processor.o
     rm sub.f90
     rm sub.o
     rm run

To compile:

.. code:: bash

   make -f Makefile-1

to clean:

.. code:: bash

   make -f Makefile-1 clean

to run the code:

.. code:: bash

   ./run

Second makefile
---------------

Now, the execution part is the same as Makefile-1, the only difference
is some of the command becomes variable If you want to modify something,
such as compiler, optimization flag, pre-processor flag, you do not have
to modify all the way through the execution part.

If you look the the command windows, you will see the compiles command
in the command window is almost the same as it is for ``Makefile-1``
(except for one additional flag)

``Makefile-2``

.. code:: makefile

   EXEC = run # the name of the execution file
   FC = gfortran # the compiler, you can use intel, pgi, etc.
   FCOPT = -O3   # OPT flag for fortran compiler
   PP = cpp  # C pre-processor. cpp for GNU, fpp for intel

   # pre processor flags, only the correct flag will affect the code,
   #   the rest of the flags, either not exist in the fortran code, or
   #   null, will not affect the result of the pre-processor.
   CPPFLAG = -P $(FLAG_1) $(FLAG_2) $(FALG_3) $(FLAG_4)
   FLAG_1 = -Ddouble_precision
   FLAG_2 = -Danything_is_okay
   # FLAG_3 = -Dor_not_used
   FLAG_4 = -Dmethod_1

   $(EXEC):
     $(PP) $(CPPFLAG) $(FLAG_1) $(FLAG_2) $(FLAG_3) $(FLAG_4) pre_processor.f95 pre_processor.f90
     $(FC) -c $(FC_OPT) pre_processor.f90 -o pre_processor.o
     $(PP) $(CPPFLAG) $(FLAG_1) $(FLAG_2) $(FLAG_3) $(FLAG_4) -P -Ddouble_precision -Dmethod_1 sub.f95 sub.f90
     $(FC) -c $(FC_OPT) sub.f90 -o sub.o
     $(FC)  $(FC_OPT) -o $(EXEC) pre_processor.o sub.o

   clean:
     rm *.f90
     rm *.o
     rm $(EXEC)

To compile:

.. code:: bash

   make -f Makefile-2

to clean:

.. code:: bash

   make -f Makefile-2 clean

to run the code:

.. code:: bash

   ./run

Third makefile
--------------

``Makefile-2`` looks much better than ``Makefile-1``, but not enough.
What if we have 1000 .f95 files in a project? Here we have a rule for
all \*.95 to all \*.o

If you look the the command windows, you will see the compile command in
the command window is identical to the case of Makefile-2

``Makefile-3``

.. code:: makefile

   EXEC = run # the name of the execution file
   FC = gfortran # the compiler, you can use intel, pgi, etc.
   FCOPT = -O3   # OPT flag for fortran compiler
   PP = cpp  # C pre-processor. cpp for GNU, fpp for intel

   # pre processor flags, only the correct flag will affect the code,
   #   the rest of the flags, either not exist in the fortran code, or
   #   null, will not affect the result of the pre-processor.
   CPPFLAG = -P $(FLAG_1) $(FLAG_2) $(FALG_3) $(FLAG_4)
   FLAG_1 = -Ddouble_precision
   FLAG_2 = -Danything_is_okay
   # FLAG_3 = -Dor_not_used
   FLAG_4 = -Dmethod_1

   # if you know the dependency of the fortran file, you can simply
   #   list them in one line

   # rule for *.95 to *.o
   .SUFFIXES: .o .f90 .f95 
   SRCS = pre_processor.f95 sub.f95
   OBJS = $(SRCS:.f95=.o)
   .f95.o:
     $(PP) $(CPPFLAG) $*.f95 > $*.f90
     $(FC)  -c $(FFLAGS) $(INCS) $*.f90

   # after all .o is gathered, link and generate the executable
   $(EXEC): $(OBJS)
     $(FC)  $(FC_OPT) -o $(EXEC) $(OBJS)

   clean:
     rm *.f90
     rm *.o
     rm $(EXEC)

To compile:

.. code:: bash

   make -f Makefile-3

to clean:

.. code:: bash

   make -f Makefile-3 clean

For ``makefile-3`` you do not have to modify the ``$(EXEC)`` or
``.f95.o`` part, when anything change happens to the files in the
project, you only need to modify ``$(SRCS)``.

More about makefile
-------------------

Actually, the ``makefile-3`` is very similar to the old version in
``FUNWAVE-TVD``.

If you can compile some of your simple code with the above three
versions of makefile, you should be able to modify and used it for your
daily project.

But makefile can do much more for you. You can gradually modify your
makefile to make it better.
