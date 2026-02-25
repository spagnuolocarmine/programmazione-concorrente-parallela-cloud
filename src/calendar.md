
# Programmazione Concorrente, Parallela e su Cloud
## Course Calendar

📜 LEGEND
- Part 🅰️
  - 📗 [MPI: A Message-Passing Interface Standard 2.2](https://www.mpi-forum.org/docs/mpi-2.2/mpi22-report.pdf)
  - ⚙️ [HAVE FUN WITH MPI](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/lets-start-to-have-fun-with-mpi)
  - 📘 [Introduction to Parallel Computing, Czech, Z., 2017](https://books.google.it/books?id=obDDDQAAQBAJ&printsec=copyright&redir_esc=y#v=onepage&q&f=false)
- Part 🅱️
  - 📕 [The Art of Multiprocessor Programming, Revised Reprint, Maurice Herlihy](https://cs.ipm.ac.ir/asoc2016/Resources/Theartofmulticore.pdf)
    - [Errata for The Art of Multiprocessor Programming](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/errata_tamp_.pdf)
- **Symbols**
  - 📒 Lesson
  - ⚗️ Lab
  
|#️⃣ |🗓️| Lesson | Type | Part| Materials | References | Assignments |
|---|--|-----------|------|-----|-----------|------------|--------------|
|1️⃣| 26/02/2026|Course introduction and parallel computing fundamentals|📒 | 🅰️🅱️| [vim graphical cheat sheet](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/vi-vim-cheat-sheet-dvorak.gif) | 📹 [Mythbusters Demo GPU versus CPU](https://www.youtube.com/watch?v=8_ZTvG1WQxM) <br> About 🐧 OS <br>📒 [An Introduction to Linux ](https://cvw.cac.cornell.edu/Linux/) <br>📺 [Linux Tutorial for Beginners: Introduction to Linux Operating System](https://www.youtube.com/watch?v=V1y-mbWM3B8)  <br>📑 [Introduction to Linux, Boston University](https://www.bu.edu/tech/files/2018/05/2018-Summer-Tutorial-Intro-to-Linux.pdf)| 🧑🏻‍🚀 activate Google GCP. You will receive a pdf with instruction on your studenti.unisa.it email. BEFORE beginning of June, 1 2026.|
|2️⃣ |27/02/2026|Introduction to HPC Cloud and GCP|📒 | 🅰️ | [Intro2GCP](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/1.gcp_an_inaction_introdution.pdf) | | |
<!--|3️⃣ |06/03/2025|Model and Architecture for Parallel Computing|📒⚗️ | 🅰️ | [shell-tools](https://missing.csail.mit.edu/2020/shell-tools/) [ssh-essentials](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys) | 📘 Cap. 2 (2.1, 2.2 with no demonstration) | [lab.2 - GCP](labs/lab.2.md)|
|4️⃣ |07/03/2025|Metrics for parallel computing|📒 | 🅰️ | [IntroDocker](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/docker-introduction_in-depth-material.pdf) | 📘 Cap. 3 (3.1, 3.2 with no demonstration) <br> 🐳  Docker resource: <br> - [Docker beginner lab](https://github.com/docker/labs/tree/master/beginner/) <br> - [Get Docker](https://docs.docker.com/get-docker/) <br> - [Documentation](https://docs.docker.com/reference/) (in-depth material) <br> - [gcloud Docker](https://cloud.google.com/sdk/docs/downloads-docker?hl=it) <br> |  |
|5️⃣ |13/03/2025|Design of parallel algorithms|📒 | 🅰️ | | 📘 Cap. 4 (4.1, 4.2, 4.3, 4.4 with no demonstration) <br> [OpenMPI](https://www.open-mpi.org/) <br> 🐳  [Docker Ubuntu OpenMPI](https://hub.docker.com/r/spagnuolocarmine/docker-mpi) <br> 🆚  [code Docker MPI integration](https://gist.github.com/spagnuolocarmine/60a5f8c065f9577c25a6717681bd84d1) <br> 🆘  [Usage Docker environment](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/docker-mpi-environment) <br> [Install OpneMPI](https://edu.itp.phys.ethz.ch/hs12/programming_techniques/openmpi.pdf)| [hello_world_mpi.c](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/hello_world_mpi.c) |
|6️⃣ |14/03/2025|Introduction to Message Passing Interface (MPI)|📒 | 🅰️ | |[MPI: A Message-Passing Interface Standard Version 3.1](https://www.mpi-forum.org/docs/mpi-3.1/mpi31-report.pdf)<br> [📖 Have fun with MPI in C:](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/lets-start-to-have-fun-with-mpi) <br> [- 📌 Chapter 1 - Introduction](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/lets-start-to-have-fun-with-mpi) |  |
|7️⃣|20/03/2025| MPI - Synchronous Communication|📒⚗️ | 🅰️ | [Find the bug 1](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/mpi_bug1.c)  | 📖 Have fun with MPI in C: <br> - 📌 [Chapter 2.1 - MPI Memory Model](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/mpi-memory-model)<br> - 📌 [Chapter 2.2 - Blocking Communication](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/blocking-communication)  <br>- 📌 [Chapter 2.3 - Communication Modes](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/communication-modes) | |
|8️⃣|21/03/2025| Lab Message Passing Interface (MPI)|⚗️ | 🅰️ | | [🔗 MPI on Cloud VM cluster](https://github.com/spagnuolocarmine/ubuntu-openmpi-openmp) |[lab.3 - MPI.1](labs/lab.3.md)[lab.4 - MPI.2](labs/lab.4.md) |
| 9️⃣ |27/03/2025| MPI - Asynchronous Communication|📒⚗️ | 🅰️ | [Find the bug 2](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/mpi_bug2.c) | 📖 Have fun with MPI in C <br> - 📌 [Chapter 2.4 - Non-Blocking Communication](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/non-blocking-communication) | [lab.5 - MPI.3](labs/lab.5.md)|
| 1️⃣0️⃣ |28/03/2025|MPI - Noncontiguous Data, Derived Datatypes - Collective Communication |📒 |🅰️||📖 Have fun with MPI in C<br>[- 📌 Chapter 3.1 - Communicate Noncontiguous Data](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/communicate-noncontiguous-data)<br>[- 📌 Chapter 3.2 - Derived Datatypes](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/derived-datatypes)<br>[-📌 Chapter 3 - Collective Communication](https://tech.io/playgrounds/47058/have-fun-with-mpi-in-c/collective-communications-overview)<br>[ 📓 mpi-derived-datatypes.pdf](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/mpi-derived-datatypes.pdf)| |
 1️⃣1️⃣ |03/04/2024|MPI Labs - Noncontiguous Data, Derived Datatypes - Collective Communication |⚗️| 🅰️|[mpi_latency.c](https://github.com/spagnuolocarmine/programmazione-concorrente-parallela-cloud/raw/main/data/mpi_latency.c) | | [lab.6 - MPI.4](labs/lab.6.md)<br>[lab.7 - MPI.5](labs/lab.7.md)|
| 1️⃣2️⃣|04/04/2024|Introduction to concurrency|📒|🅱️| | 📕 Cap. 1, Appendice B | |
| 1️⃣3️⃣ |10/04/2025|Mutual exclusion 1 |📒|🅱️| |📕 Cap. 2 (2.1->2.6)| |
| 1️⃣4️⃣ |11/04/2025|[Scalability Research Forum](forums/2024/crf-2024.md)|⚗️|🅰️|||[lab.8 - MPI.6](labs/lab.8.md)|
| 1️⃣5️⃣ |24/04/2025|Mutual exclusion 2 |📒|🅱️| |📕 Cap. 2 (2.7->2.8) | |
| 1️⃣6️⃣ |08/05/2025|Concurrent Objects |📒|🅱️| Fix [Double-Checking Locking](https://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html) |📕 Cap. 3 ||
| 1️⃣7️⃣ |09/05/2025|Monitor|📒|🅱️||Cap. 8||
| 1️⃣8️⃣ |15/05/2025|Spin Locks |📒|🅱️| |📕 Cap. 7  ||
| 1️⃣9️⃣ |16/05/2025|Lists |📒|🅱️| |📕 Cap. 9 | |
| 2️⃣0️⃣ |22/05/2025|Queues |📒|🅱️||📕 Cap. 10 | |
| 2️⃣1️⃣ |23/05/2025|Lab MPI + Q&A Presentazioni Scalability Research Forum  |⚗️|🅰️🅱️||| |
| 2️⃣2️⃣|29/05/2025 (4 ore)|[Scalability Research Forum 1️⃣](forums/2025/crf-2025.md)||||||
| 2️⃣3️⃣ |30/05/2025 (4 ore)|[Scalability Research Forum 2️⃣](forums/2025/crf-2025.md)||||||
-->
