# Ancient Fossil ❌

## Challenge Description
> ![image](https://github.com/user-attachments/assets/b576f511-39dc-4205-837a-cc13a0a95206)


## Approach
1. The file I received seemed to be a SQLite3 database, based on its header. Upon further inspection using DB Browser, I found some unusual entries, such as a rebuild hash, which looked suspicious.

   ![image](https://github.com/user-attachments/assets/b49cc3f7-9e05-492b-922d-3d35ee69af58)

2. Since I wasn’t sure what this hash meant, I decided to Google it. That led me to discover that this was related to something called [Fossil SCM](https://fossil-scm.org/home/uv/download.html).

   ![image](https://github.com/user-attachments/assets/1e9d919c-fc00-47a1-aeb0-03e762e71376)

3. Fossil SCM is a version control system that can manage repositories similar to Git. I realized that the .fossil file I had could potentially be seen as a Git repository using Fossil SCM tools.
   So, I installed Fossil and used the export command to convert the file to a Git repository.<br>I ran the following command:

   ```
   ./fossil export --git ancient.fossil|grep flag
   ```

   Just like that, the flag was revealed!

   ![image](https://github.com/user-attachments/assets/a754eeb1-76af-4f97-87d8-ca930eb85f12)

   
## Flag: 
flag{2ed33f365669ea9f10b1a4ea4566fe8c}




   



