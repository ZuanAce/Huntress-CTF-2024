# Zimmer Down ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/dc15769b-ac61-43c2-ba9b-a5e579f025f5)


## Approach
1. I was given a forensic challenge with a NTUSER.DAT file. This file contains the Windows Registry hive for user-specific configurations.
   ChatGPT suggested me to use **Eric Zimmerman's Registry Explorer** — an excellent tool for navigating and analyzing Registry hives.

   ![image](https://github.com/user-attachments/assets/42be1b20-c81d-40f0-ac24-b3aee0224a34)

   ![image](https://github.com/user-attachments/assets/9a482427-3482-413a-bf07-085d07aee4ee)


3. Using Registry Explorer, I started searching for common places where artifacts or unusual data might hide. ChatGPT pointed me toward several interesting paths to investigate:

   ```
   NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist
   NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run
   NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
   and many more
   ```
   
4. As I browsed through the hive, something unusual caught my eye in the `RecentDocs` key. There was an entry for a folder named `.b62`. Now, that doesn’t look like your typical folder name — definitely sus!

   ![image](https://github.com/user-attachments/assets/7006062f-6792-47e2-a000-35ed08149fc1)

   When I clicked on it, the `Target Name` field contained an encoded string. It looked like gibberish, but I had a hunch. .b62... could it be Base62 encoded?

5. I took the string and pasted it into an online Base62 decoder. Sure enough, it decoded perfectly, revealing the hidden flag! 

   ![image](https://github.com/user-attachments/assets/b3886781-3146-4f71-88a4-c0998a2dc71f)
   
## Flag: 
flag{4b676ccc1070be66b1a15dB601c8d500}



   



