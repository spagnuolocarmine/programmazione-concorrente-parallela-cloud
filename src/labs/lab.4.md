# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 3 - MPI Point-to-Point Communication

**Develop an MPI program in C for the following problems, using only the MPI_Send and MPI_Recv operations:**

1. Exchange of an integer value between two MPI processes.
2. Sending a string (read from stdin) from the process with rank **0** to the process with rank **1**.
3. Given **P** MPI processes and an array of integer values with length **N**, perform the following operations:
    - *Broadcasting*, the process with rank **0** sends to all processes **1..P-1**;
    - *Gathering*, the process with rank **0** receives an integer value from all processes **1**...**P-1**;
    - *Scatter*, the process with rank **0** sends a portion of the array to each process in **1**...**P-1**.
4. Starting from the previous point, generalize the programs to obtain a library *mycollective*. There are no constraints on the function signatures and/or computational requirements.
5. Evaluate the performance of the implemented library in sending the data types **MPI_Int** and **MPI_Char**, calculating the execution times on a single machine varying the size of **N** and the number of MPI processes.

- How to calculate the execution time?


```c 
/*................*/
double start, end;
MPI_Init(&argc, &argv);
MPI_Comm_rank(MPI_COMM_WORLD, &rank);
MPI_Barrier(MPI_COMM_WORLD); /* tutti i processi sono inizializzati */
start = MPI_Wtime();
/*----------------*/
/*................*/
/*codice programma*/
/*................*/
/*----------------*/
MPI_Barrier(MPI_COMM_WORLD); /* tutti i processi hanno terminato */
end = MPI_Wtime();
MPI_Finalize();
if (rank == 0) { /* Master node scrive su stdout il tempo o su file */
    printf("Time in ms = %f\n", end-start);
}
/*................*/
```

- *Note that the rank values refer to the processes' indices obtained from the MPI_COMM_WORLD communicator.*