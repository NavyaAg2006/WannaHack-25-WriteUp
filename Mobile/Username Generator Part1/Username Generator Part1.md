# Username Generator Part1
## Challenge Description
the challenge provides us an apk file and we are required to search for the flag within it using _apktool_ or _jadx_.

## Solution Walkthrough
We can use the apktool for reverse engineering Android APK files. It allows us to decode APK resources to nearly original form, rebuild them after modification, and debug small changes.

To decompile our file username-gen-one.apk we can use the command
```
apktool d username-gen-one.apk
```
this gives us a folder of all the files. I named this folder 'a'.
In order to find the flag in this folder i simply used the command
```
grep -r "WannaHack" a
```
this gave us the result

<img width="1402" alt="image" src="https://github.com/user-attachments/assets/b3cbb994-9451-4909-8f7d-a1efef9c9311" />

and here is our flag!

## Flag
> WannaHack{harDc0dED_57R1n95_aRE_e2}
