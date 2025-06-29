# Custom Post-Exploitation Modules

This directory holds custom **Post-Exploitation** modules. These are the tools you use *after* a successful exploit has granted you a session on the target system.

> Post-exploitation is the phase of a penetration test where an attacker focuses on value. The goal is no longer just to gain access, but to extract sensitive information, expand influence within the network (lateral movement), and maintain control for future access (persistence).

### Purpose of This Directory

Store and categorize modules designed for specific post-exploitation tasks, such as:
- **Custom scripts** for enumerating unique environments or software.
- **Modified public modules** designed to evade logging and detection.
- **Specialized tools** for privilege escalation on patched or hardened systems.
- **Niche data exfiltration** scripts for non-standard data types.

### Common Post-Exploitation Objectives

Post-exploitation modules are built to achieve specific goals, including:

* **Privilege Escalation**: Gaining higher-level permissions (e.g., from `USER` to `NT AUTHORITY\SYSTEM` or `root`).
* **Situational Awareness**: Gathering detailed intelligence about the compromised host (e.g., running services, installed software, network configuration, user activity).
* **Credential Harvesting**: Dumping password hashes, Kerberos tickets, or searching for plaintext credentials stored on the system.
* **Lateral Movement**: Using the compromised host as a pivot point to attack other systems within the internal network.
* **Persistence**: Installing a mechanism (e.g., a backdoor or scheduled task) to ensure you can regain access even if the system is rebooted or the initial vulnerability is patched.
* **Data Exfiltration**: Identifying and stealing sensitive files and information.

### How to Use Modules in This Directory

Using a post-exploitation module requires an **active session**. The workflow is different from auxiliary or exploit modules.

1.  **Gain a Session**: First, successfully run an exploit to get a Meterpreter or shell session.
2.  **Background the Session**: Do not interact with the session directly. Instead, send it to the background.
    ```
    meterpreter > background
    [*] Backgrounding session 1...
    ```
3.  **Load and Use the Post Module**: Load your module as usual. The `loadpath` command should have already been run.
    ```
    msf6 > use post/windows/gather/checkvm
    ```
4.  **Set the Session ID**: The most critical step is to tell the module which session to run against.
    ```
    msf6 post(windows/gather/checkvm) > show options
    
    Module options (post/windows/gather/checkvm):

       Name     Current Setting  Required  Description
       ----     ---------------  --------  -----------
       SESSION                   yes       The session to run this module on.

    msf6 post(windows/gather/checkvm) > set SESSION 1
    SESSION => 1
    ```
5.  **Run the Module**:
    ```
    msf6 post(windows/gather/checkvm) > run
    ```

---

[<-- Back to Main README](../../README.md)
