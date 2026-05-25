# Linux DevOps Lab 12: Process Management
## Project Title
Process Management in Linux (DevOps Fundamentals)

## Project Overview

This lab demonstrates fundamental Linux process management skills used in DevOps and system administration. It covers how to start, monitor, prioritize, and terminate processes using essential Linux commands.

The exercise simulates real-world server management tasks such as handling background services, tracking system processes, and controlling resource usage.

## Objective

To understand and practice how to:

- Start processes in the background
- Monitor running processes
- Identify process IDs (PIDs)
- Terminate processes
- View system performance
- Adjust process priority using Linux tools

## Tools & Environment
- Operating System: Ubuntu (WSL on Windows 11)
- Shell: Bash
- Commands Used:
- sleep
- ps
- grep
- jobs
- kill
- top
- nice
- renice
## Step-by-Step Process
### 1. Start a Background Process

A long-running process was started in the background using:
```
sleep 300 &
```
Output:
```
[1] 1856
```
Explanation:
- sleep 300 → process runs for 300 seconds
- & → runs process in background
- 1856 → Process ID (PID)

<img width="1240" height="162" alt="image" src="https://github.com/user-attachments/assets/8ed53c6e-e4fa-48df-a09f-aa273c80d1cf" />

## 2. View Running Jobs
```
jobs
``` 
Output:
```
[1]+  Running  sleep 300 &
```
Explanation:
- Confirms that the process is running in the background
- [1] is the job ID

<img width="1160" height="84" alt="image" src="https://github.com/user-attachments/assets/391efd2e-1165-4172-9e30-58c59e5ca890" />

## 3. Identify Process Using ps
```
ps aux | grep sleep
```
Output:
```
1856  sleep 300
1876  grep sleep
```
Explanation:
- Shows active processes
- PID 1856 belongs to the sleep process
- Second line is the grep command itself

<img width="1226" height="226" alt="image" src="https://github.com/user-attachments/assets/5c18d975-8249-4607-82bb-02950b7641d9" />

## 4. Terminate the Process
```
kill 1856
```
Output:
```
[1]+ Terminated sleep 300
```
Explanation:
- kill stops a process using its PID
- Process successfully terminated

<img width="1204" height="76" alt="image" src="https://github.com/user-attachments/assets/5cbabf40-1868-401f-bd6c-d9f8b8d66161" />

## 5. Confirm Process Termination
```
jobs
```
Output:

(No output)
```
ps aux | grep sleep
```
Output:
```
grep sleep
```
Explanation:
- No active sleep process remains
- Only search command is visible

<img width="1244" height="226" alt="image" src="https://github.com/user-attachments/assets/b0c85a5c-adee-470a-acf2-736166c37ed9" />

## 6. Monitor System Processes
```
top
```
Explanation:
- Displays real-time system processes
- Shows CPU, memory usage, and running tasks
- Useful for performance monitoring

Exit with:
```
q
```

<img width="1242" height="1408" alt="image" src="https://github.com/user-attachments/assets/7bb46961-f9a8-4036-ae72-fa8997f85f36" />

## 7. Process Priority Management
Start process with lower priority:
```
nice -n 10 sleep 300 &
```
Change priority of running process:
```
renice -n 5 -p <PID>
```
Explanation:
- nice → starts process with defined priority
- renice → changes priority of existing process
- Lower value = higher priority

<img width="1232" height="120" alt="image" src="https://github.com/user-attachments/assets/41bcd20e-a260-46e4-a0bf-f7a112a9edb5" />

## Summary of Commands
#### Task	                                  Command
- Start background process	              sleep 300 &
- View jobs	                              jobs
- List processes	                        ps aux
- Find process	                          `ps aux
- Kill process	                          kill PID
- Monitor system	                        top
- Start low priority process	            nice -n 10 command &
- Change priority	                        renice -n value -p PID

## Key Learnings
- Linux processes can run in foreground or background
- Every process has a unique PID
- Processes can be monitored and controlled using system commands
- System resources can be analyzed in real time using top
- Process priority affects CPU scheduling behavior

## Conclusion

This lab successfully demonstrated Linux process management techniques essential for DevOps and system administration. The ability to control processes, monitor system performance, and adjust priorities is critical for managing production servers efficiently.
