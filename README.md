# pso-lib-cop
Library implementing the particle swarm optimization (PSO) metaheuristic for solving continuous optimisation problems (COP).


This library is available in three versions: in the first version, the PSO metaheuristic is implemented sequentially, the two remaining versions are improved for parallel computation, using OpenMP/MPI frameworks.

## Compilation

To compile the project normally, there is nothing special to do. You can make changes in main.cpp depending on the type of execution (Parallel OMP, MPI, or sequential) you want.


To do classical tests (CUTE without code coverage) :  
1. Comment the hand located in the file "main.cpp".  
2. Uncomment the hand located in "Tests.cpp".  

To do coverage tests with gcov, the following options must be added :  
1. In "GCC C++ Compiler/Debugging": add "-coverage" and check "Generate gcov information".  
2. In "GCC C++ Link

## OMP Parallel Project Setup
To run the project in parallel, you must:  
1. Remove all parameters related to coverage tests  
2. "GCC C++ Compiler/Optimization", add O2 in the scrollbar

## MPI Parallel Project Settings

To run the project in parallel with OMP, you need:  
1. Remove all parameters related to coverage tests  
2. "GCC C++ Compiler/Optimization", put O0 in the scrollbar
3. In "GCC C++ Compiler/Includes", add "/usr/lib/openmpi/include".
4. In "GCC C++ Compiler/Miscellaneous" add "-Wno-long-long", and remove "-Weffc++".
5. In "GCC C++ Linker", change "Command" to "mpiCC" instead of "g++" and the option to "-fopenmp".
  
## Customize execution settings

To change the different coefficients, go to "Essaim.h" (they will also be changed for EssaimOMP.h and EssaimMPI.h). These have an impact on how efficient the calculation of the speed is.

For a function with a lot of local minima, the following coeffcients are advised:  

	C1=1.0 and C2=2.0 OR generally speaking, a C2 more important than C1.  
	In one case with more global minima :  
	C1=2.0 and C2=2.0  

In the main.cpp you can modify :  
- The number of particles at the creation of the swarm  
- The number of dimensions at the creation of the swarm  
- The number of iterations when calling algoEssaim  


In Objectif.h  
- You can choose which function to execute in the "()" operator. The library comes with a selection functions which can be used to for functions global minimum approximation: sphere function, sum squares function, Rastrigin function, Rosenbrock function, Trid function.
- WARNING: you must choose the search space corresponding to the function chosen in the Objectif constructor.  

## Important note:

The file "joe-kuo-other-4.5600.txt" provided at the root of the project, MUST be put in the same folder as the executable, otherwise the execution will not work.  

