## Description
> A developer created a testing program that is continuously writing to a log file _/var/log/bad.log_ and filling up disk. You can check for example with tail -f /var/log/bad.log.  
> 
> This program is no longer needed. Find it and terminate it. Do not delete the log file.

## Solution
First, let's find out which process is writing to the log:
```bash
$ lsof /var/log/bad.log

output:
COMMAND   PID  USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
badlog.py 589 admin    3w   REG  259,1     5866 265802 /var/log/bad.log
```

The process we need is `badlog.py` with PID `589`.
So, we can kill it:
```bash
$ kill 589
```

***end.***