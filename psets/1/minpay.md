# Paying the Minimum

Write a program to calculate the credit card balance after one year if a person only pays the minimum monthly payment required by the credit card company each month.

## Getting Started

Here's how to download this problem into your own [CS50 IDE](https://ide.cs50.io/). Log into CS50 IDE and then, in a terminal window, execute each of the below.

* Execute `cd` to ensure that you’re in `~/` (i.e., your home directory, aka `~`).
* Execute `cd cs51x` to change into that directory.
* Execute `mkdir pset1` to make (i.e., create) a directory called `pset1` in your home directory.
* Execute `cd pset1` to change into (i.e., open) that directory.
* Execute wget `https://www.dropbox.com/s/pbmp2pn5y3889de/minpay.zip` to download a (compressed) ZIP file with this problem’s distribution.
* Execute `unzip minpay.zip` to uncompress that file.
* Execute `rm minpay.zip` followed by `yes` or `y` to delete that ZIP file.
* Execute `ls`. You should see a directory called `minpay`, which was inside of that ZIP file.
* Execute `cd minpay` to change into that directory.
* Execute `ls`. You should see file `minpay.py`.

## Understanding

If you open `minpay.py`, you will see three variables for storing the below values from the user.

1. The outstanding balance on the credit card
2. The annual interest rate
3. The minimum monthly payment rate

Your task is to print the `minimum monthly payment`, `remaining balance` and `principle paid` for each month in the format shown in the example below. All numbers should be rounded to the nearest penny. 

Finally, print the result, which should include the `total amount paid` that year and the `remaining balance`.

```
$ python minpay.py
Enter the outstanding balance on your credit card: 4800 
Enter the annual credit card interest rate as a decimal: .2 
Enter the minimum monthly payment rate as a decimal: .02 
Month: 1 
Minimum monthly payment: $96.0 
Principle paid: $16.0 
Remaining balance: $4784.0 
Month: 2 
Minimum monthly payment: $95.68 
Principle paid: $15.95 
Remaining balance: $4768.05 
Month: 3 
Minimum monthly payment: $95.36 
Principle paid: $15.89 
Remaining balance: $4752.16
Month: 4 
Minimum monthly payment: $95.04 
Principle paid: $15.84 
Remaining balance: $4736.32 
Month: 5 
Minimum monthly payment: $94.73 
Principle paid: $15.79 
Remaining balance: $4720.53 
Month: 6 
Minimum monthly payment: $94.41 
Principle paid: $15.73 
Remaining balance: $4704.8 
Month: 7 
Minimum monthly payment: $94.1 
Principle paid: $15.69 
Remaining balance: $4689.11 
Month: 8 
Minimum monthly payment: $93.78 
Principle paid: $15.63 
Remaining balance: $4673.48 
Month: 9 
Minimum monthly payment: $93.47 
Principle paid: $15.58 
Remaining balance: $4657.9 
Month: 10 
Minimum monthly payment: $93.16 
Principle paid: $15.53 
Remaining balance: $4642.37 
Month: 11 
Minimum monthly payment: $92.85 
Principle paid: $15.48 
Remaining balance: $4626.89 
Month: 12 
Minimum monthly payment: $92.54 
Principle paid: $15.43 
Remaining balance: $4611.46 
RESULT 
Total amount paid: $1131.12 
Remaining balance: $4611.46
```

### Hints
Use the round function.
To help you get started, here is a rough outline of the stages you should probably follow in writing your code:

* Retrieve user input. (This is already present in the starter code)
* Initialize some state variables. Remember to find the monthly interest rate from the annual interest rate taken in as input.
* For each month:
    * Compute the new balance. This requires computing the minimum monthly payment and figuring out how much will be paid to interest and how much will be paid to the principal.
    * Update the outstanding balance according to how much principal was paid off.
    * Output the minimum monthly payment and the remaining balance.
    * Keep track of the total amount of paid over all the past months so far.
* Print out the result statement with the total amount paid and the remaining balance.