# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 4 - MPI Non-blocking communication 

**Develop an MPI program in C for the following problems:**

1. **Ring 2**: Given *P* processors, develop an MPI program where each processor sends its rank to its right neighbor in the order defined by MPI_COMM_WORLD and receives from the left neighbor. The communication of the rank should occur in a non-blocking manner. Additionally, each process forwards the messages it receives from the left neighbor and sums all the values, including its own, into a variable. The process terminates when each process has received the rank of all others and writes the calculated sum to the standard output.

2. Develop the same program but utilizing different communication modes.

3. Evaluate the performance of the programs on an  MPI cluster varying the number of virtual instance from 2 to 16 nodes.

4. Execute and evaluate the performance of all programs developed in previous labs on the same cluster.


- *Furthermore, note that the rank values refer to the processes' indices obtained from the MPI_COMM_WORLD communicator.*


