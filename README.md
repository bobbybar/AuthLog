# AuthLog

These computer log files include: attempted logins to the machine from other machines, logins from the same machine, running commands as another user (typically root) via the sudo command, and adding users. Monitoring attempted, successful and failed login attempts helps understand potential attacks on the machine. Understanding what is being done via sudo commands and by whom helps monitor changes to the system.

## Data:
The MergedAuth.log consists of 5 different log files that we will analyze. Most lines of the log file consist of a similar structure with the date-time, logging host(usually IP), app\[PID\], and message.

## Goals:
Our first task is to create a data frame with the following columns: date-time, the name of the host, the application, the process ID (PID), the message, and the name of the log file from which it came from. If there is no app for the corresponding line, NA will replace it.

Next, we will validate the data in the data frame and start to explore the information it contains. <br>
- Verify that the PIDs are all numbers.<br>
- How many lines are in each log file?<br>
- What are the range of date-times for the messages? for each of the different log files in the combined file? How many days does each log file span?<br>
- Do the application names contain numbers? If so, are they just versions, e.g. ssh2, or is there additional structure to the numbers?<br>
- Is the host value constant/the same for all records in each log file?<br>
- What are the most common apps (daemons/programs) that are logging information on each of the different hosts?<br>

As we explore, we will notice that there are valid and invalid login attempts from users. Here are some questions we will answer:<br>
- Find valid/successful logins<br>
  - What are the user names and Internet Protocol (IP) addresses of those logins?<br>
- Find the invalid user login/ids<br>
  - What were the associated IPs?<br>
  - Were there multiple invalid user logins from the same IP addresses – Were there valid logins from those IP addresses?<br>
  - Are there multiple IPs using the same invalid login?<br>
    - Are these related IPs, e.g., from the same network/domain?<br>
- What IP address had too many authentication failures?<br>

Lastly, we will explore the Sudo commands:<br>
- What are the executables/programs run via sudo?<br>
  - By what user?<br>
  - What machine are they on?<br>

