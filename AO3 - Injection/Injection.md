# AO3:2021 Injection
This type of vulnerability can be exploited when users are entering data that is processed by the application, and the data is not sanitised and validated correctly. 
Hostile data is used to try to trick the form into outputting additional records, that should not be displayed.

### Common injections include:
- SQL Injection - When user input is passed to an SQL query. An attacker could pass in an SQL query, which could cause an unintended outcome
- Command Injection - When user input is passed to system commands, An attacker can pass in a command which can manipulate the server's system, potentially returning sensitive data

For example, the Equifax breach in 2017 was a major attack where attackers entered malicious SQL queries and they extracted confidential customer information

### Mitigation:

- Ensure all inputs are sanitised, validated and filtered before using them.
- Regularly test the application's user input fields and forms in order to find weaknesses.
- Use the principles of least access and zero trust to restrict users.

### Tools to detect this vulnerability:
- SQLMap: This is an automated tool for detecting potential areas for SQL Injection
- Burp Suite: For injecting payloads

### Challenge Writeup:

This challenge exploits the "Cowsay" website using command injection. The website uses code from the cowsay command. The interface has an input field that returns the user's input and prints it to the screen as part of an ASCII graphic. 

I tried to inject the "whoami" command but this just outputted the text "whoami" as part of the picture. 


![Screenshot 2025-06-13 234148](https://github.com/user-attachments/assets/d4f21635-15cf-44c6-8aec-686d54d726d1)

To manipulate this, I will use an inline command, so that the console will detect it and run it first. I inputted "$(whoami)" into the field, and this time the word "apache" was printed as part of the graphic. Bingo!

![Screenshot 2025-06-13 234407](https://github.com/user-attachments/assets/f5d4cf35-dc97-449f-a97d-398c5896bf5b)

We can run some other commands to see what information we can get. 

![Screenshot 2025-06-13 235621](https://github.com/user-attachments/assets/9950f164-5402-4cc5-944e-ac9c60728b6d)


### Summary:
Injection vulnerabilities are extremely dangerous, especially if they are running with administrator level access. An attacker can access sensitive data or manipulate the webpage to their liking. Applications should never trust the input of a user and they should follow strict sanitisation protocols to avoid these attacks. 
