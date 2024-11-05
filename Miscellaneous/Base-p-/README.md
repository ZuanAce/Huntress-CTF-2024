# Base-p- ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/1be5389a-250c-4dc2-a458-de4c6411eb35)

## Approach
1. I opened the file and found what looked like Chinese characters. After a quick Google search(chinese character CTF), I realized it was base65536 encoding!
   
   ![image](https://github.com/user-attachments/assets/ed5a86ca-363b-4a8c-8ad3-fd177096c1ae)

2. Decoded the base65536 text with [online base65536 decoder](https://www.better-converter.com/Encoders-Decoders/Base65536-Decode) and got…base64.
   
   ![image](https://github.com/user-attachments/assets/4ab779af-2316-4a50-b533-0df82f767ae2)
   
3. Threw it into [Cyberchef](https://gchq.github.io/CyberChef/) to decode the base64, which gave me an image file containing a series of colours.
   
   ![image](https://github.com/user-attachments/assets/50386a70-8fd2-4803-ad4c-5a6b3c409ca2)

5. Figured out that it's somehow related to colour decoder, a simple google search realised it's hex colour! Using this [colour picker](https://imagecolorpicker.com/) gives the string below:
   ```
   #666c61#677b35#383663#663863#383439#633937#333065#613762#323131#326666#663339#666636#617d20
   ```
6. Using Cyberchef again to decode, and the flag revealed!
   
   ![image](https://github.com/user-attachments/assets/20a25fa6-5b67-4cf5-a0ec-602645c97e4e)

## Flag: 
flag{586cf8c849c9730ea7b2112fff39ff6a} 



   



