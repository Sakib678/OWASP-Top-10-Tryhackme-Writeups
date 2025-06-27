***
# AO4:2021 Insecure Design

This is a vulnerability related to how flaws in development can lead to vulnerabilities that an attacker can exploit. The idea of this type of vulnerability is that the application remains insecure to poor design.
Developers, quality auditors and the security teams should adhere to best design practices so that the vulnerabilities are not released with the product. 

For example, The Mirai Botnet was a combination of IoT devices that were maliciously controlled bots. These IoT devices had easy to guess default usernames and passwords, which allowed an attacker to control them. If they were securely designed, the users would have been required to change these credentials during the device setup. 

### Tools one could use to exploit this:
- Burp Suite
- OWASP Zap
- Postman
- 
### Challenge Writeup:

The website is a login page for a file server. We need to log into "josephs" account. As the password is unknown, we could try every possible combination, but this could take a while and we may be limited to a set number of attempts.
An easier method to try first is the password reset function. Once opening this, we enter the name of  the account and we are required to pick one security question and answer it. 
2 of the security questions could have a lot of answers, however answering "what is your favourite colour" is likely to be a set choice of options that we can try.
So by brute forcing this question using the different colours, we can try to see if one works.

![Screenshot 2025-06-16 155457](https://github.com/user-attachments/assets/664217db-cfb1-4b7c-afb1-619b9360b40d)

The colour "green" works and this resets the password and displays it on the screen for us. 

![Screenshot 2025-06-16 155421](https://github.com/user-attachments/assets/5a336f12-309e-4e75-8903-a90a5cdd2dd9)

We can then use this password to login to the interface. I then navigated to the private folder, and discovered the flag. 
![Screenshot 2025-06-16 230351](https://github.com/user-attachments/assets/2f8ed2c9-9e98-428b-b167-7f884b286a4f)



### Mitigation:
- Using a secure development lifecycle and secure coding practices
- Applying the defense in depth principle which establishes multiple layers of security
- Use the principle of least privilege
- Perform Threat Modelling 

### Summary:

Insecure design is not about a misconfiguration or a bug, it's about a flaw in logic, which can be even more difficult to fix. For this challenge, the password reset feature was exploitable as an easy security question could be answered. This highlights how poor design can allow an attacker in without exploiting vulnerabilities through more traditional methods. This reinforces the importance of ensuring that security is considered throughout every step of the software development lifecycle. 

***
