# The-Hospital-Priority-Scheduling--Using-Non-Preemptive-and-Preemptive-Priority-Scheduling-Algorithms
The hospital scheduling system implemented in C uses priority scheduling (both
non-preemptive and preemptive) to manage patient treatment order efficiently.
The choice between the two scheduling methods depends on the hospital’s
requirements:
1. Non-Pre-emptive Priority Scheduling:

 Patients are treated in order of priority, and once a treatment
starts, it cannot be interrupted.
 This method ensures that a high-priority patient does not get
interrupted but may cause delays for critical patients arriving
later.

2. Pre-emptive Priority Scheduling:

 The system allows interruption if a patient with a higher
priority arrives or becomes available
 This ensures that the most critical patients get immediate

attention but may lead to longer waiting times for lower-
priority cases.

Key Observations:

 Waiting Time (WT) and Turnaround Time (TAT):
1. Preemptive scheduling usually results in lower
waiting times for high-priority patients but may
increase waiting times for lower-priority ones.
2. Non-pre-emptive scheduling ensures that once
a patient starts treatment, it is completed
without interruption
 Efficiency
1. Preemptive scheduling is better suited for
emergency cases where critical patients need
immediate attention.
2. Non-preemptive scheduling works well when
interruptions are not desirable, such as in surgical
procedures

Overall, this system effectively models real-world hospital scenarios where patient
priority determines scheduling, ensuring fair and efficient medical attention.
