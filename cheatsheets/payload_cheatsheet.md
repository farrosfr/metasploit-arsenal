# Metasploit Payload Cheatsheet

A quick reference for commonly used payloads.

## Windows Payloads

| Payload Type | Example Path | Description |
| :--- | :--- | :--- |
| **Staged Meterpreter (TCP)** | `windows/meterpreter/reverse_tcp` | A small payload (stager) that downloads the rest of the Meterpreter payload. Very commonly used. |
| **Stageless Meterpreter (TCP)** | `windows/meterpreter_reverse_tcp` | Sends the entire Meterpreter payload in a single connection. Larger in size, but more stable. |
| **Staged Meterpreter (HTTPS)** | `windows/meterpreter/reverse_https` | Same as reverse\_tcp, but the communication is wrapped in SSL/TLS. Good for evading IDS/IPS detection. |
| **Stageless Shell (TCP)** | `windows/shell_reverse_tcp` | Provides a standard command prompt (cmd.exe). Stageless. |

## Linux Payloads

| Payload Type | Example Path | Description |
| :--- | :--- | :--- |
| **Staged Meterpreter (TCP, 64-bit)** | `linux/x64/meterpreter/reverse_tcp` | Meterpreter stager for 64-bit Linux systems. |
| **Stageless Meterpreter (TCP, 64-bit)** | `linux/x64/meterpreter_reverse_tcp` | The stageless version of the payload above. |
| **Stageless Shell (TCP, 64-bit)** | `linux/x64/shell_reverse_tcp` | Provides a /bin/bash or /bin/sh shell on a 64-bit system. |
| **Python Shell (Generic)** | `python/meterpreter_reverse_http` | A Python-based payload, very useful if the target has Python installed. |

## Web / Scripting Payloads

| Payload Type | Example Path | Description |
| :--- | :--- | :--- |
| **PHP Meterpreter (Staged)** | `php/meterpreter/reverse_tcp` | A payload to be executed on a web server running PHP. |
| **Java JSP Meterpreter (Staged)** | `java/jsp_shell_reverse_tcp` | Provides a shell via a JSP page uploaded to a Java server (Tomcat, etc.). |
| **NodeJS Shell (Stageless)** | `nodejs/shell_reverse_tcp` | A reverse shell for NodeJS-based applications. |
