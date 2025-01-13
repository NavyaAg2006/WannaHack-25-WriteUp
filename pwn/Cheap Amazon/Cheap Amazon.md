# Cheap Amazon
## Challenge Description
We have an nc command that looks like this and the source code. 

<img width="736" alt="image" src="https://github.com/user-attachments/assets/eada0ec2-ce05-4c92-bc60-8c8429f56d6f" />

In order to buy the flag we need to find a vulnerability in the code to get _money in pocket_ equal to the cost of the flag.

## Source Code
```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    puts(" ██████╗██╗  ██╗███████╗ █████╗ ██████╗      █████╗ ███╗   ███╗ █████╗ ███████╗ ██████╗ ███╗   ██╗"); 
    puts("██╔════╝██║  ██║██╔════╝██╔══██╗██╔══██╗    ██╔══██╗████╗ ████║██╔══██╗╚══███╔╝██╔═══██╗████╗  ██║"); 
    puts("██║     ███████║█████╗  ███████║██████╔╝    ███████║██╔████╔██║███████║  ███╔╝ ██║   ██║██╔██╗ ██║");  
    puts("██║     ██╔══██║██╔══╝  ██╔══██║██╔═══╝     ██╔══██║██║╚██╔╝██║██╔══██║ ███╔╝  ██║   ██║██║╚██╗██║");
    puts("╚██████╗██║  ██║███████╗██║  ██║██║         ██║  ██║██║ ╚═╝ ██║██║  ██║███████╗╚██████╔╝██║ ╚████║");
    puts(" ╚═════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═╝         ╚═╝  ╚═╝╚═╝     ╚═╝╚═╝  ╚═╝╚══════╝ ╚═════╝ ╚═╝  ╚═══╝");
    setbuf(stdout, NULL);
    int balance = 1000;
    int money = 0;
    printf("Welcome! Buy whatever you want, but remember to check your balance.\n");
    while(1){
        printf("\n");
        printf("Money in pocket: %d\n", money);
        printf("Current Amazon Balance: %d\n", balance);
        printf("1. Withdraw\n");
        printf("2. Deposit\n");
        printf("3. Buy flag (PRICE: 1000000)\n");
        printf("4. Exit\n");
        int input;
        int option;
        printf("Option: ");
        scanf("%d", &option);
        if(option == 1){
            printf("Enter amount of money to withdraw: ");
            scanf("%d", &input);
            if(input <= balance) {
                balance -= input;
                money += input;
            }
            else {
                printf("Not enough balance!\n");
                continue;
            }
        }
        else if(option == 2){
            printf("Enter amount of money to deposit: ");
            scanf("%d", &input);
            if(input <= money) {
                balance += input;
                money -= input;
            }
            else {
                printf("Not enough money!\n");
                continue;
            }
        }
        else if(option == 3){
            if(money < 1000000) printf("Not enough money!\n");
            else {
		system("cat /flag.txt");
                return 0;
            }
        }
        else if(option == 4){
            return 0;
        }
        else{
            printf("Not a valid option!");
        }
    }
    return 0;
}
```
## Solution Walkthrough
We can see that whenever the input amount is less then the money or balance, their value changes accordingly. It can be noted that they haven't accounted for negative values.

So if we choose deposit then input -1000000, the if statement _input <= money_ is satisfied since
```
money = 0
input = -1000000
```
and thus by
```
balance += input;
```
the new balance becomes _(balance + input)_ i.e.
```
balance = 1000 + (-1000000) = -999000
```
and by 
```
money -= input;
```
the new money becomes _(money-input)_ i.e.
```
money = 0 - (-1000000) = 1000000
```
And thus now we have enough money to buy the flag!

<img width="750" alt="image" src="https://github.com/user-attachments/assets/0a9e3bdf-362e-4371-8e25-8be3425630f1" />

## Flag
> WannaHack{w3lc0m3_70_pwn1ng_47N2SBVo}
