2.sjf
#include <stdio.h>
#include <stdlib.h>
struct process
{
int pid;
int a_time;
int b_time;
int priority;
int w_time;
int turn_a_time;
};
int main()
{
struct process p[10];
int i, n;
printf("Enter the number of
processes (up to 10): ");
scanf("%d", &n);
for (i = 0; i < n; i++)
{
printf("\nEnter the PID: ");
scanf("%d", &p[i].pid);
printf("Enter the arrival time: ");
scanf("%d", &p[i].a_time);
printf("Enter the burst time: ");
scanf("%d", &p[i].b_time);
}
int total_waiting_time = 0;
int total_turnaround_time = 0;
int current_time = 0;
printf("\nProcess\tArrival Time\tBurst
Time\tWaiting Time\tTurnaround Time\n");
for (int i = 0; i < n; i++)

{
int waiting_time = current_time -
p[i].a_time;
if (waiting_time < 0)
{
waiting_time = 0;
current_time = p[i].a_time;
}
total_waiting_time += waiting_time;
int turnaround_time = waiting_time +
p[i].b_time;
total_turnaround_time +=
turnaround_time;
printf("%d\t\t%d\t\t%d\t\t%d\t\t%d\n",
p[i].pid, p[i].a_time,
p[i].b_time, waiting_time,
turnaround_time);
current_time += p[i].b_time;
}
float avg_waiting_time =
(float)total_waiting_time / n;
float avg_turnaround_time =
(float)total_turnaround_time / n;
printf("\nAverage Waiting Time:
%.2f\n", avg_waiting_time);
printf("Average Turnaround Time:
%.2f\n", avg_turnaround_time);
return 0;
}
