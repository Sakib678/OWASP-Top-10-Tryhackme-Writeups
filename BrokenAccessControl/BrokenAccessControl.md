***
# AO1:2021 Broken Access Control 

Access Control is a security feature that can control which users are allowed to access certain features.  Access Control can be split into 4 types:

- Discretionary Access Control: The administrator or resource owner determines who is allowed to access a resource and what actions they are allowed to perform.
- Mandatory Access Control: Access is determined by a defined set of rules. Only those with a particular clearance can access certain areas. The rules are enforced by the system.
- Role Based Access Control: Users are assigned access levels based on the level of access needed for their job responsibilities. Typically used within an enterprise system. 
- Attribute Based Access Control: Access to resources is determined by attributes such as user role, time of day, location and device. 

Broken Access Control is a type of vulnerability where a user is able to access a resource or carry out an action that they shouldn't have access to. 
For example, in CVE-2025-48741, users are able to access log and alert files, even if the user does not have permission to do this, via a specific API endpoint. 

This type of vulnerability can be discovered by manipulating a URL to bypass access controls, which can allow an attacker to gain unauthorised access to privileged data. Improperly secured endpoints can be used to access or modify data using the access level of the endpoint.

### Mitigation:
 - Deny access by default unless it is a public resource
 - A user should be given the minimum level of access necessary for a user to perform their function
 - Regularly and comprehensively auditing access controls, analysing possible gaps in security that an attacker could exploit. 

### Tools one could use to exploit this:
- Burp Suite
- OWASP ZAP

### Challenge 1 Writeup:

This challenge is a Broken Access Control challenge focusing on IDOR (Insecure Direct Object Reference). This is where an attacker is able to access a resource indirectly via a broken access control.


![Screenshot 2025-06-09 172830](https://github.com/user-attachments/assets/14e6ea86-4c37-47cc-b734-5caebc799178)


The machine is a note server where users can view their own notes. The URL shows some promise here as there is a parameter being passed within the URL called "note_id=1". So by simply adjusting the id value, we can access other people's notes. 

By changing the id value to 0, it gives us the flag. 

![Screenshot 2025-06-09 173128](https://github.com/user-attachments/assets/89628994-e210-46c4-bf06-f936ad51d476)


### Summary:
This is a low risk attack, if access control is set correctly. If an account is breached, but it is an account with limited access, it limits the attacker, unless they are able to escalate privileges. It is essential to ensure that access levels are completely locked down. The impact of this attack is huge as if an attacker is able to escalate privileges vertically, after gaining initial access, it can lead to considerable data exfiltration. 
