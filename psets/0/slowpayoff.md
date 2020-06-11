# Paying Debt Off In a Year

Write a program that calculates the minimum fixed monthly payment needed in order pay off a credit card balance within 12 months. We will not be dealing with a minimum monthly payment rate.

Here are a few examples of how the program might work.

```
$python slowpayoff.py
Enter the outstanding balance on your credit card: 1200 
Enter the annual credit card interest rate as a decimal: .18 
RESULT
Monthly payment to pay off debt in 1 year: 120 
Number of months needed: 11 
Balance: -10.05
```

```
$python slowpayoff.py
Enter the outstanding balance on your credit card: 32000 
Enter the annual credit card interest rate as a decimal: .2 
RESULT 
Monthly payment to pay off debt in 1 year: 2970 
Number of months needed: 12 
Balance: -74.98
```

## Specification

You are given a starter file which takes the following floating point numbers:

1. the outstanding balance on the credit card
2. annual interest rate as a decimal

Print out the fixed minimum monthly payment, number of months (at most 12 and possibly less than 12) it takes to pay off the debt, and the balance (likely to be a negative number).

Assume that the interest is compounded monthly according to the balance at the start of the month (before the payment for that month is made). The monthly payment must be a multiple of $10 and is the same for all months. Notice that it is possible for the balance to become negative using this payment scheme. In short:

```
Monthly interest rate = Annual interest rate / 12.0
```

```
Updated balance = Previous balance * (1 + Monthly interest rate) – Minimum monthly payment
```


## Getting Started
Here’s how to download this problem’s starter files into your own CS50 IDE. Log into CS50 IDE and then, in a terminal window, execute each of the below.

* Execute `cd` to ensure that you’re in `~/` (i.e., your home directory, aka `~`).
* Execute `cd cs51x` to change into that directory.
* In case if you haven't yet created folder for `pset1`, execute `mkdir pset1` to create `pset1` folder in your home directory.
* Execute `cd pset1` to change into (i.e., open) that directory.
* Execute `wget https://www.dropbox.com/s/r0qt7o4wx3lks8z/slowpayoff.zip` to download a (compressed) ZIP file with this problem’s distribution.
* Execute `unzip slowpayoff.zip` to uncompress that file.
* Execute `rm slowpayoff.zip` followed by `yes` or `y` to delete that ZIP file.
* Execute `ls`. You should see a directory called `slowpayoff`, which was inside of that ZIP file.
* Execute `cd slowpayoff` to change into that directory.
* Execute `ls`. You should see file `slowpayoff.py`.

## Hints

Start at `$10` payments per month and calculate whether the balance will be paid off (taking into account the interest accrued each month). If $10 monthly payments are insufficient to pay off the debt within a year, increase the monthly payment by $10 and repeat.

## Testing

Execute the below to evaluate the correctness of your code using `check50`. But be sure to compile and test it yourself as well!

```
check50 cs21x/problems/pset0/slowpayoff
```

Execute the below to evaluate the style of your code using style50.

```
style50 slowpayoff.py
```
