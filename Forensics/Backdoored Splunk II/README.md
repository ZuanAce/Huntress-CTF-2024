# Backdoored Splunk II ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/ea8d26f3-a07c-42bf-ac20-777b1e1ab99a)



## Approach
1. It's my first time doing this challenge, so I did some Google search. I noticed that this challenge is very similar with the [Backdoored Splunk](https://github.com/LazyTitan33/CTF-Writeups/blob/main/Huntress-CTF-2023/Forensics/Backdoored_Splunk.md) challenge from last year.
   However, after some digging, I found something suspicious in the `dns-health.ps1 file`:

   ![image](https://github.com/user-attachments/assets/e697f6f0-5f19-4f37-be67-715191cc9e1e)

3. ChatGPT suggested that "1200" relates to modulated data signals, which led me to use a tool called **Minimodem**,  a command-line program which decodes (or generates) audio modem tones at any specified baud rate, using various framing protocols. It acts a general-purpose software FSK modem, and includes support for various standard FSK protocols such as Bell103, Bell202, RTTY, TTY/TDD, NOAA SAME, and Caller-ID. After installing it, I ran:
   
   ```
   minimodem --rx 1200 -f transmissions.wav
   ``` 

4. Success! I decoded a hidden message along with the flag!

   ![image](https://github.com/user-attachments/assets/f400721b-cf27-4aef-a88d-83dff8b2a443)
   
## Flag: 
flag{f28d133e7174c412c1e39b4a84158fa3}




   



