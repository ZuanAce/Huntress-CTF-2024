# Base64by32

## Challenge Description

> <small>Author: @JohnHammond</small><br><br>This is a dumb challenge. I'm sorry. <br><br> <b>Download the file(s) below.</b>

## Approach

1. The title gave it away: Base64 by 32 means decoding the input 32 times!
2. Instead of decoding manually (which would be exhausting!), we used a simple Python script:

```python
import base64

# File path for the Base64 encoded text
file_path = "base64.txt"

# Read the contents of the file
with open(file_path, "r") as f:
    encoded_data = f.read().strip()

# Decode the Base64 data 32 times
for i in range(32):
    try:
        # Decode the Base64 data
        encoded_data = base64.b64decode(encoded_data).decode("utf-8")
        print(f"Decoded {i + 1} times: {encoded_data[:50]}...")  # Show partial result for progress
    except Exception as e:
        print(f"An error occurred during decoding: {e}")
        break

# Print the final decoded content
print("\nFinal Decoded Content:")
print(encoded_data)

```
3. Running the script reveals the flag!!
   
![image](https://github.com/user-attachments/assets/acff42b2-723c-47c7-b6a7-677a5482c0ec)

## Flag
flag{8b3980f3d33f2ad2f531f5365d0e3970}



