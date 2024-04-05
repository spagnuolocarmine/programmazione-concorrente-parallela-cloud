# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 3 - MPI Point-to-Point Communication

**Develop an MPI program in C for the following problems:**

1. **_Ring_**: Given **P** processes, the process with rank *i* sends an integer value to the process with rank *i+1*. Note that the communication pattern is circular and toroidal, so the process with rank *P-1* sends to the process with rank *0*. The program execution involves 10 iterations. In each iteration, processes increment the value received from the left neighbor by a pseudo-random integer between 0-100. A particular iteration ends when the value received by a process exceeds a certain threshold *S* provided as input to the program. At the end of the 10 iterations, the program writes to standard output (rank 0) the average number of communication rounds needed to converge using *P* and *S*. Note that random number generators should not be reinitialized between iterations. It is recommended to initialize the generators using the rank value.
   
   ![ring.png](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/ring.png)

2. Calculate the maximum and minimum of arrays of integer values using *P* processes and blocking and non blocking communication operations.
3. Develop the Reduce functionality in the _mycollective_ library, capable of supporting the maximum and minimum operators of an array of integers.
4. Modify the _mycollective_ library to implement gather, scatter, broadcast, and reduce operations in non-blocking mode. Note that these operations involve multiple processes; therefore, the library should also provide a function to wait for an array of MPI_Request, utilizing the operations offered by MPI.

- *Furthermore, note that the rank values refer to the processes' indices obtained from the MPI_COMM_WORLD communicator.*
