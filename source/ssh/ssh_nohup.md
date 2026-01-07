# SSH - nohup

[Introduction](#introduction)

[Usage](#usage)

---
## Introduction

`nohup` tell the process to ignore the **SIGHUP** signal
 which is sent by ssh session on termination, thus making the command persist
 even after session logout. On session logout the command is detched from
 controlling terminal and keeps on running in background as daemon process.

---
## Usage

`nohup` with running task at background was sent to background with prompt
 returning immediately giving **PID** and **job ID** of the process ([JOBID] PID).

**1\. run a program to background with `nohup`:**

```bash
nohup ping www.ami.com 1>/dev/null 2>&1 &
```
