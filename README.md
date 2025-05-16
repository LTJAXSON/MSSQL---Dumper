# MSSQL---Dumper
Features

     Column-based data extraction
    Automatically scans for sensitive data using common PII keywords like username, password, token, email, dob, and more.

     Custom column targeting with LIKE_SEARCH
    Target columns by name using your own comma-separated keywords:

-o LIKE_SEARCH=secret,auth,email

 Regex-powered value hunting with REGEX (python based)
Perform deep content inspection across all columns and tables, even if column names don't match anything:

-o REGEX='^\$2[aby]\$.{56}'       # Find bcrypt hashes
-o REGEX='\d{16}'                 # Match 16-digit credit card numbers

 Dual match logic

    Full row output when columns match PII or LIKE_SEARCH

    Targeted cell output when regex matches values (even in unknown columns)

     Example Usage

nxc mssql 192.168.1.100 -u sa -p 'Password123!' -M mssql_dumper  -o LIKE_SEARCH=apikey,auth \ -o REGEX='\d{4}-\d{4}-\d{4}-\d{4};(?i)bearer' -o SAVE=true

   `POC`
   ![image](https://github.com/user-attachments/assets/ca34c318-32e4-48e3-9039-21c73ff0053d)


  `Module Options`

1 - SEARCH       Semicolon-separated regex(es) to search for in **Cell Values**


2 - LIKE_SEARCH  Comma-separated list of column names to specifically look for


3 - SAVE         Save the output to sqlite database (default True)


  `Coming Next`
 Work in progress to enable data retrieval through linked servers expanding the attack surfce.

