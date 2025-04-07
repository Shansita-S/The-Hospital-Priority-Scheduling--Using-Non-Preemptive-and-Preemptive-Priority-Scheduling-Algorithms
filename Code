#include <stdio.h>
#include <string.h>
struct Patient {
    char name[20];
    int at, tt, priority, ct, tat, wt, remaining_tt;
};
// Swap function for sorting
void swap(struct Patient *a, struct Patient *b) {
    struct Patient temp = *a;
    *a = *b;
    *b = temp;
}
// Non-Preemptive Priority Scheduling
void nonPreemptive(struct Patient patients[], int n) {
    int time = 0;
    // Sorting by arrival time, then by priority
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (patients[i].at > patients[j].at || 
               (patients[i].at == patients[j].at && patients[i].priority > patients[j].priority)) {
                swap(&patients[i], &patients[j]);
            }
        }
    }
    // Process patients
    for (int i = 0; i < n; i++) {
        if (time < patients[i].at)
            time = patients[i].at;
        time += patients[i].tt;
        patients[i].ct = time;
        patients[i].tat = patients[i].ct - patients[i].at;
        patients[i].wt = patients[i].tat - patients[i].tt;
    }
}
// Preemptive Priority Scheduling (Fixed)
void preemptive(struct Patient patients[], int n) {
    int time = 0, completed = 0, minIndex;
    // Copy treatment time to remaining_tt
    for (int i = 0; i < n; i++) 
        patients[i].remaining_tt = patients[i].tt;

    while (completed < n) {
        minIndex = -1;
        for (int i = 0; i < n; i++) {
            if (patients[i].at <= time && patients[i].remaining_tt > 0) {
                if (minIndex == -1 || patients[i].priority < patients[minIndex].priority)
                    minIndex = i;
            }
        }

        if (minIndex == -1) {
            time++;
            continue;
        }

        patients[minIndex].remaining_tt--;
        time++;

        if (patients[minIndex].remaining_tt == 0) {
            completed++;
            patients[minIndex].ct = time;
            patients[minIndex].tat = patients[minIndex].ct - patients[minIndex].at;
            patients[minIndex].wt = patients[minIndex].tat - patients[minIndex].tt;
        }
    }
}
// Display function
void display(struct Patient patients[], int n) {
    printf("\nName\tAT\tTT\tPriority\tCT\tTAT\tWT\n");
    for (int i = 0; i < n; i++) {
        printf("%s\t%d\t%d\t%d\t\t%d\t%d\t%d\n", 
               patients[i].name, patients[i].at, patients[i].tt, 
               patients[i].priority, patients[i].ct, 
               patients[i].tat, patients[i].wt);
    }
}
// Main function
int main() {
    int n, choice;
    struct Patient patients[10];
    printf("Enter the number of patients: ");
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        printf("Enter Name, Arrival Time, Treatment Time, Priority for Patient %d: ", i + 1);
        scanf("%s %d %d %d", patients[i].name, &patients[i].at, &patients[i].tt, &patients[i].priority);
    }
    printf("Select Scheduling Type:\n1. Non-Preemptive Hospital Scheduling\n2. Preemptive Hospital Scheduling\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    if (choice == 1) {
        nonPreemptive(patients, n);
        printf("\nNon-Preemptive Hospital Scheduling\n");
    } else {
        preemptive(patients, n);
        printf("\nPreemptive Hospital Scheduling\n");
    }
    display(patients, n);
    return 0;
}
