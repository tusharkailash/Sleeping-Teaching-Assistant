# Sleeping-Teaching-Assistant


# Sleeping Teaching Assistant #
A Classical Inter-process Communication and Synchronization problem in Operating Systems


From the description of the problem we implement two threads -
 
1. studentsThread() - which can either get tutored or will leave the office if there is no free chair
2. teachingAssistantThread() - which can either tutor students or go to sleep

The TA has three actions. To check for a student, sleep if no one's waiting and wake up when a student arrives, we run a wait() operation on the student semaphore. When a student arrives, the TA starts tutoring her, and then there is one less student in the waiting room. After the tutoring, the TA checks for a student and the cycle repeats.

The student also has three actions but, unlike the TA, the student only performs her actions once.
When a student arrives, she checks to see if there's a chair available in the waiting room. If there isn't, the student leaves. Otherwise the student waits, and the number of students in the waiting room increases. To wake up the sleeping TA, the student runs an post() on the students semaphore, and then a wait() on the TA semaphore, waiting to be tutored.
The modification of the number of chairs is protected using mutex lock and unlock mechanisms.
