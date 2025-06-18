***
# AO6:2021 Vulnerable and Outdated Components

As the name says, if a component is not up to date or no longer supported, it may mean the application is at a high risk of an attack. A company may not be aware that their applications are not up to date and it can be very simple for an attacker to exploit this. 

For example, in 2019, a website belonging to the Australian government was hacked due to a vulnerability in a PHP library called SimplePie. This vulnerability was known and an update had been released, however it had not been patched. 

### Tools one could use to exploit this:
- Burp Suite: Useful for analysing HTTP requests and responses
- Searchsploit - for finding exploits
- 

### Challenge Writeup:
This challenge requires us to exploit a known vulnerability in a bookstore web application. On the front page, it was clearly indicated that PHP and mySQL were in use by the webpage. 
However, I want to get the exact versions, so I used Burp Suite for this challenge. I used the Burp Suite proxy to look at the request and response for the homepage. The response indicated that PHP 8.0.21 was being used. 
I also ran a google search for an exploit for a bookstore application using the phrase "bookstore PHP 8.0.21 exploit". This search provided me with an premade exploit that I could use on this application. 



![Screenshot 2025-06-18 162348](https://github.com/user-attachments/assets/4025a978-eafc-4d8d-8a49-706248be1335)



I then ran the script within the terminal and passed the URL of the page. This gave me a web shell which I could use to look through directories and see where the web application files were stored. The flag was located in /opt/flag.txt/
![Screenshot 2025-06-18 162951](https://github.com/user-attachments/assets/4d50ba02-13b9-4efb-880a-1b9bc70f0e46)




### Mitigation:
- Regularly monitoring and checking for security updates for all components, and applying these patches as soon as they are released
- Create and implement a robust process for updating and patching components
- Maintain a software inventory, which includes a comprehensive list of all the components, including their dependencies and versions
- Avoid using unsupported or end of life applications. 

### Summary:
Vulnerable and Outdated Components are a critcal risk to web applications. They can provide attackers with an easy entrance into your network as a vulnerability may already be known. 
In this challenge, a known PHP vulnerabiltiy for an online book store application was used. This emphasizes the importance of patching and continuiously monitorimg the web for known vulnerabilities. 


***
