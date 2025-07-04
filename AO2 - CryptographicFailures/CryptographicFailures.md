***
# AO2:2021 Cryptographic Failures

Cryptographic Failures occur when a cryptographic algorithm or a protocol is not implemented or configured correctly. This can lead to attackers accessing data such as passwords and credit card numbers. Poorly hashed passwords can be targets for brute force or dictionary attacks. Attackers often look for areas of weakness in cryptographic systems in order to access sensitive data. 

### Common Causes include:
- Storing passwords in plaintext
- Using a weak or an outdated hashing algorithm such as MD5 or SHA1
- Transmitting data over unencrypted connection
- Hardcoding cryptographic keys


For example, in 2019, Facebook accidentally revealed over 540 million records as they were cached on unsecured Amazon servers. These records should have been held in a secure private and definitely not a publicly available server.

### Mitigation:
- Ensure sensitive data is stored only if it's needed. Simply because if the data isn't there, it cannot be stolen
- Encrypt all data in transit
- Ensure that up to date and strong cryptographic algorithms are used. Keys for these algorithms should be managed securely.
- Outdated protocols should not be used. 
- Store password as hashes using strong hashing functions.

### Tools one could use to detect or exploit this vulnerability:
- Burp Suite
- Wireshark


### Challenge 2 Writeup:

I used Burp Suite for this challenge, so I could analyse the HTTP request and responses easier. I looked at the HTTP response for login.php, and I noticed that the developer left a note for themselves to store the database in a better place than /assets.

![Screenshot 2025-06-09 174930](https://github.com/user-attachments/assets/c315c2c8-0ede-458e-8d96-8c9690c22b06)


Then, I navigated to the assets folder by amending the URL, which allowed me to see the webapp.db file!
![Screenshot 2025-06-09 175234](https://github.com/user-attachments/assets/a73dad39-269e-4f68-b874-e8f2e34dcc3e)


After this, I downloaded the db file and used sqlite3 to print the table headings and the data held within the table. 


![Screenshot 2025-06-09 175809](https://github.com/user-attachments/assets/9c27e1f2-5046-4df3-b6e4-1fa2883edf29)


The table shows a password hash for the administrator account which I attempted to crack using hashcat.

6eea9b7ef19179a06954edd0f6c05ceb

This string looks like an MD5 hash as it is 32 characters long and the letters in this string are between A and F, indicating that it uses a hexadecimal format. 

I used the rockyou wordlist with the md5 setting within hashcat and the plaintext was revealed as "qwertyuiop". 

![Screenshot 2025-06-09 182445](https://github.com/user-attachments/assets/24e1c5b4-7af4-4510-8083-20dea94473de)



Finally, I used the username and password to login as admin which gave me the flag.

![Screenshot 2025-06-09 180705](https://github.com/user-attachments/assets/e44ec345-2c98-4293-8c76-34d3813d4ebe)

### Summary: 

This vulnerability highlights the importance of encryption for data that is being stored and data that is being transmitted. This challenge demonstrated a database that could be easily accessed. The database also contained the hash for the adminstrator password, which an attacker could exploit locally, avoiding detection. Without proper testing, this vulnerability is extremely dangerous. 

***
