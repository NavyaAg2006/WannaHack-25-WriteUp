# Basics
## Challenge Description
This challenge requires us to compute the square of a given number 100 times and return the correct result for each input. If we succeed in doing so, we will receive the flag. We can do this using a Python library called **pwntools**.
On running the netcat command we see something like this-

<img width="531" alt="Screenshot 2025-01-13 at 8 23 19 PM" src="https://github.com/user-attachments/assets/2d4abf8e-567c-4cd6-8c76-e5024701bf8d" />

## Understanding The Task
- The challenge will provide an integer input.
- You need to compute the square of the given integer.
- You must repeat this process for 100 different inputs.
- If you correctly return the square for each input, the server will return the flag.
## Solution Code
```python
from pwn import *
import re

# Connect to the server
host = 'wannahack.iitbhucybersec.in'
port = 42521
conn = remote(host, port)

marker = b"*********************************************"
conn.recvuntil(marker)

# Solve 100 problems
for _ in range(100):
    while True:
        # Receive a line and strip whitespace
        line = conn.recvline().decode().strip()
        data = re.search(r"I GIVE: (\d+)",line)

        if data:
            num = int(data.group(1))
            print(f"I GIVE: = {num}")
            result = num ** 2                # Compute the square
            print(f"YOU GIVE: {result}")     # Print the result as required
            conn.sendline(str(result))       # Send the result back to the server
            break                            # Move to the next problem after sending the result
        else:
            print(f"couldn't extract number")
            
line = []
while True:
    try:
        conn.timeout = 2         
        line = conn.recvline().decode().strip()
        if not line:
            break
        print(f"{line}")
    except E0FError:
        print("connection closed by server")
        break

# Close the connection
conn.close()
```
## Explaination
- The script connects to a remote server.
- It waits for an initial marker indicating the start of the challenges.
- It solves 100 problems by reading numbers from the server, computing their squares, and sending the results back.
- After solving all problems, it waits for any final output from the server and prints it.
- The connection is closed when everything is done.

### Running the code on terminal looks like this

<img width="687" alt="Screenshot 2025-01-13 at 8 54 52 PM" src="https://github.com/user-attachments/assets/61620dbb-6ac7-4d5b-b87a-9aaaba2af4d5" />

after 100 problems are solved we get the flag!

<img width="745" alt="Screenshot 2025-01-13 at 8 55 14 PM" src="https://github.com/user-attachments/assets/8dd33a15-ab9d-4c80-ac65-bcdfc9c421ee" />

## FLAG
> WannaHack{pwntools_m4g1c_GbJkD252}
