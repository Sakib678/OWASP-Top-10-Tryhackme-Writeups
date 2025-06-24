***
# AO9:2021 Security Logging and Monitoring Failures

When applications are set up, every action performed by a user should be recorded and stored.
It is important to do this as it can help to trace an attacker's steps in the event of an incident and it can also be the only sign that there has been a breach. 

Suspicious Activity within logs could include:
- Multiple login attempts
- Logins from a shady IP address
- Rapid requests from a client


Logs should include IP addresses, usernames, timestamps etc

For example, in 2013, attackers gained access to Target's network via a third party. Target failed to log failed login attempts properly, and alerts were not set up, allowing attackers to brute force their way into the network. The stores also failed to monitor their logs for suspicious activity. 



### Challenge Writeup:

This challenge is a log analysis challenge. 

The logs indicate login attempts with invalid credentials. These are from the IP address 49.99.13.16, suggesting that this is the IP address of an attacker. 
The attempts are also for administrator level accounts. The 401 HTTP error code indicates that the attempts were failed. The repeated attempts suggest that this is a brute force attack, due to the combination of username and passwords trying to gain access to accounts.  

![image](https://github.com/user-attachments/assets/7144e40c-efb7-4cb5-8d06-debf324bf197)



### Mitigation:
- Ensure that logs are comprehensively logged
- Rank suspicious activity so that the higher risk and impact actions are responded to quicker
- Securely store these log files
- Create and implement a process where logs are regularly reviewed and analysed to detect possible security incidents. 
- Use real time automated monitoring systems to detect security incidents.


### Summary: 
Without proper logging and monitoring, security breaches can go unnoticed, which can allow an attacker to lay undetected for weeks or months. 
Effective logging act as a warning system as well as a forensic tool. They can help organisations to detect, respond to and recover from attacks. 
Therefore, it is necessary that organisations log not only critical events but also other user activity. 

***
