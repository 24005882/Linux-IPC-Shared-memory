# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## Write a C program that illustrates two processes communicating using shared memory.

    #include <stdio.h>
    #include <sys/ipc.h>
    #include <sys/shm.h>
    
    int main()
    {
    	// Generate a unique key using ftok
    	key_t key = ftok("shmfile", 65);
    
    	// Get an identifier for the shared memory segment using shmget
    	int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
          printf("Shared memory id = %d \n",shmid);
    // Attach to the shared memory segment using shmat
    	char* str = (char*)shmat(shmid, (void*)0, 0);
    	
        printf("Write Data : ");
    	fgets(str, 1024, stdin);
    
    	printf("Data written in memory: %s\n", str);
    
    	// Detach from the shared memory segment using shmdt
    	shmdt(str);
    
    	return 0;
    }

 

## OUTPUT

![371405490-d4bc6ce8-7de7-41ca-8465-c874e52e129d](https://github.com/user-attachments/assets/baf91c1a-9dd1-4407-8386-3a2a9fd7e1c3)



# RESULT:
The program is executed successfully.
