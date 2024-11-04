# Finders Fee ✅

## Challenge Description
> ![Screenshot 2024-11-04 210545](https://github.com/user-attachments/assets/e670963a-3654-4239-b4bb-eff81935718a)

## Approach
1. The hint was all in the title—Finders Fee. A simple *find* command was all it took to track down the hidden flag.txt file. With the help of ChatGPT, I constructed a find command to search for the flag.txt file within the /home directory and display its contents. The command is as follows:
   
   ```
   find /home -name "flag.txt" -exec cat {} \;
   ```
   
   **This command:**
   - Searches for files named flag.txt starting from the /home directory.
   - Uses -exec cat {} \; to print the contents of each found file.
     
3. Running the commad and just like that, the flag was revealed!
   
   ![image](https://github.com/user-attachments/assets/3d0f3778-e6cd-49e3-96e1-5eeb9b556a33)

## Flag: 
flag{63a10f0440218364424b20f9ddf6ad39}




   


