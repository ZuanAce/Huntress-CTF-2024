# Zulu ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/40a2bc24-4bbc-4d30-b576-581ce02399b7)

## Approach
1. I started by checking the file type:
   
   ```
   zulu: compress'd data 16 bits
   ```
   Looks like it's compressed! But running *cat* just produced gibberish..

   ![image](https://github.com/user-attachments/assets/36c01507-4f7b-4aea-832b-77b87fb77706)

2. After a bit of head-scratching, I realized the file might need a .Z extension for uncompress to work properly with the help of ChatGPT. So, I renamed it to zulu.Z
   
3. With the file renamed, uncompress worked its magic. I ran cat again, and boom—there was the flag!
   
   ![image](https://github.com/user-attachments/assets/1ff03c45-cb5d-4cb7-b54e-efc6ad9d160a)

   
## Flag: 
flag{74235a9216ee609538022e6689b4de5c}




   


