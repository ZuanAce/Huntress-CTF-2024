# HelpfulDesk ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/74b5c714-34a3-4a52-b5b6-e06e00e166f5)


## Approach
1. When I first accessed the page, I was met with a login screen and a bold yellow banner warning about a "Security Update required." Clearly, there was something interesting to explore here.

   ![image](https://github.com/user-attachments/assets/5da529ed-dcd5-4a3d-89cd-074d7f7a75ca)

2. I checked out the security bulletin and found a critical update note for version 1.2. So, I downloaded the source code for both versions—1.1 and 1.2—o compare changes.

   ![image](https://github.com/user-attachments/assets/863550b1-b90e-4328-a620-91e8718ec363)

3. I extracted both versions into two separate folders and used the *diff* command for a quick comparison:

   ```
   diff -r helpfuldes-1.1/ helpfuldesk-1.2/
   ```

   ![image](https://github.com/user-attachments/assets/3fbed802-b975-42bd-a338-a41f60c09f6d)

   ![image](https://github.com/user-attachments/assets/4a175d9c-f46b-4c54-b2ad-30af48e73fe0)

   There it was: the most notable change was in the HelpfulDesk.dll file. A .NET library? Now, we were onto something.
   
6. Using DotPeek to decompile the libraries, I compared the two versions. My patience paid off when I found a small tweak in SetupController.cs—the Trim('/') function at SetupWizard() was removed in the latest version. Such a minor change… but those are often the most revealing.

   ![image](https://github.com/user-attachments/assets/d7acd4e7-1f31-4829-8c04-d20d97f2a8c7)

   ![image](https://github.com/user-attachments/assets/4aac7c1e-014b-4890-99e6-4c8092481632)

   ![image](https://github.com/user-attachments/assets/86783feb-2564-46ba-8891-c329c4615a82)

8. This led me to try accessing the path /Setup/SetupWizard/, revealing a setup panel where I could configure an administrator password.

   ![image](https://github.com/user-attachments/assets/8528240c-2d44-4482-a7e6-4a8e219b8885)

9. After setting a password (just a quick “admin:123” to get through), I logged in and started exploring. In the file system, there it was—the elusive flag.txt file.

   ![image](https://github.com/user-attachments/assets/e57be98e-637e-4c0c-b9d8-689b3f100deb)

10. A quick peek inside the downloaded *flag.txt* revealed the flag.
 
## Flag: 
flag{03a6f458b7483e93c37bd94b6dda462b}

