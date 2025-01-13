# Impossible
## Challenge Description
the challenge provides us with a nc command which requires us to submit a string which if satisfies the required conditions gives us the flag. Attached with it is the source code which would help us understand those conditions in order to get the flag.
## Source Code
```python
#! /bin/python3

flag = open('/flag.txt').read()

while True:
    s = input("Enter the string: ")
    if len(s) >= 20:
        print("String too long!!")
        print()
    elif len(s.upper()) < 25:
        print("String too short!!")
        print()
    elif len(s.upper()) > 25:
        print("String too long!!")
        print()
    else:
        print(f"Well done! FLAG: {flag}")
        break

```
## Understanding the task
the text from the flag.txt is printed when the loop iterates to the else condition for which the if conditions and the else if conditions must not be satisfied.
- The first if condition is satisfied if the length of the string is greater than or equal to 20, thus we must enter a string with length less than 20.
- The else if conditions are satisfied if the length of the string converted to upper case is less than 25 or greater than 25.

Hence the length of the required string must be less than 20 but after conversion to upper case must be equal to 25.

## Solution
In order to do so we must find a character which expands after being converted to uppercase. one such character is **"ß"** which when converted to uppercase returns "SS". 
We use this quality to form a string which has length less than 20 but as uppercase expands to exactly 25. One such string can be **"ßßßßßßßßßßßßa**". 
This string of length 13 on conversion to uppercase returns **"SSSSSSSSSSSSSSSSSSSSSSSSA"**, which is 25 characters long.
### Implementing the Solution
<img width="429" alt="Screenshot 2025-01-13 at 10 00 59 PM" src="https://github.com/user-attachments/assets/d787e6da-1de5-452f-82f8-cf10db76b77b" />

## Flag
> WannaHack{m0r3_l1k3_1_4m_p0551bl3_9eKzSXaF}
