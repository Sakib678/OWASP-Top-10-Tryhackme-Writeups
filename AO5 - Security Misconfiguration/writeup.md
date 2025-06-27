
***
# AO5:2021 Security Misconfiguration

As the name suggests, security misconfigurations occur when systems and applications are not configured properly. Perhaps, features shouldn't be installed or enabled or default accounts and their passwords are unchanged. 
This vulnerability can lead to more severe vulnerabilities, such as remote code execution. 

It is common for developers to use debugging functions when writing code. However, if these are not disabled when the application is deployed, hackers can exploit these. 

For example, a company may onboard a new laptop or server, and it may come with a lot of sample applications. These applications could have several known security vulnerabilities. An attacker could exploit the vulnerabilities and gain access to data that the application can also access. 


### Challenge Writeup:

The challenge is a todo list web application where the goal is to read the application source code. By exploring the app and trying to delete the "Watch TV" task, we are met with an SQL error page

![Screenshot 2025-06-17 184015](https://github.com/user-attachments/assets/bf7d8e9b-7212-4081-b95e-ce21b50a121d)

I then hovered over one of the frames and a console icon appeared, which I can use to execute python code.

I ran the following python code "import os; print(os.popen("ls -l").read())" in order to print the directory contents. 
![Screenshot 2025-06-17 184258](https://github.com/user-attachments/assets/8be502aa-08f7-41dc-b6da-148d3e1bf94e)

A quick explanation of the command: It imports python's OS library, which allows it to interact with the operating system. 
It also starts a shell and runs the command "ls -l", which lists files in the current working directory. 
Then it reads the output of this command as a string, which is then printed to the console. 

The first question asks for the name of the database file, which is "todo.db". 

Now we need to try and modify this command to read the app.py file, which contains the application source code. 
![Screenshot 2025-06-17 184720](https://github.com/user-attachments/assets/6ca77e79-e1e6-4a10-8d3d-6d1d4650f036)
I used the cat command here, but it is likely that other commands would work as well. 

This showed me the full source code of the application, including application logic. 
### Mitigation:
- Ensuring access controls are strong and restrictive
- Centralise configuration management, perhaps using Active Directory
- Regularly audit systems
- Ensure sufficient logging, and ensure that the logs are regularly monitored. 

### Summary:
Security Misconfiguration happens when insecure settings or configurations are not set properly. This can lead to an attacker gaining unauthorised access. In this challenge, a debugging console was exposed on an error page, which an attacker could use to run python code. This emphasises the importance of ensuring that settings are configured correctly, as a simple debugging tool led to a compromise of the full application. 

***
