# Custom Auxiliary Modules

This directory is the designated storage for custom **Auxiliary** modules for the Metasploit Framework.

> Auxiliary modules are used for a wide range of tasks that don't involve direct exploitation, such as scanning, reconnaissance, enumeration, fuzzing, and even Denial of Service (DoS). They are the primary tools for information gathering.

### Purpose of This Directory

The purpose of this space is to house and organize auxiliary modules that are:
* **Custom-built** for a specific reconnaissance task.
* **Modified** from existing modules to add new features or evade detection.
* **Obtained** from the security community but not yet integrated into the core Metasploit Framework.

### Common Use Cases for Custom Auxiliary Modules

- **Vulnerability Scanning**: Creating a scanner for a newly discovered or niche vulnerability that doesn't have an official exploit module yet.
- **Advanced Enumeration**: Writing a script to discover specific information from a service, like enumerating user lists, software versions, or misconfigured cloud buckets.
- **Information Gathering**: Automating the process of scraping specific data from a web application or API.
- **Fuzzing**: Developing a simple fuzzer to test for unexpected behavior in a network service or application input.

### How to Use Modules in This Directory

1.  **Place Your Module**: Add your custom auxiliary module file (e.g., `my_scanner.rb`) into this directory. For better organization, you can create subdirectories (e.g., `scanner/http/`).
2.  **Load the Path in `msfconsole`**: The most effective way is to load the parent `custom_modules` directory. This will load all custom auxiliary, exploit, and post modules at once.
    ```
    msf > loadpath /path/to/your/repo/metasploit-arsenal/custom_modules
    msf > reload_all
    ```
3.  **Use Your Module**: You can now search for and use your module like any other.
    ```
    msf > search my_scanner
    msf > use auxiliary/scanner/http/my_scanner
    msf > show options
    ```

---

[<-- Back to Main README](../../README.md)
