# Hidden Streams ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/fc6609d8-88b4-47e7-a1c2-e055981c6afe)


## Approach
1. We were given a Windows event log file, and the first step was to open it and skim through the logs. At first glance, these logs can be overwhelming, but if you know what you're looking for, they become much easier to navigate.
2. Event IDs are crucial because they tell you what kind of event was recorded. Thanks to ChatGPT, I knew that event ID 15 might be important, so I focused on that one. 
3. I dug into the details of the event and found a hash under the `Contents` section of the log. This seemed like a key piece of information!
 
   ![image](https://github.com/user-attachments/assets/527b53c7-162f-4a69-a394-e5c474034c52)
   
4. The hash was encoded in Base64, so the next logical step was to decode it. After decoding, I found that it gave me the flag.

   ![image](https://github.com/user-attachments/assets/2910d598-cddd-412b-9d03-1342d562b98b)

## Flag: 
flag{bfefb891183032f44fa93d0c7bd40da9}
