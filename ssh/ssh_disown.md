# SSH - disown

[Introduction](#introduction)

[Usage](#usage)

---

## Introduction

`disown`, removes the job from the process job list of the system,
 so the process is shielded from being killed during session disconnection as
 it won’t receive `SIGHUP` by the shell when you logout.

**Disadvantage:**

Used only for the jobs that do not need any input from the **stdin** and neither 
 need to write to **stdout**

>  try to interact with **stdin** or **stdout**, it will halt

---

## Usage

**1\. run a program to background**

```bash
ping www.ami.com -4 1>/dev/null 2>&1 &
```

Response *PID*:

```bash
[1] 48069
```

**2\. list running jobs:**

```bash
jobs -l
[1]+ 48069 Running                 ping www.ami.com -4 > /dev/null 2>&1 &
```

**3\. removes the job from the process job list of the system:**
  _pass disown signal to job_


```bash
disown -h %1
```

**4. exit ssh and re-login remote server**

```bash
exit
# reconnect
ssh name@hostname
```

**5. check the jobs list, the previous job is still running:**

```bash
ps -ef | grep ping
jun        48069    8998  0 21:11 pts/6    00:00:00 ping www.ami.com -4
jun        48071    8998  0 21:11 pts/6    00:00:00 grep --color=auto ping
```
