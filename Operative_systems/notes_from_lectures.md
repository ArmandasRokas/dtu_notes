## Lenktion 1

### Chapter 1

- putting layers of abstractions. 
- OS provide communication layer to hardware
- Volitile - reboot. data no longer there
- IR instruction fatched and ready to execute
- PSW information that is needed when program needs to be restored
- registers - is fast memory inside CPU
- hit - in which level of cache is received

### Chapter 2

- fd - integer value  (fd = open("filename.txt")) 
- offset - where you are in a file
- stdin stout first three fd is taken
- open/write/read is **system calls** 

```c
fd = open("filename.txt") // fd is integer value
    
read(fd, buff, 100)  // fd file descriptor
read(0, buff, 100)    // sdin 
write(1, buff, 100)   // 1 console
```

- ISA low level abstractions
- Linux multiple user can log in and do stuff.. Time sharing 
- **Process** is instance of program
- Scheduling - priotizing

```
shell <--> OS
```

- Program that runs another program remains the same PID
- execv is system call. That has no respect for original program that is called. That means lines after execv is not executed
- fork returns two values. Two differnt PIDs
- creates two processes
- if p == 0 after fork is the child
- after fork calls exec to change context of the program
- `wait` waits when child process terminates
- | pipe - input redirection

```c
while(1){
    write(1,'$');
    read commend (0, command, arg); // parse so become a command
    if(fork == 0){
        child exec
        
    } else{
        //parent
        wait(0)
    }
}
```

- fd array. fd[0] input   -------- fd[1] output

```c
fd[2] 
pipe(fdarray);
fork 
read
write
exec
```

- fork duplicates everyting it has
- pipe - established a pipe, where you can write and read
- start pipe in shell/ Write program creates a pipe
- input can be read from another fd
- when do fork create another similet with differnt PID and have access to the same pipe
- before doing exec . I am reading from parent process and writng to the child process
- and then execute exec



- if  fork 0 0 You are in child process
- if fork > 1 you are in parent process



`execvp`