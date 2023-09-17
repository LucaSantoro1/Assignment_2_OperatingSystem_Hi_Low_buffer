# Assignment_2_OperatingSystem_Hi_Low_buffer
Real Time Systems for Automation M, Assignment 2 (OS): hi-low buffer. Code + Report.A number of concurrent tasks cooperate in a producer-consumer fashion. The behaviour of these tasks is illustrated by the following pseudo-code: 

void producer(void) {
    FOREVER {
        value = produce();
        p = f(value);
        upload(value, p);
    }
}

void consumer() {
    determine threshold;
    FOREVER {
        value = download(threshold);
        consume(value);
    }
}

Producers not only produce integer values but also associate each integer they produce a parameter p, which can be either LOW or HIGH (naturally, LOW < HIGH). The tasks cooperate via a shared buffer having a fixed capacity of N slots (each slot can hold one integer), using two methods: upload and download. These methods work as follow:
void upload(value, p) copies value and p onto an empty slot in the buffer. If there are no empty slots, the calling task has to wait. If multiple tasks are waiting to upload, then upload requests with p equal to HIGH have the priority.
int download(t) is invoked with an argument t which, like p, could be either LOW or HIGH. It takes from the buffer a value whose associated p is greater than or equal to t, and returns the value to the caller, freeing the corresponding slot. If the buffer does not contain an integer with p >= t, then the calling task has to wait.
Analyze the problem. Design, implement and test a monitor that offers methods upload and download as described. Be sure to avoid deadlock as well as any race condition (in other words, the buffer must function correctly). Moreover, concurrency should be preserved: threads should proceed concurrently whenever possible and not block unnecessarily.

Submit your working source code as one or more .c/.h files, and your project as a single .pdf document. Alternatively, you can submit everything together as a single .zip bundle. Do not submit executable files. The project file should contain your design of the monitor, where you briefly explain the general idea behind your implementation. If you like you can add your considerations about anything you consider relevant and noteworthy.
