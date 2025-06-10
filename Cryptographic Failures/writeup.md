# Cryptographic Failures:

I used Burp Suite for this challenge, so I could analyse the HTTP request and responses easier. I looked at the HTTP response for login.php, and the developer left a note for themselves to store the database in a better place than /assets.

![Screenshot 2025-06-09 174930](https://github.com/user-attachments/assets/c315c2c8-0ede-458e-8d96-8c9690c22b06)


By navigating to the assets folder by amending the URL, we can see the webapp.db file!
![Screenshot 2025-06-09 175234](https://github.com/user-attachments/assets/a73dad39-269e-4f68-b874-e8f2e34dcc3e)


I then downloaded the file and used sqlite3 to print the table headings and the data held within the table. 


![Screenshot 2025-06-09 175809](https://github.com/user-attachments/assets/9c27e1f2-5046-4df3-b6e4-1fa2883edf29)


The table shows a password hash for the administrator account which I'll attempt to crack using hashcat.

6eea9b7ef19179a06954edd0f6c05ceb

This string looks like an MD5 hash as it is 32 characters long and the letters in this string are between A and F. 

I passed hashcat the rockyou wordlist and got the result "qwertyuiop". 

![Screenshot 2025-06-09 182445](https://github.com/user-attachments/assets/24e1c5b4-7af4-4510-8083-20dea94473de)



I then used the username and password to login as admin which gave me the flag.

![Screenshot 2025-06-09 180705](https://github.com/user-attachments/assets/e44ec345-2c98-4293-8c76-34d3813d4ebe)

