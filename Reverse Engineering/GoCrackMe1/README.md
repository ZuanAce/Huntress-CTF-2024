# GoCrackMe1 ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/44e3d79f-0fbd-4e1d-b204-5db900044a36)


## Approach
1. Since it’s a web challenge, I went straight to inspect the page and spotted a suspicious auth cookie.

   ![image](https://github.com/user-attachments/assets/c642f223-3b67-453b-9dc7-ba0c5e10fbcd)

2. Ran the cookie through [Cipher Identifier](https://www.dcode.fr/cipher-identifier) and found it’s base64 encoded! Decoding it gave me **testuser.0.1730771528**.

   ![image](https://github.com/user-attachments/assets/ebbc5002-f270-4410-8a19-9215ccf2521d)

3. To gain admin access, I tweaked the cookie to **admin.1.0.1730771528**, encoded it back, set the cookie, and refreshed the page. Just like that—I was in as admin!

   ![image](https://github.com/user-attachments/assets/a43085df-17d7-46c9-ad5d-1258ea128a44)

   ![image](https://github.com/user-attachments/assets/cb532c53-1b24-4f28-8f36-6f509fe6854b)

4. Looked around but didn’t see a flag. Then, I noticed an API documentation section and found I could edit plant alerts and send commands. Jackpot!

   ![image](https://github.com/user-attachments/assets/e6aa0b89-8822-4d59-b841-cebf35bef9ba)

   It turns out I can edit the plant's alert and send command, and the logs will capture the output!

6. I set the alert command to ls and ran it through the API, which revealed a flag.txt file in the logs.
   
   ![image](https://github.com/user-attachments/assets/1e85e534-09f2-4db7-9caa-74e94ab08abd) ![image](https://github.com/user-attachments/assets/421c3c22-10a3-436e-8ab7-28b8df040524)

   ![image](https://github.com/user-attachments/assets/ff61283e-8785-490d-91b3-3b66c59aeaaa)

8. Updated the command to cat flag.txt, executed it, checked the logs, and there it was—the flag!

   ![image](https://github.com/user-attachments/assets/f281241a-2cd9-459d-bdc0-c954e1c8d888)

   ![image](https://github.com/user-attachments/assets/ee664308-f62d-4e94-9140-59a1f923fc22)
  
## Flag: 
flag{c29c4d53fc432f7caeb573a9f6eae6c6}




   
