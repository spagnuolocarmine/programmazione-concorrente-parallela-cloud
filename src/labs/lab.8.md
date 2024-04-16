# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 6 - MPI putting all together

**Develop an MPI program in C for the following problems:**

### Game of Life 

The Game of Life, also known simply as Life, is a cellular automaton devised by the British mathematician John Horton Conway in 1970.

The "game" is a zero-player game, meaning that its evolution is determined by its initial state, requiring no further input. One interacts with the Game of Life by creating an initial configuration and observing how it evolves, or, for advanced "players," by creating patterns with particular properties.

![](https://upload.wikimedia.org/wikipedia/commons/e/e5/Gospers_glider_gun.gif)

The universe of the Game of Life is an infinite two-dimensional orthogonal grid of square cells, each of which is in one of two possible states, alive or dead, or "populated" or "unpopulated." We can suppose to use a matrix of char, which marks if the cell is alive or dead.

Every cell interacts with its eight neighbors, which are the cells that are horizontally, vertically, or diagonally adjacent. At each step in time, the following transitions occur:

- Any live cell with fewer than **2** live neighbors dies as if caused by underpopulation.
- Any live cell with **2** or **3** live neighbors lives on to the next generation.
- Any live cell with more than **3** live neighbors dies, as if by overpopulation.
- Any dead cell with exactly **3** live neighbors becomes a live cell, as if by reproduction.

The initial pattern constitutes the seed of the system. The first generation is created by applying the above rules simultaneously to every cell in the seed—births and deaths occur simultaneously, and the discrete moment at which this happens is sometimes called a tick (in other words, each generation is a pure function of the preceding one). The rules continue to be applied repeatedly to create further generations.

🗒️ The program must be able to simulate the process for a particular number of steps I. The MASTER process initializes a char matrix at random and split among P-1 processors. Notice that the MASTER can contribute to the computation or not; it is your choice. Each slave simulates the game and sends the corresponding ghost cells to its neighbor's processors, need in for the next simulation step. The hard part of the problem concerns equally divide the matrix among processors, which can be done in different ways. Your program must work on any matrix size (N!=M) and a number of processes.

### N-body

In the N-body problem, we need to find the positions and velocities of a collection of interacting particles over some time. For example, an astrophysicist might want to know the positions and velocities of a group of stars. In contrast, a chemist might want to know the positions and velocities of a collection of molecules or atoms.

![](https://mir-s3-cdn-cf.behance.net/project_modules/disp/b15a1122638879.56315fcc653b5.gif)

An n-body solver is a program that finds the solution to an n-body problem by simulating the behavior of the particles. The input to the problem is the mass, position, and velocity of each particle at the start of the simulation, and the output is typically the position and velocity of each particle at a sequence of user-specified times, or merely the position and velocity of each particle at the end of a user-specified time.

Problem details are also available [here](https://en.wikipedia.org/wiki/N-body_simulation).

👉 NOTES. Consider only the solution that is quadratic in the number of particles; however, also the Barnes-Hut algorithm can be considered but should be harder to develop. For the mathematical part (bodies force computation) of the problem, follow the guidelines of this solution:

<details>
  <summary>Show code</summary>

```c
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include "timer.h"

#define SOFTENING 1e-9f

typedef struct { float x, y, z, vx, vy, vz; } Body;

void randomizeBodies(float *data, int n) {
  for (int i = 0; i < n; i++) {
    data[i] = 2.0f * (rand() / (float)RAND_MAX) - 1.0f;
  }
}

void bodyForce(Body *p, float dt, int n) {
  for (int i = 0; i < n; i++) { 
    float Fx = 0.0f; float Fy = 0.0f; float Fz = 0.0f;

    for (int j = 0; j < n; j++) {
      float dx = p[j].x - p[i].x;
      float dy = p[j].y - p[i].y;
      float dz = p[j].z - p[i].z;
      float distSqr = dx*dx + dy*dy + dz*dz + SOFTENING;
      float invDist = 1.0f / sqrtf(distSqr);
      float invDist3 = invDist * invDist * invDist;

      Fx += dx * invDist3; Fy += dy * invDist3; Fz += dz * invDist3;
    }

    p[i].vx += dt*Fx; p[i].vy += dt*Fy; p[i].vz += dt*Fz;
  }
}

int main(const int argc, const char** argv) {
  
  int nBodies = 30000;
  if (argc > 1) nBodies = atoi(argv[1]);

  const float dt = 0.01f; // time step
  const int nIters = 10;  // simulation iterations

  int bytes = nBodies*sizeof(Body);
  float *buf = (float*)malloc(bytes);
  Body *p = (Body*)buf;

  randomizeBodies(buf, 6*nBodies); // Init pos / vel data

  double totalTime = 0.0;

  for (int iter = 1; iter <= nIters; iter++) {
    StartTimer();

    bodyForce(p, dt, nBodies); // compute interbody forces

    for (int i = 0 ; i < nBodies; i++) { // integrate position
      p[i].x += p[i].vx*dt;
      p[i].y += p[i].vy*dt;
      p[i].z += p[i].vz*dt;
    }

    const double tElapsed = GetTimer() / 1000.0;
    if (iter > 1) { // First iter is warm up
      totalTime += tElapsed; 
    }
#ifndef SHMOO
    printf("Iteration %d: %.3f seconds\n", iter, tElapsed);
#endif
  }
  double avgTime = totalTime / (double)(nIters-1); 

#ifdef SHMOO
  printf("%d, %0.3f\n", nBodies, 1e-9 * nBodies * nBodies / avgTime);
#else
  printf("Average rate for iterations 2 through %d: %.3f +- %.3f steps per second.\n",
         nIters, rate);
  printf("%d Bodies: average %0.3f Billion Interactions / second\n", nBodies, 1e-9 * nBodies * nBodies / avgTime);
#endif
  free(buf);
}
```
</details>


### Word Count

The word count is the number of words in a document or passage of text. Word counting may be needed when a text is required to stay within specific numbers of words. This may particularly be the case in academia, legal proceedings, journalism, and advertising.


<img src="https://i.redd.it/86j6offa3iby.gif" height="300" border="0">


Word count is commonly used by translators to determine the price of a translation job. Word counts may also be used to calculate measures of readability and to measure typing and reading speeds (usually in words per minute). When converting character counts to words, a measure of 5 or 6 characters to a word is generally used for English

We will be doing a version of map-reduce using MPI to perform word counting over a large number of files


💡 There are three steps for this process:

- the MASTER node reads the file list (or a directory), which will contain the names of all the files that are to be counted. Note that only 1 of your processes should read the files list. Then each of the processes should receive their portion of the files from the MASTER process. Once a process has received its list of files to process, it should then read in each of the files and perform a word counting, keeping track of the frequency each word found in the files occurs. We will call the histogram produced the local histogram. This is similar to the map stage or map-reduce.
- the second phase is combining the frequencies of words across processes. For example, the word 'cat' might be counted in multiple processes, and we need to add up all these occurrences. This is similar to the reduced stage of map-reduce.
- the last phase is to have each of the processes send their local histograms to the master process. The MASTER process just needs to gather up all this information. Note that there will be duplicate words between processes. The master should create a CSV formatted file with the words and frequencies ordered.

👉🏻 **NOTES.** The hard part of the problem concerns splitting the computation among the processors. For instance, if we split the files between processors, we cannot have a good partitioning scheme because some files must be bigger and bigger than other files. A good partitioning scheme must consider the number of words in each file, and split according to this value.

