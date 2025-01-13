# Cheap Amazon Revenge
## Challenge description
We have an nc command that looks like this.

<img width="701" alt="image" src="https://github.com/user-attachments/assets/2a53bef9-2ec8-4204-818d-fb515dbf2723" />

Clearing the amount is way less so we need to find a vulnerability in code to crack this.

## Solution
According to the source code provided it only takes integer input so if we deposit a large -ve integer dur to integer overflow it wraps around and we are able to obtain a large number for _money in pocket_. And then we can easily buy the flag.

<img width="744" alt="image" src="https://github.com/user-attachments/assets/3421b4b7-2b71-420b-810c-4759e80f279b" />

## Flag
> WannaHack{1n73g3r_0v3rfl0w_CSO101_aaSMLZ46}
