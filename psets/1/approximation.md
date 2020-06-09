# Successive approximation

Successive approximation is a problem-solving method where you try to guess the right answer to a problem and then check your guess. If the guess is good enough, you're done. Otherwise, you keep improving your guess in small increments and checking it, getting closer and closer to the right answer, until you determine that the guess is good enough. For the first 3 problems of this problem set, we will look at Newton's method, which uses successive approximation to find the roots of a function.

## Getting Started

TODO

## Polynomials

For this problem set, we will be representing polynomials as tuples. The index of a number in the tuple represents the power, and the value at that index represents the coefficient for that term. 

So for example, the polynomial __x<sup>4</sup> + 3x<sup>3</sup> + 17.5x<sup>2</sup> – 13.39__ would be represented by the tuple __(-13.39, 0.0, 17.5, 3.0, 1.0)__. This is because the tuple represents __-13.39x<sup>0</sup> + 0.0x<sup>1</sup> + 17.5x<sup>2</sup> + 3.0x<sup>3</sup> + 1.0x<sup>4</sup>__, which is the same as __x<sup>4</sup> + 3x<sup>3</sup> + 17.5x<sup>2</sup> – 13.39__

Implement the `evaluate_poly` function. This function evaluates a polynomial function for the given x value. It takes in a tuple of numbers poly and a number x. By number, we mean that x and each element of poly is a float. `evaluate_poly` takes the polynomial represented by poly and computes its value at x. It returns this value as a float.

## Derivatives

As stated before, we will need to find f'(x<sub>n</sub>), where f'(x) is the derivative of f(x). Recall that the derivative of a polynomial f(x) = ax<sup>b</sup> is f'(x) = abx<sup>b - 1</sup>, unless b = 0, in which case f'(x) = 0. To compute the derivative of a polynomial function with many terms, you just do the same thing to every term individually. For example, if __f(x) = x<sup>4</sup> + 3x<sup>3</sup> + 17.5x<sup>2</sup> – 13.39__, then __f'(x) = 4x<sup>3</sup> + 9x<sup>2</sup> + 35x__.

Implement the `compute_deriv` function. This function computes the derivative of a polynomial function. It takes in a tuple of numbers poly and returns the derivative, which is also a polynomial represented by a tuple.

## Newton’s Method

Newton’s method (also known as the Newton-Raphson method) is a successive approximation method for finding the roots of a function. Recall that the roots of a function f(x) are the values of x such that f(x) = 0. You can read more about Newton’s method [here](https://en.wikipedia.org/wiki/Newton%27s_method).

Here is how Newton’s method works:

1. We guess some x<sub>0</sub>.
2. We check to see if it's a root or close enough to a root by calculating f(x<sub>0</sub>). If f(x<sub>0</sub>) is within some small value epsilon of 0, we say that's good enough and call x<sub>0</sub> a root.
3. If f(x<sub>0</sub>) is not good enough, we need to come up with a better guess, x<sub>1</sub>. x<sub>1</sub> is calculated by the equation: x<sub>1</sub> = x<sub>0</sub> - f(x<sub>0</sub>) / f'(x<sub>0</sub>).
4. We check to see if x<sub>1</sub> is close enough to a root. If it is not, we make a better guess x<sub>2</sub> and check that. And so on and so on. For every x<sub>n</sub> that is not close enough to a root, we replace it with x<sub>n+1</sub> = x<sub>n</sub> - f(x<sub>n</sub>) / f'(x<sub>n</sub>) and check if that’s close enough to a root. We repeat until we finally find a value close to a root.

For simplicity, we will only be using polynomial functions in this problem set.

Implement the `compute_root` function. This function applies Newton's method of successive approximation as described above to find a root of the polynomial function. 

It takes in a tuple of numbers poly, an initial guess x_0, and an error bound epsilon. 

It returns a tuple. The first element is the root of the polynomial represented by poly; the second element is the number of iterations it took to get to that root.

The function starts at x_0. It then applies Newton's method. It ends when it finds a root x such that the absolute value of f(x) is less than epsilon, i.e. f(x) is close enough to zero. It returns the root it found as a float.


