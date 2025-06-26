***
# A10:2021 Server Side Request Forgery

A Server Side Request Forgery attack occurs when an attacker tricks the server into making requests on behalf of the attacker. This is dangerous as a server can have a lot more privileges than the attacker and a higher access level. This can lead to an attacker exploiting or gaining access to an internal system, extracting sensitive data or conducting further attacks. 

For example, in 2020, an SSRF vulnerability in GitHub's repository mirroring feature allowed attackers to send internal requests and access Github infrastructure.

### Tools one could use to exploit this:
- Burp Suite
- curl

  
### Challenge Writeup:

The challenge involves looking through a website and trying to exploit an SSRF vulnerability. 

When exploring the website, there seems to be an admin area. When trying to access this, we discover that it is only available from localhost. 

![image](https://github.com/user-attachments/assets/781773d1-823a-47b1-9380-9005b11d2083)

By hovering over the "Download Resume" button, I can see a server parameter pointing to "secure-file-storage.com" and an id parameter. It might be worth it to check if these parameters can be manipulated.

I first changed the server parameter to the IP address of my attackbox. 
I also started a netcat listener to listen on port 80 in order to recieve the contents of any request. 

![image](https://github.com/user-attachments/assets/7aeaba1f-c39f-4cb1-856d-77a3eae1376a)

The manipulation of the server parameter sends the request to my VM rather than the secure file storage server. This shows me the API key, which is a unique code that is used to identify users and authentication.

This next part was a little more difficult.

Gaining access to the admin area involves trying to exploit an SSRF vulnerability. 
I tried changing the server parameter so that the admin area is being accessed via localhost. This link still works but doesn't produce exactly what I need.

![image](https://github.com/user-attachments/assets/ffb43639-0017-45bd-87c4-daa9785d1f9f)


We need to remove the id part of the URL, however we cannot access the site without it. So our next step is to try to keep the link together but stop the server from using the id part of it. 

This link provided some help. This is a method called escaping, which will break up the link. 

https://portswigger.net/web-security/essential-skills/obfuscating-attacks-using-encodings

I used the following link:
http://10.10.246.211:8087/download?server=http://localhost:8087/admin%23&id=75482342

This allowed me to view the following pdf file, which showed em the flag.

![image](https://github.com/user-attachments/assets/ca90554b-2a31-4507-b8bb-e6eb188702a8)


### Mitigation/Prevention Strategies:

- Validate and sanitise all input from a user
- Segment the network and ensure web servers cannot directly access other internal services, unless it is through secured and checked channels. 
- Comprehensively log all server side requests 
- Apply the principle of least privilege

### Summary:

This challenge demonstrates how a harmless parameter being exposed can lead to a serious SSRF vulnerability. By manipulating this parameter, I was able to make the server send a request to my own machine, where I captured an API key. Using URL encoding, I was able to access the internal admin area. This highlights the importance of validating input. 



### Summary:



***

