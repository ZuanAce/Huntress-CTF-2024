# Ran Somewhere ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/a19c13ce-27ce-48bb-883e-8e5ee89c3546)

## Approach
1. I was given a file named ran_somewhere.eml, which is an email file. I opened it using an online [EML reader](https://www.emlreader.com/). The email described a scenario where someone’s laptop was compromised. The email had three attachments: a text file and two images. Here’s what the email content looked like:
   
   ![image](https://github.com/user-attachments/assets/f57db681-44da-48d9-80ca-dbc6382418ca)

2. The images attached to the email were labeled with hexadecimal codes. Here are the images:

   - Image 1 (Hex: 69 6d 20 6e 65 61 72 62 79):
     ![image](https://github.com/user-attachments/assets/75bb0a6f-fca6-4a4a-8e9d-b9447d26e68c)

     The victim seems to be near a coffee shop!

   - Image 2 (Hex: 66 69 6e 64 20 69 74 20 79 65 74):
     ![image](https://github.com/user-attachments/assets/7bc16e5d-4567-4361-9278-86f99f9b4197)

4. I started by performing reverse image searches for both images. I tried searching the full images as well as cropped sections, but nothing useful came up.
5. Next, I visited the [company website](https://sites.google.com/view/id-10-t/home)company website mentioned in the email. At the bottom of the page, I noticed this small text:

   ```
   Not Licensed to provide solutions to anyone or anywhere, especially Maryland
   ```
   
   This seemed like a clue pointing to a location in Maryland, USA.
   
7. I started searching for the names and companies mentioned in the email. One testimonial mentioned Z Vault Coffee Shop. Recalling that our victim was at a coffee shop, I searched for “Z Vault Coffee Shop.” This led me to a closed coffed shop named "Z Vault" at Bel Air.
   ![image](https://github.com/user-attachments/assets/e55f0e34-1020-403e-aa2b-f20a3d753bc4)

   ![image](https://github.com/user-attachments/assets/5c518b2e-ea25-4f67-8d64-447efe2f365a)

8. Now that I had narrowed it down to Bel Air, I searched for castles or significant historical buildings nearby. I discovered the Bel Air Armory, a notable landmark that matched the clues.
   
   ![image](https://github.com/user-attachments/assets/18782eeb-00b9-43f7-86a2-d3a57bdbb63c)
   
## Flag: 
flag{Bel Air Armory}




   

