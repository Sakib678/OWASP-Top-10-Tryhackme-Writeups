***
### AO4:2021 Insecure Design

This is a vulnerability related to how flaws in development can lead to vulnerabilities that an attacker can exploit. The idea of this type of vulnerability is tha the application remains insecure to poor design.
Developers, quality auditors and the security teams should adhere to best design practices so that the vulnerabilities are not released with the product. 

For example, an application may not limit the number of login attempts needed, which would make it vulnerable to a brute force attack. 

# Tools one could use to exploit this:

# Challenge Writeup:

The website is a login page for a file server. We need to log into "josephs" account. As the password is unknown, we could try every possible combination, but this could take a while and we may be limited.
An easier method to try first is the password reset function. Once opening this, we enter the name of  the account and we are rquired to pick one security question and answer it. 
2 of the security questions could have a lot of answers, however answering "what is your favourite colour" is likely to be a set choice of options that we can try.
So by brute forcing this question using the different colours, we can try to see if one works. The colour "green" works and this resets the password and displays it on the screen for us. 
We can then use this password to login to the interface, which gives us the flag. 

# Mitigation:
- Using a secure development lifecycle and secure coding practices
- Applying the defense in depth principle which establishes multiple layers of security

# Summary:

***
