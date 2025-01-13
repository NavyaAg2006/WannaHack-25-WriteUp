# Guess
## Challenge Description
The challenge provides us with an nc command which is a guessing game, but the catch is we have to repond very quickly.

## Solution
In order to do this we write a python code using pwntools to interact with the host server and respond quickly.

## Solution Code
```python
from pwn import *

# Server details
host = 'wannahack.iitbhucybersec.in'
port = 42987

conn = remote(host, port)

marker = b"*********************************************"
conn.recvuntil(marker)
l = conn.recvline().decode().strip()
print(l)
l1 = conn.recvline().decode().strip()
print(l1)

low, high = 1, 100000000

while low <= high:
     guess = (low + high) // 2
     conn.sendline(str(guess))
     print(f"Sent guess: {guess}")
     response = conn.recvline().decode().strip()
     print(f"response: {response}")
     if "HIGHER" in response:
        print("going higher")
        low = guess + 1
     elif "LOWER" in response:
        print("going lower")
        high = guess - 1
     else:
        print("break while loop")
        break 
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
I have implemented binary search algorithm to guess a number within a given range (low to high). Here's how it works:

- It calculates the middle (guess) of the current range.
- Sends the guess to a server using conn.sendline.
- Receives feedback (response), which indicates whether the guess should be higher, lower, or if it's correct.
- If the response is "HIGHER", it adjusts low to guess + 1 (narrows the range upwards).
- If the response is "LOWER", it adjusts high to guess - 1 (narrows the range downwards).
- If the response indicates the guess is correct, it breaks the loop

after the correct guess is made we receive the flag!

<img width="571" alt="image" src="https://github.com/user-attachments/assets/a15cc500-610f-4b3b-b2da-14d75fee5483" />

## Flag
> WannaHack{m3n_gu335_suks_4an3ecwl}
