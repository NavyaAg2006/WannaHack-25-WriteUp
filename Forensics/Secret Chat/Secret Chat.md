# Secret Chat
## Challenge Description
The challenge provides us a pcap file and requires for us to find the conversation between two people held over TCP.

## Solution Walkthrough
We use Wireshark to examine our pcap file.

Since there are many packets we need to filter the ones we need. So we got to _Statistics_ then _Protocol Hierarchy_.

<img width="1432" alt="image" src="https://github.com/user-attachments/assets/08cf2fa9-35ef-4035-bcab-146f75f25fc3" />

There under Transmission Control Protocol(TCP) we choose data to look for the chats.

<img width="1119" alt="image" src="https://github.com/user-attachments/assets/c382b6cf-333b-431c-bd58-95a9d459a055" />

Then we right click to _Follow TCP Stream_ and we get the chat.

<img width="964" alt="Screenshot 2025-01-13 at 11 23 38 PM" src="https://github.com/user-attachments/assets/7955787e-8e38-435a-af4c-76ba791d9653" />

Clearly the string 'v2FubmFIYWNre1RDUF9FTkMwREVEX0NINFR9' is our flag in base 64 encoded format.
After using a decypher tool like [dcode](dcode.fr) We get our flag!

## Flag
> WannaHack{TCP_ENC0DED_CH4T}
