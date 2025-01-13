# Crackme
## Challenge Description
The challenge provides us a file which on running seems to be asking for a password to provide the flag. It looks like the password needs to be cracked.

## Solution Walkthrough
Although we could try to crack the password there seems to be a simpler way to solve this. We can use the strings command to extract all strings from the file since the file itself isn't password protected. The Strings command also reveals flag along with all the other strings!

<img width="399" alt="image" src="https://github.com/user-attachments/assets/e65b87df-1a81-49f9-8d53-43cff28f1d7d" />

## Flag
> WannaHack{lmao_strings_make_it_too_easy}
