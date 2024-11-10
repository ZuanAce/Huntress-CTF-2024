# Sekiro ✅ 

## Challenge Description

![image](https://github.com/user-attachments/assets/af4d6bf9-b9fa-491e-9073-3098ab611d2b)

## Approach

1. After connecting to the challenge server, it was clear that the game followed this pattern:
   - Strike can be countered by Block.
   - Block can be countered by Advance
   - Retreat can also be countered by Advance.
   - Advance can also be countered by Retreat.

   This essentially created a loop similar to the logic of Rock Paper Scissors. The server would announce its move, and we had to respond correctly based on the opponent's choice.

2. To make our lives easier, we wrote a simple Python script to automate the game.

```python
import socket

# Server information
HOST = "challenge.ctf.games"
PORT = 31310

# Define responses based on opponent's moves
def get_response(opponent_move):
    move = opponent_move.lower().strip()
    if "strike" in move:
        return "block\n"
    elif "block" in move:
        return "advance\n"
    elif "retreat" in move:
        return "advance\n"
    elif "advance" in move:
        return "retreat\n"
    else:
        return None  # Handle unexpected input

try:
    # Create a socket and connect to the challenge server
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.connect((HOST, PORT))
        print("[*] Connected to the server.")

        buffer = ""  # Store accumulated data

        while True:
            # Receive data from the server
            chunk = s.recv(1024)  # Read in chunks
            if not chunk:
                print("[!] Connection closed by server.")
                break

            # Decode the chunk and handle decoding errors gracefully
            buffer += chunk.decode(errors='ignore')

            # Print all accumulated data
            print(buffer)

            # Process opponent's move if available
            if "Opponent move:" in buffer:
                opponent_move = buffer.split("Opponent move:")[-1].split("\n")[0]
                print(f"[*] Opponent move: {opponent_move}")

                # Determine and send your move
                response = get_response(opponent_move)
                if response:
                    print(f"[*] Your move: {response.strip()}")
                    s.sendall(response.encode())
                else:
                    print("[!] Unexpected input or end of game.")
                    break

                # Clear the buffer after processing the move
                buffer = ""

except Exception as e:
    print(f"[!] An error occurred: {e}")

```

## Flag
flag{a1ae4e5604576818132ce3bfebe95de5}
