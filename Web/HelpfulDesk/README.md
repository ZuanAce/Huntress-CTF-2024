# HelpfulDesk ✅

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




   






After accessing the application and reviewing the security bulletin, I noticed there was a new version available (1.2), while the deployed version was 1.1.

Security bulletin and detected software version.
Security bulletin and detected software version.
I downloaded the file and tried to identify changed files using a simple diff command. It quickly turned out the only significant change was in the HelpfulDesk.dll file. Then, using the file command, I verified the file type, revealing it was a .NET library.
Detected differences in files.
Detected differences in files.
Using DotPeek, I decompiled both library versions, saving them to separate folders. Then, with WinMerge, I compared changes between versions. In SetupController.cs, responsible for software configuration, the expression Trim('/') was removed in the newer version.
Comparison of differences after decompilation.
Comparison of differences after decompilation.
I decided to visit the suggested URL path. Entering /Setup/SetupWizard/ revealed the application’s setup panel, allowing me to set an administrator password.
Exploiting the vulnerability and setting a new admin password.
Exploiting the vulnerability and setting a new admin password.
After setting my own password, e.g., admin:admin, I successfully logged into the application and retrieved the flag.
Admin file listing in the Desktop directory.
Admin file listing in the Desktop directory.
Obtained flag: flag{03a6f458b7483e93c37bd94b6dda462b}
