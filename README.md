# Metasploit Offensive Security Arsenal

> "May the eyes of cowards never sleep." - Khalid bin Walid

This repository is a personal collection of scripts, custom modules, cheatsheets, and walkthroughs related to the Metasploit Framework. Maintained by **FarrosFR**, this repository aims to be a practical knowledge base for the world of offensive security and penetration testing.

<br>

<details>
<summary>⚠️ Important Disclaimer</summary>
<br>
All information, scripts, and techniques in this repository are intended ONLY FOR ETHICAL CYBERSECURITY EDUCATION AND RESEARCH PURPOSES. Using these tools and techniques to attack targets for which you do not have explicit permission is illegal. The author (FarrosFR) is not responsible for any misuse of the information within this repository. Use at your own risk and always act professionally and ethically.
</details>

---

## Table of Contents

1.  [About This Repository](#about-this-repository)
2.  [Directory Structure](#directory-structure)
3.  [Use Cases & Implementation Examples](#use-cases--implementation-examples)
    * [Resource Script: Automated Listener](#resource-script-automated-listener)
    * [Cheatsheet: Payloads](#cheatsheet-payloads)
    * [Walkthrough: MS17-010 (EternalBlue) Exploitation](#walkthrough-ms17-010-eternalblue-exploitation)
4.  [How to Use This Repository](#how-to-use-this-repository)
5.  [Contributing](#contributing)
6.  [License](#license)

---

## About This Repository

This repository serves as:
* **A Storage for Custom Modules**: To store custom `exploit`, `auxiliary`, or `post` modules that have been created or modified.
* **A Collection of Resource Scripts (.rc)**: To automate repetitive tasks in `msfconsole`.
* **A Hub for Cheatsheets**: A quick reference for essential commands, payloads, and techniques.
* **A Documentation of Walkthroughs**: Step-by-step notes from real-world pentesting scenarios or lab platforms like Hack The Box & TryHackMe.

## Directory Structure

```

/
├── custom\_modules/     \# For your custom Metasploit modules
├── resource\_scripts/   \# .rc scripts for msfconsole automation
├── cheatsheets/        \# Quick references (payloads, commands, etc.)
└── walkthroughs/       \# Step-by-step guides for specific scenarios

````

## Use Cases & Implementation Examples

Here are some practical examples found in this repository.

### Resource Script: Automated Listener

We often need to quickly set up a `multi/handler` listener. This `.rc` script automates it.

**File**: [`resource_scripts/multi_handler_listener.rc`](resource_scripts/multi_handler_listener.rc)

**Implementation**:
Run from your terminal (not inside msfconsole):
```bash
msfconsole -r resource_scripts/multi_handler_listener.rc
````

This will immediately start a listener with the predefined configuration from the file.

### Cheatsheet: Payloads

A quick reference for various common payloads used in Metasploit, categorized by the target operating system.

**File**: [`cheatsheets/payload_cheatsheet.md`](https://www.google.com/search?q=cheatsheets/payload_cheatsheet.md)

**Example Snippet**:
| Platform | Payload Type                      | Example                             |
| :---     | :---                              | :---                                |
| Windows  | Staged Reverse TCP (Meterpreter)  | `windows/meterpreter/reverse_tcp`   |
| Linux    | Stageless Reverse TCP (Shell)     | `linux/x64/shell_reverse_tcp`       |

### Walkthrough: MS17-010 (EternalBlue) Exploitation

A step-by-step guide to exploiting the MS17-010 vulnerability, one of the most famous vulnerabilities targeting the SMB protocol in Windows.

**File**: [`walkthroughs/case_ms17-010_eternalblue.md`](https://www.google.com/search?q=walkthroughs/case_ms17-010_eternalblue.md)

This walkthrough covers:

1.  Target identification.
2.  Selecting the exploit module in Metasploit.
3.  Configuring `RHOSTS`, `LHOST`, and `PAYLOAD`.
4.  Executing the exploit and gaining a Meterpreter session.

## How to Use This Repository

1.  **Clone the Repository**

    ```bash
    git clone [https://github.com/farrosfr/metasploit-arsenal.git](https://github.com/farrosfr/metasploit-arsenal.git)
    cd metasploit-arsenal
    ```

2.  **Adding Custom Modules**
    Copy your `.rb` module to the appropriate directory inside `custom_modules/`. Inside `msfconsole`, use the `loadpath` command to load it:

    ```
    msf > loadpath /path/to/your/repo/metasploit-arsenal/custom_modules
    msf > reload_all
    ```

## Contributing

Currently, this repository is maintained for personal use. However, if you find any errors or have suggestions, please open an *Issue*.

## License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE).
