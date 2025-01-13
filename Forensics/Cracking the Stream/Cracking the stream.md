# Cracking The Stream
## Challege Description
We are given a pcap file. According to the description we are supposed to find a password protected file and crack the password to find our flag.

## Solution Walkthrough
On using the binwalk command on the pcap file provided,
```
binwalk chall.pcap
```
we see that there is a zip archive file along with our pcap file.

<img width="844" alt="image" src="https://github.com/user-attachments/assets/d90a8dc2-0a93-4ddd-916e-1ac88c3302fc" />

In order to extract this we use the command
```
binwalk -e chall.pcap
```

after the extraction we need to crack the password to extract the flag from zip file. To do this we use the rockyou.txt file. Just enter the command
```
fcrackzip -D -p rockyou.txt -v -u 2C36A.zip
```

This tells us the password to our zip archive.

<img width="489" alt="image" src="https://github.com/user-attachments/assets/6f522ea1-1638-4d05-944c-fc3873d01c12" />

Using this password we can extract our flag file.

## Flag
> WannaHack{F0ll0w_7he_H77P_S7ream5}
