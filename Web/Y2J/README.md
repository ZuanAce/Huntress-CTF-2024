# Y2J ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/4cca9c49-1d86-4c81-94f9-d6ab3fd5faee)


## Approach
1. This challenge involved converting YAML to JSON which was totally new to me!
   
   ![image](https://github.com/user-attachments/assets/efb36f5b-f339-46ef-bb17-6e30a22c1bfd)


2. Curious about YAML exploitation, I Googled around and found common vulnerabilities in Python and Ruby YAML deserialization. To identify which one I was dealing with, I reloaded the page a few times, inspecting headers and response details. Bingo—it's a Python server!
   
   ![image](https://github.com/user-attachments/assets/afa0d1f6-eb1c-45a2-a1b6-c2bebcd5a12c)
   
4. After digging through [Hacktricks](https://book.hacktricks.xyz/pentesting-web/deserialization/python-yaml-deserialization) and experimenting, I found a working exploit payload. Here’s what I used:

   ```
   !!python/object/new:str
   - !!python/object/apply:subprocess.check_output
      - !!python/tuple
        - cat
        - /flag.txt
   ```
   This payload let me run system commands, and voilà—executing it revealed the flag!
   
   ![image](https://github.com/user-attachments/assets/07db3750-86f7-4d12-95e3-bb1bc55ce523)

   
## Flag: 
flag{b20870a1955ac22377045e3b2dcb832a}




   





