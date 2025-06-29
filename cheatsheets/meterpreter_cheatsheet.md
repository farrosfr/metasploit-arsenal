# Meterpreter Commands Cheatsheet

A quick reference for essential commands available within a Meterpreter session. These commands are used for post-exploitation after successfully gaining access to a target.

### Core & Channel Commands

| Command | Description |
| :--- | :--- |
| `?` / `help` | Displays the help menu listing all available commands. |
| `background` | Sends the current Meterpreter session to the background. |
| `sessions -i <id>`| Interacts with a backgrounded session by its ID. |
| `exit` / `quit` | Terminates the Meterpreter session. |

### File System Commands

| Command | Description |
| :--- | :--- |
| `ls` | Lists files and directories in the current remote directory. |
| `cd <directory>` | Changes the current remote directory. |
| `pwd` | Prints the current working directory on the remote machine. |
| `cat <file>` | Displays the contents of a remote file. |
| `download <file>`| Downloads a file from the target to your local machine. |
| `upload <file>` | Uploads a file from your local machine to the target. |
| `edit <file>` | Edits a remote file using your local `vim` editor. |
| `search -f <pattern>` | Searches for files on the target machine (e.g., `search -f *.pdf`). |

### System & Process Commands

| Command | Description |
| :--- | :--- |
| `sysinfo` | Displays system information about the target machine. |
| `getuid` | Shows the user that Meterpreter is running as. |
| `ps` | Lists all running processes on the target. |
| `kill <pid>` | Terminates a process on the target by its Process ID (PID). |
| `getpid` | Shows the PID of the current Meterpreter payload process. |
| `execute -f <cmd>` | Executes a command or application on the target. |
| `shell` | Drops you into a standard command shell on the target. |
| `reboot` / `shutdown`| Reboots or shuts down the remote machine. |

### Privilege Escalation & Credential Harvesting

| Command | Description |
| :--- | :--- |
| `getsystem` | Attempts to escalate privileges to the `NT AUTHORITY\SYSTEM` user on Windows. |
| `hashdump` | Dumps the password hashes from the SAM database on a Windows target. Requires SYSTEM privileges. |
| `load kiwi` | Loads the `kiwi` extension (a port of Mimikatz) for advanced credential theft on Windows. |

### Network Commands

| Command | Description |
| :--- | :--- |
| `ipconfig` / `ifconfig` | Displays network interface information on the target. |
| `route` | Shows the network routing table of the target. |
| `portfwd` | Forwards a local port to a remote port, allowing you to pivot into the target's network. |
