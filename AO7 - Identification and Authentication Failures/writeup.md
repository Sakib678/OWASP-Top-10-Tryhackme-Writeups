***
# AO7:2021 Identification and Authentication Failures
This type of vulnerability occurs when a system fails to correctly verify a user's identity. An attacker can exploit this flaw to access data that they shouldn't be able to access, typically by posing as another user. 

For example, an application could allow (by accident) a brute force attack, allowing an attacker to try every password and pose as an authenticated user. It could also expose a session identifier in the URL, allowing an attacker to hijack the session. 



### Mitigation:
- Implement multi-factor authentication to prevent brute force and other attacks 
- Do not deploy applications with default credentials and avoid hard coding these
- Ensure passwords are complex and a strong password policy is enforced
- Limit login attempts and implement account lockouts
- Use a secure server-side session manager that generates a new random session ID after login
- Prevent duplicated usernames

### Challenge Writeup:

This challenge involves bypassing identity verification by re-registering as a user, in order to view the content that is under the access of the original user.
For the first flag, we need to register as "darren", which is a user that already exists. 

![image](https://github.com/user-attachments/assets/e591c646-23e2-456d-85ea-ec39bbd2d145)

So by registering as " darren" (with a space before darren), it allows us to create a new account that is able to view darrens data. 

![image](https://github.com/user-attachments/assets/bf18b525-64e9-4f2a-96bc-f9e82ad5b431)

![image](https://github.com/user-attachments/assets/e4c8d039-7870-4000-8d81-6151b776ded8)

The second flag involves doing the same thing but as "arthur". 

![image](https://github.com/user-attachments/assets/e5a060de-66d5-419c-9843-69a49ccd3d66)

### Summary:

This challenge emphasizes how important it is for applications to ensure that every user is unique, and users are authenticated correctly.  Users should not be able to pose as each other. This simple mistake allowed attackers to create a duplicate user account and compromise another user's data.  Implementing strict checks on users who register, securing sessions and enforcing multi factor authentication are essential defences when considering the protection of user accounts. 

***
