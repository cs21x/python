# Problem Set 1

## Introduction

This problem set will introduce you to using control flow in Python and formulating a computational solution to a problem. 

## Paying Off Credit Card Debt

Each month, a credit card statement will come with the option for you to pay a minimum amount of your charge, usually 2% of the balance due. However, the credit card company earns money by charging interest on the balance that you don’t pay. So even if you pay credit card payments on time, interest is still accruing on the outstanding balance.

Say you’ve made a `$5,000` purchase on a credit card with `18%` annual interest rate and `2%` minimum monthly payment rate. After a year to calculate the remaining balance you can use the following equations.

**Minimum monthly payment** = Minimum monthly payment rate x Balance 

Remember, minimum monthly payment gets split into interest paid and principal paid.

**Interest paid** = Annual interest rate / 12 months x Balance 

**Principal paid** = Minimum monthly payment - Interest paid 

**Remaining balance** = Balance – Principal paid

For month 1, we can compute the minimum monthly payment by taking 2% of the balance:

**Minimum monthly payment** = .02 x $5000.0 = `$100.0`

We can’t simply deduct this from the balance because there is compounding interest. Of this $100 monthly payment, compute how much will go to paying off interest and how much will go to paying off the principal. Remember that it’s the annual interest rate that is given, so we need to divide it by 12 to get the monthly interest rate.

**Interest paid** = .18/12 x $5000.0 = `$75.0` 

**Principal paid** = $100.0 – $75.0 = `$25`

The remaining balance at the end of the first month will be the principal paid this month subtracted from the balance at the start of the month.

**Remaining balance** = $5000.0 – $25.0 = `$4975.0`

For month 2, we repeat the same steps:

**Minimum monthly payment** = .02 x $4975.0 = `$99.50`

**Interest paid** = .18/12 x $4975.0 = `$74.63`

**Principal paid** = $99.50 – $74.63 = `$24.87`

**Remaining Balance** = $4975.0 – $24.87 = `$4950.13`

After 12 months, the the total amount paid is `$1167.55`, leaving an outstanding balance of `$4708.10`. Pretty depressing!

## What to Do

1.  Submit [Paying the Minimum]({{ "/psets/1/minpay" | relative_url }})
2.  Submit [Paying Debt Off In a Year]({{ "/psets/1/payoff.md" | relative_url }})
3.  Submit [Using Bisection Search to Make the Program Faster]({{ "/psets/1/bisection" | relative_url }})
