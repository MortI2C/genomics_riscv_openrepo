# Genomics RISC-V Open-data Repository

This is a repository of results obtained experimenting with Epistasis genomics workload on RISC-V architectures.
The current repository will be moved into a proper web-site with tools to properly visualize the data gathered. However, for now, we provide the results as txt files with the output of the workload for the several cases we examined so far.

The results are in the results folders. Each batch folder consists of a repetition of the experiments, so we can consider statistics such as standard deviation.
Naming convention for the files is:
mdr_f[0-9]_n[0-9]_c[0-9].log

Which has the following meaning:
* MDR is the current version of the Epistasis method implemented.
* f indicates the number of files evaluated for scalability tests. The more files, the more parts of the genome have been sequenced and evaluated. The files are scaled in such a way that even with lower numbers it makes sense to compare with x86 architectures where we can have very large number of files.
* n indicates the number of nodes used. The master node is always on a separate node. Therefore, n indicates the number of worker nodes used.
* c is the number of cores used. The amount is, naturally, limited by the platform.

We additionally upload a .tar.gz with the current implementation of Epistasis, already prepared to run on RISC-V with the following requirements:
* Singularity must be present
* Java must be installed. We built Java 11 ZeroVM, however Java 19 JDK is the latest OpenJDK java version and has been ported to RISC-V as well. At the time of running the experiments JDK19 was not yet available on its final release so we built JVM based on the ZeroVM release.
* Apache Spark must be set and compiled. It compiles with no major complication provided maven and javac are installed on the system.
* Python must be installed. PySpark is used on the Epistasis as a python library linkin with the Spark runtime, which relies on Java. 
