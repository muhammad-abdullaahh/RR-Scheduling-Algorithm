# Round Robin (RR) CPU Scheduling - C Implementation

This project implements the Round Robin CPU Scheduling algorithm in C language with arrival time support.

## Features
- Supports Arrival Time
- Uses Time Quantum
- Handles CPU idle time
- Calculates:
  - Finish Time (FT)
  - Turnaround Time (TAT)
  - Waiting Time (WT)
- Computes average WT and TAT

## Input
- Number of processes
- Arrival time for each process
- Burst time for each process
- Time Quantum

## Output
- Process table with AT, BT, FT, TAT, WT
- Average Waiting Time
- Average Turnaround Time

---

## How to Run

```bash
gcc rr.c -o rr
./rr
```
