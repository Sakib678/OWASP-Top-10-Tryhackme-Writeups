# Cryptographic Failures:

I used Burp Suite for this challenge, so I could analyse the HTTP request and responses easier. I looked at the HTTP response for login.php, and the developer left a note for themselves to store the database in a better place than /assets.

* photo of burp response*

By navigating to the assets folder by amending the URL, we can see the webapp.db file! I then downloaded the file and used sqlite3 to print the table headings and the data held within the table. 

*photo of SQLtable*

The table shows a password hash for the administrator account which I'll attempt to crack using hashcat.

6eea9b7ef19179a06954edd0f6c05ceb

This string looks like an MD5 hash as it is 32 characters long and the letters in this string are between A and F. 

I passed hashcat the rockyou wordlist and got the result "qwertyuiop". 

*Insert photo of hashcat result*


I then used the username and password to login as admin which gave me the flag.

*Insert photo of flag result*
