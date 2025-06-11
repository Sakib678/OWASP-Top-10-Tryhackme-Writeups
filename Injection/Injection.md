# AO3:2021 Injection
This type of vulnerability can be exploited when users are entering data that is processed by the application, and the data is not sanitised and validated correctly. 
Hostile data is used to try to trick the form into outputting additional records, that should not be displayed.

### Common injections include:
- SQL Injection
- NoSQL Injection
- LDAP Injection
- Command Injection

For example, the Equifax breach in 2017 was a major attack where attackers entered malicious SQL queries and they extracted confidential customer information

### Mitigation:

- Ensure all inputs are sanitised, validated and filtered before using them.
- Regularly test the application's user input fields and forms in order to find weaknesses.
- Use the principles of least access and zero trust to restrict users.

### Tools to detect this vulnerability:
- SQLMap: This is an automated tool for detecting potential areas for SQL Injection
- Burp Suite: For injecting payloads

### Challenge Writeup:

### Summary:
