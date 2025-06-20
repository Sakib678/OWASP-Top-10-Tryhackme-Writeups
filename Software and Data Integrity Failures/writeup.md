***
# AO8:2021 Software and Data Integrity Failures

The integrity of data is about ensuring that the data has not been modified. Keeping important data safe from attackers is essential. Hashes are very useful to prove that the data has kept its integrity.

A modern application is typically built using libraries from official sources and some unknown repositories. If a repository is compromised, it can allow an attacker to introduce malicious files or code into the software cycle, allowing them to run malicious programs on the application server. 

One of the most infamous examples of this type of attack is the SolarWinds supply chain attack. Attackers infiltrated the development process and inserted malicious code into a software update for a trusted tool, which was then distributed to thousands of organisations. This gave the attackers access to critical systems. 



### Challenge Writeup:

This challenge involves looking at Data Integrity Failures and exploiting a vulnerability present on libraries that support JWT. 

First we need to login to the guest account. When attempting a login, the password for the guest account is revealed to us. 

However, we are met with an error.

![image](https://github.com/user-attachments/assets/119924a5-f555-4727-986c-2124e1afacf6)

As we have a successful login, we have a JWT cookied stored in our browser. We should be able to edit the cookie by viewing the developer tools. 

![image](https://github.com/user-attachments/assets/03557aee-2276-4af3-bb62-2b8631454fcf)

The JWT token is held in base64, we can try to decode this and edit it to access an admin account. 

The token is split into 3 parts - the header, the payload and the signature. We are disregarding the signature to bypass the signature validation. 
The first "." indicates the end of the header and the second "." indicates the end of the payload" so by removing everything after the second ".", we can remove the signature too.
![image](https://github.com/user-attachments/assets/507dec0e-3dc9-4b70-acd6-e623b5bf71a8)

We then need to change the username from 'guest' to 'admin'. And the alg type from 'HS256' to 'none'.

![image](https://github.com/user-attachments/assets/b30d0feb-3acd-47aa-ae89-a7ef62055bd0)

Then we can just encode the header and the payload seperately. And combine them both by putting the full stops back where they should go, and making it into one string. 

Then we should paste the combined string back into the value field, which should give us access to the admin account and the flag!


![image](https://github.com/user-attachments/assets/dd4ec306-9610-4c6a-b2ed-e4d31d35d862)


### Mitigation:

- Use hash validation to detect tampering
- Monitor and test software to ensure the intended behaviour is occurring to find and remediate any security vulnerabilities. 
- Reduce trust in unverified sources and ensure that strong validation is applied throughout the software delivery cycle. 

### Summary:

This challenge demonstrated how a weak JWT implementation lead to a data failure and a serious breach of integrity. 
This type of vulnerabiltiy often stems from trusting external libraries without seeking proper validation. It is important to ensure that all tokens are validated, insecure configurations are avoided 
and there is a strict zero trust policy with all third party code.

***
