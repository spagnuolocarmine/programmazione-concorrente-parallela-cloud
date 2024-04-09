# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 5 - MPI Collective communication

**Develop an MPI program in C for the following problems:**

1. **Broadcasting**: Develop an MPI program utilizing *P* processors, where the process with rank 0 in MPI_COMM_WORLD broadcasts an array of doubles to all other processes in MPI_COMM_WORLD.

2. **Scattering**: Develop an MPI program utilizing *P* processors, where the process with rank 0 in MPI_COMM_WORLD scatters an array of doubles among all processes in MPI_COMM_WORLD.

3. **Gathering**: Develop an MPI program utilizing *P* processors, where the process with rank 0 in MPI_COMM_WORLD gathers a set of double values distributed among all processes in MPI_COMM_WORLD.

4. Evaluate the performance of the previous programs in handling large-sized arrays of doubles relative to the number of available processors.

5. Implement points 1, 2, and 3 using the _mycollective_ library and assess the performance compared to MPI collective operations.

6. Evaluate the performance of all previously developed programs on an MPI cluster composed of 8 nodes.

7. Develop an MPI program that, given an array *A* of integers of length *N*, evenly utilizes *P* processors to update the values in *A*. Each element *A[i]* is calculated using the following operation:
   - *A[i] = A[i-1] + A[i] + A[i+1]*, for each *i*, 1...*N*-2
   - *A[0] = A[N-1] + A[0] + A[1]*, for *i=0*
   - *A[N-1] = A[N-2] + A[N-1] + A[0]*, for *i=N-1*
   The array *A* is initialized in the master process, and the slaves perform operations only on their portion of the array. Each slave process sends its portion of the array back to the master; upon receiving all portions, the master process writes the execution time to standard output.

8. Develop an MPI program that, given a matrix of size *NxM* and *P* processes, calculates the maximum for each row of the matrix using *P* processes fairly. Upon completion, the master process writes the maximum of each row to standard output.

9. Repeat the previous point by calculating the minimum for each column.

10. Combine points 8 and 9 into a single program.


- *Furthermore, note that the rank values refer to the processes' indices obtained from the MPI_COMM_WORLD communicator.*
