# Notes on Operating Systems
From my OS course at GSW.

Deadlocks can arise if 4 conditions hold simultaneously.
1) Mutual exlusion: Only one proces at a time can use a resource.
2) Hold and wait: A process olding at least 1 other resource is waiting to acquire additional resources held by other processes.
3) No preemption: A resource can be released only voluntarily by the process holding it, after that process has completed its task (no forced stopping).
4) circular wait: process --> resource = request, resource --> process = allocation.

Bankers Algorithm

  n = number or processes
  m= resource types

Available[j] = n of availabe instances of j resource
Max[i][j] = max demand of process i for resource j
Allocation[i][j] = current allocation of resource j to process i
Need[i][j] = Remaining resource need of process i for resource j = M[i][j] - Allocation[i][j]

Step 1: Calculate need

1. Need[i][j] = Max[i][j - Allocation[i][j]
2. Need[i] <= Available
3. Available = Available + Allocation[i]
4. Repeat

Terms:
- kernel = the core of the OS; manages resources and proceses
- user space - where user applications and processes execute
- Power-On Self-Test (POST) = This is what happens first when the computer is turned on. It checks to see if all hardware components are functioning correclty before the operating system begins to load.
- Central Processing Unit (CPU) = The brain of the computer.
- Graphical User Interface (GUI) = Often called a "desktop environment."

POST --> hard disk/solid-state drive --> bootloader --> RAM

How are files loaded/opened? When you click on a file the OS allocates the necessary resources and then loads the program into memory, telling the CPU to start to executing.

| CPU | GPU |
| --- | --- |
| A few powerful cores | Thousands of smaller, efficient cores which creates high throughput|
| Sequential procesing | Parallel processing |
| RAM | VRAM |
| Diverse asks and operating systems | Visual calcluations, gaming, AI tasks |
