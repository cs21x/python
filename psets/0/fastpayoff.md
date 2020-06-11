# Using Bisection Search to Make the Program Faster

## Getting Started
TODO

## Background

You'll notice that in the previous problem, your monthly payment had to be a multiple of $10. Why did we make it that way? In a separate file, you can try changing the code so that the payment can be any dollar and cent amount (in other words, the monthly payment is a multiple of $0.01). Does
your code still work? It should, but you may notice that your code runs more slowly, especially in cases with very large balances and interest rates.
How can we make this program faster? We can use bisection search! This will be covered in the next lecture but you can read more about bisection search [here](https://en.wikipedia.org/wiki/Bisection_method).

We are searching for the smallest monthly payment such that we can pay off the debt within a year. What is a reasonable lower bound for this value? We can say $0, but you can do better than that. If there was no interest, the debt can be paid off by monthly payments of one-twelfth of the original balance, so we must pay at least this much. One-twelfth of the original balance is a good lower bound.

What is a good upper bound? Imagine that instead of paying monthly, we paid off the entire balance at the end of the year. What we ultimately pay must be greater than what we would've paid in monthly installments, because the interest was compounded on the balance we didn't pay off each month. So a good upper bound would be one-twelfth of the balance, after having its interest compounded monthly for an entire year.

In short:

```
Monthly payment lower bound = Balance / 12.0 
Monthly payment upper bound = (Balance * (1 + (Annual interest rate / 12.0)) ** 12.0) / 12.0
```

## Specification

Write a program that uses these bounds and bisection search to find the smallest monthly payment to the cent (no more multiples of $10) such that we can pay off the debt within a year. Try it out with large inputs, and notice how fast it is. A sample run of the program should be as below.

```
$ python fastpay.py
Enter the outstanding balance on your credit card: 320000 
Enter the annual credit card interest rate as a decimal: .2 
RESULT 
Monthly payment to pay off debt in 1 year: 29643.05 
Number of months needed: 12 
Balance: -0.1
```

## Testing

Execute the below to evaluate the correctness of your code using `check50`. But be sure to test the code yourself as well!

```
check50 cs21x/problems/pset0/fastpayoff
```

Execute the below to evaluate the style of your code using style50.

```
style50 slowpayoff.py
```
