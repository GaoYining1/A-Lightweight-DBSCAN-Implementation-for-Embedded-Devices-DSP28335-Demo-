# A-Lightweight-DBSCAN-Implementation-for-Embedded-Devices-DSP28335-Demo-
This project is a lightweight implementation of the DBSCAN clustering algorithm for embedded devices, developed for the TI TMS320F28335 DSP chip. It successfully addresses the limitations of traditional DBSCAN algorithms, such as high memory consumption, complex computations, and poor adaptability to resource-constrained embedded scenarios.
The project has been fully verified through practical tests: it achieves fast clustering on 100 sets of ToF sensor data with no dynamic memory allocation, a core computation time of ≤500μs, and memory usage of ≤8KB.


**Hardware Environment**
Main Controller：TI TMS320F28335 (32-bit DSP)
Clock Frequency：150MHz
Minimum RAM： 64KB 
Minimum Flash： 256KB 
Communication Interface：UART (9600bps, 8N1)
Sensor Input：ToF distance data (1D float)

**Software Dependencies**
Compiler: TI Code Composer Studio (CCS) v9.3+
SDK: TI C2000Ware v3.4+
Dependent Library: rts2800_ml.lib (C2000 series runtime library)
Host Computer: Any serial assistant (for viewing clustering results)

**Quick Start**
1. Import the Project
Open CCS and click Project → Import CCS Projects;
Select the DSP28335_DBSCAN_Demo folder in the repository directory and import the project;
Verify the SDK path configuration (Project → Properties → C2000Ware Path points to the local C2000Ware installation directory).

2. Compile and Download
Click Project → Build Project. Compilation completes without warnings/errors (expected compilation time ≤30 seconds);
Connect the DSP development board to the computer and select the corresponding emulator (e.g., XDS100v3);
Click Run → Debug to download the program to the development board.

3. View Results
Open a serial assistant (Baud rate: 9600, Data bits: 8, Stop bits: 1, Parity: None);
After powering on the development board, the serial port will output:
Initialization information (DBSCAN parameters, data volume);
Clustering results (number of clusters, number of outliers, members of each cluster);
Performance data (core computation time).

**Usage Instructions**
1. Adjust DBSCAN Parameters
   
Modify the macro definitions in main.c to adapt to your data scenario:

#define EPS 0.2f        // Neighborhood radius (adjust based on data distribution, e.g., ToF unit: mm)

#define MIN_PTS 3       // Minimum number of points to form a core point

#define MAX_CLUSTERS 5  // Maximum number of supported clusters (avoids memory overflow)

2. Replace Input Data
Modify the data[100] array in main.c with your sensor data (1D float):

const float data[100] = {408.3697, 408.5345, 408.5214, ..., 408.3213  // Your data (100 sets total)};

**Serial Output**
DBSCAN Demo

EPS=0.2, MinPts=3

Cluster 1: 408.3697, 408.5345, 408.5214, ...

Cluster 2: 406.1382, 406.0065, 406.088, ... 

Noise：410.9800, ... 

Time:333.9149us

Calculate Done!


**Contribution & Communication**
We welcome contributions and communications through the following channels:

Submit Issues: Report bugs or propose optimization suggestions;

Initiate Pull Requests: Submit code optimizations or new feature implementations;

Email Communication: gaoyining777216@gmail.com (subject: "DBSCAN-Embedded Discussion").


























