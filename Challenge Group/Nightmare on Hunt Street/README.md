# Nightmare on Hunt Street ✅

## Challenge Description

![image](https://github.com/user-attachments/assets/f094ef40-4f42-44e5-bf11-cefbfe06fa07)


## Solution Part 1

The IP address of the host used by the attacker was found to be 10.1.1.42:  
![image](https://github.com/user-attachments/assets/eee3375f-8260-4f9e-b9db-e001b1cc45a8)


**Part 2**
<b>How many times was the compromised account brute-forced?</b> Answer just the integer value. 

## Solution Part 2 

To find this, I filtered the logs for Event ID 4625, which corresponds to failed login attempts with a total of 32.
![image](https://github.com/user-attachments/assets/2c28bee8-9398-4e4a-8e2f-31c46b9e9cd3)

**Part 3**
<b>What is the name of the offensive security tool that was used to gain initial access?</b> Answer in all lowercase. 

## Solution Part 3
Was determined by reviewing the logs and identifying `psexec` was used for initial access.

**Part 4**
<b>How many unique enumeration commands were run with <code>net.exe</code>?</b> Answer just the integer value.

## Solution Part 4

Filtered logs revealed 5 total commands, but only 3 unique commands were identified:
```
    <Data Name="CommandLine">"C:\Windows\system32\net.exe" users</Data>	
    <Data Name="CommandLine">"C:\Windows\system32\net.exe" localgroup administrators susan_admin /ADD</Data>
    <Data Name="CommandLine">"C:\Windows\system32\net.exe" user susan_admin Susan123! /ADD</Data>
    <Data Name="CommandLine">"C:\Windows\system32\net.exe" user</Data>
    <Data Name="CommandLine">"C:\Windows\system32\net.exe" user susan_admin SusanIsStrong123 /ADD</Data>
```

**Part 5**
<b>What password was successfully given to the user created?</b>

## Solution Part 5
The password was found in the log entry `C:\Windows\system32\net1 user susan_admin Susan123! /ADD` for the answer of `Susan123!`
![image](https://github.com/user-attachments/assets/df29982f-3944-4714-ae94-a02c72e4c273)
