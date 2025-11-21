# EX 1C Job Sequencing using Greedy Approach
## DATE: 01-11-2025
## Aim:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm
1. Read the number of jobs and their details (jobId, deadline, profit).
2. Sort all jobs in descending order of profit.
3. Find the maximum deadline among all jobs.
4. Create a boolean array to represent available time slots.
5. For each job (in sorted order), try to schedule it at the latest possible free slot before its deadline.
6. If the slot is free, schedule the job and update the total profit and number of jobs done.
7. Print the number of jobs completed and the total profit earned. 

## Program:
```txt
Program to implement Reverse a String
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151
```
```java
import java.util.*;
public class JobScheduling {

    static class Job {
        int id, deadline, profit;
        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

        int maxDeadline = 0;
        for (Job job : jobs)
            maxDeadline = Math.max(maxDeadline, job.deadline);

        boolean[] slot = new boolean[maxDeadline + 1];
        int jobCount = 0, maxProfit = 0;

        for (Job job : jobs) {
            for (int j = Math.min(maxDeadline, job.deadline); j > 0; j--) {
                if (!slot[j]) {
                    slot[j] = true;
                    jobCount++;
                    maxProfit += job.profit;
                    break;
                }
            }
        }
        return new int[]{jobCount, maxProfit};
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Job[] jobs = new Job[n];
        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }
        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}
```
## Output:
<img width="236" height="344" alt="image" src="https://github.com/user-attachments/assets/55b08570-7713-4a50-b493-3205bca97560" />

## Result:
The program successfully implemented and the expected output is verified.
