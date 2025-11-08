# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
### ex2_1.c
```c
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

int main() {
    pid_t pid;
    pid = fork();

    if (pid < 0) {
        printf("Fork failed.\n");
        return 1;
    }
    else if (pid == 0) {
        printf("Child Process:\n");
        printf("My PID: %d\n", getpid());
        printf("Parent PID: %d\n", getppid());
    }
    else {
        printf("Parent Process:\n");
        printf("My PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
    }

    return 0;
}
```
## OUTPUT

<img width="939" height="257" alt="Screenshot 2025-11-08 124740" src="https://github.com/user-attachments/assets/6e8d7cd7-2671-41f1-b10e-7092a39f1345" />

## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
### ex2_2.c
```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t pid;
    pid = fork();

    if (pid < 0) {
        printf("Fork failed.\n");
        return 1;
    }
    else if (pid == 0) {
        printf("Child process executing 'ls -l' command...\n");
        execl("/bin/ls", "ls", "-l", NULL);
        printf("execl() failed.\n"); // Only executes if exec fails
    }
    else {
        wait(NULL);
        printf("Child process finished execution.\n");
        printf("Parent process exiting.\n");
    }

    return 0;
}
```
## OUTPUT
<img width="946" height="302" alt="image" src="https://github.com/user-attachments/assets/a2caa4b7-dd3a-4b51-bcd9-8a9377d27bf1" />


# RESULT:
The programs are executed successfully.
