// Create a folder in d drive and copy path
>cd path
>git init
>touch .txt
>git add path
>git clone url
>git commit -m "first commit"
>git remote add origin git_repository_path
>git push -u origin master
>git pull origin master
>git fetch --all
>git branch
>git branch a1
>git branch -d a1   (delete a branch)
>git checkout -b m1
>git fetch --all
git --force origin main

import java.util.Scanner;

public class FCFS {
    
    static class Process {
        int id, arrivalTime, burstTime, waitingTime, turnaroundTime;
        
        Process(int id, int arrivalTime, int burstTime) {
            this.id = id;
            this.arrivalTime = arrivalTime;
            this.burstTime = burstTime;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the number of processes: ");
        int n = sc.nextInt();
        
        Process[] processes = new Process[n];
        
        for (int i = 0; i < n; i++) {
            System.out.print("Enter arrival time and burst time for process " + (i + 1) + ": ");
            int arrivalTime = sc.nextInt();
            int burstTime = sc.nextInt();
            processes[i] = new Process(i + 1, arrivalTime, burstTime);
        }

        // Sort processes by arrival time
        java.util.Arrays.sort(processes, (p1, p2) -> p1.arrivalTime - p2.arrivalTime);

        int currentTime = 0;
        
        for (Process p : processes) {
            if (currentTime < p.arrivalTime) {
                currentTime = p.arrivalTime;
            }
            p.waitingTime = currentTime - p.arrivalTime;
            p.turnaroundTime = p.waitingTime + p.burstTime;
            currentTime += p.burstTime;
        }

        System.out.println("\nProcess ID | Arrival Time | Burst Time | Waiting Time | Turnaround Time");
        for (Process p : processes) {
            System.out.printf("%9d | %12d | %9d | %12d | %15d%n", p.id, p.arrivalTime, p.burstTime, p.waitingTime, p.turnaroundTime);
        }

        sc.close();
    }
}


