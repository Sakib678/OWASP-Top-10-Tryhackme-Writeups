This challenge is a Broken Access Control challenge focusing on IDOR (Insecure Direct Object Reference). This is where an attacker is able to access a resource indirectly via a broken access control.


![Screenshot 2025-06-09 172830](https://github.com/user-attachments/assets/14e6ea86-4c37-47cc-b734-5caebc799178)


The machine is a note server where users can view their own notes. The URL shows some promise here as there is a parameter being passed within the URL called "note_id=1". So by simply adjusting the id value, we can access other people's notes. 

By changing the id value to 0, it gives us the flag. 

![Screenshot 2025-06-09 173128](https://github.com/user-attachments/assets/89628994-e210-46c4-bf06-f936ad51d476)
