Compiling Trap on Windows with Intel Fortran
======

Several steps are needed to get Trap to work on Windows with the Intel Fortran Compiler.
- Install the Windows Cluster Computing SDK which has an MPI implementation
- Install the lp_solve executable (see lpsolve.sourceforge.net) and add the location the the Path environmental variable
- In the Visual Studio project properties:
	* Under Configuration Properties -> Debugging set Command to 'mpiexec.exe'
	* Under Configuration Properties -> Debugging set Command Arguments to ' -n 4 $(TargetPath)'
	* Under Configuration Properties -> Fortran -> General set Additional Include Directories to 'C:\Program Files\Microsoft Compute Cluster Pack\Include'
	* Under Configuration Properties -> Fortran -> Preprocessor set Preprocess Source File to 'Yes (/fpp)'
	* Under Configuration Properties -> Linker -> General set Additional Library Directories to 'C:\Program Files\Microsoft Compute Cluster Pack\Lib\i386'
	* Under Configuration Properties -> Linker -> Input set Additional Dependencies to 'msmpi.lib'
	* Under Configuration Properties -> Build Events -> Pre-Build Event set Command Line to 'copy TrapDef.dat Debug/TrapDef.dat' for the Debug Configuration
- Right click on the Source Files directory and Add -> Existing Item... and browse to 'C:\Program Files\Microsoft Compute Cluster Pack\Include' and select the 'mpi.f90' file