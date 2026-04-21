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

## C Code

```c
#include <stdio.h>

int main()
{
    int n, tq, i, time = 0, done = 0;
    int bt[20], at[20], rt[20], wt[20], tat[20], ft[20];
    int visited[20] = {0};

    float avg_wt = 0, avg_tat = 0;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    printf("Enter time quantum: ");
    scanf("%d", &tq);

    for(i = 0; i < n; i++)
    {
        printf("P%d Arrival Time: ", i + 1);
        scanf("%d", &at[i]);

        printf("P%d Burst Time: ", i + 1);
        scanf("%d", &bt[i]);

        rt[i] = bt[i];
    }

    while(done < n)
    {
        int executed = 0;

        for(i = 0; i < n; i++)
        {
            if(at[i] <= time && rt[i] > 0)
            {
                if(rt[i] > tq)
                {
                    time += tq;
                    rt[i] -= tq;
                }
                else
                {
                    time += rt[i];
                    ft[i] = time;
                    tat[i] = ft[i] - at[i];
                    wt[i] = tat[i] - bt[i];
                    rt[i] = 0;

                    avg_wt += wt[i];
                    avg_tat += tat[i];

                    done++;
                }
                executed = 1;
            }
        }

        if(executed == 0)
        {
            time++;
        }
    }

    printf("\nProcess\tAT\tBT\tFT\tTAT\tWT\n");

    for(i = 0; i < n; i++)
    {
        printf("P%d\t%d\t%d\t%d\t%d\t%d\n", i + 1, at[i], bt[i], ft[i], tat[i], wt[i]);
    }

    printf("\nAverage Waiting Time = %.2f", avg_wt / n);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat / n);

    return 0;
}
```

## How to Run

```bash
gcc rr.c -o rr
./rr
```
