# I Can't SSH ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/5ed47a21-e754-428f-af9c-ac4afdfa3a55)

## Approach
1. I jumped into this challenge excited to use a private key for SSH access. I thought it would be straightforward, so I ran:

   ```
   ssh user@challenge.ctf.games -i id_rsa -p 32208
   ```
   
   ![image](https://github.com/user-attachments/assets/ef065777-48c9-4f46-9a52-c6b2b6a12759)

   But to my surprise, it didn’t work! I was confused and stuck right away.


2. I then decided to check the private key file with the cat command. That’s when I noticed something was off with the format.
   
   ![image](https://github.com/user-attachments/assets/6016589d-c113-4120-94af-07f27857898d)

   So, the format of the file was wrong!!!
   
4. I realized I needed to convert the key to the right format. A quick Google search led me to the steps I needed.

   ![image](https://github.com/user-attachments/assets/784d8ba0-5228-40f7-a0af-2a8d50228b89)

5. I carefully followed the instructions and remembered to set the permissions with chmod 600 newkey_in_right_format after a few frustrating tries.

   ![image](https://github.com/user-attachments/assets/f430dbbf-e68e-4815-810f-05f83c2ad7d2)

   ![image](https://github.com/user-attachments/assets/72ee1928-bf5c-4cf9-96ca-7d0471ece27d)

6. With my new key ready, I tried the SSH command again:

   ```
   ssh -p 32208 user@challenge.ctf.games -i newkey_in_right_format
   ```
   Finally, I got in! And I quickly found the FLAG!

   ![image](https://github.com/user-attachments/assets/28d59a8f-1f42-4be7-b0f2-35f33f2a2247)
   
## Flag: 
flag{ee1f28722ec1ce1542aa1b486dbb1361}



   



