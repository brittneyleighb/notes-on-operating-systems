# Operating Systems Study Notes

Short notes from my GSW operating-systems coursework. This is a living study document, not a complete technical reference; terminology and examples will be expanded as I review the material.

## Deadlock

A deadlock is possible only when all four Coffman conditions hold at the same time:

1. **Mutual exclusion:** at least one resource can be used by only one process at a time.
2. **Hold and wait:** a process holding one or more resources waits for additional resources.
3. **No preemption:** the operating system cannot forcibly take a resource away; its holder releases it voluntarily.
4. **Circular wait:** processes form a cycle, where each waits for a resource held by the next.

Break any one condition and that particular deadlock cannot occur.

## Banker's algorithm

Banker’s algorithm asks whether granting a request would leave the system in a **safe state**.

| Symbol | Meaning |
| --- | --- |
| `n` | Number of processes |
| `m` | Number of resource types |
| `Available[j]` | Available instances of resource type `j` |
| `Max[i][j]` | Maximum declared demand of process `i` for resource type `j` |
| `Allocation[i][j]` | Instances of resource type `j` currently allocated to process `i` |
| `Need[i][j]` | Remaining demand: `Max[i][j] - Allocation[i][j]` |

### Safety check, in plain steps

1. Calculate `Need = Max - Allocation`.
2. Set `Work = Available`; mark every process unfinished.
3. Find an unfinished process whose `Need` is less than or equal to `Work`.
4. Pretend that process completes and releases its allocation: `Work = Work + Allocation`.
5. Mark it finished and repeat.
6. If every process can finish, the state is safe. If none of the unfinished processes can proceed, it is unsafe.

## Core terms

- **Kernel:** the privileged core of an operating system; it manages hardware access, processes, memory, files, and protection.
- **User space:** where ordinary applications run with limited privileges.
- **POST:** firmware's power-on self-test, which checks hardware during startup.
- **CPU:** executes instructions and coordinates computation.
- **GUI:** graphical user interface, often provided by a desktop environment rather than the operating system kernel itself.

## Simplified boot path

`Power on → firmware/POST → select boot device → bootloader → kernel → user-space services and desktop/login`

The exact path differs across BIOS, UEFI, operating systems, and boot configurations.

## Opening a file versus launching a program

Opening a document asks an application to read file data. Launching a program asks the loader and OS to create a process, map the executable and required libraries into memory, establish its initial state, then schedule it to run on the CPU.

## CPU and GPU

| CPU | GPU |
| --- | --- |
| Fewer, general-purpose cores optimized for low-latency and branching work | Many simpler cores optimized for high-throughput parallel work |
| Uses system RAM | Often has dedicated VRAM; integrated GPUs may share system memory |
| Runs operating-system and application control code | Accelerates graphics and suitable parallel workloads |

## Next study topics

- Process states, context switches, and scheduling
- Paging, virtual memory, and page replacement
- Synchronization, race conditions, and semaphores
- File systems and storage
- System calls, interrupts, and device I/O
