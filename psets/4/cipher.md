# Introduction

Encryption is the process of obscuring information to make it unreadable without special knowledge. For centuries, people have devised schemes to encrypt messages — some better than others — but the advent of the computer and the Internet revolutionized the field. These days, it’s hard not to encounter some sort of encryption, whether you are buying something online or logging into Athena.  

A cipher is an algorithm for performing encryption (and the reverse, decryption). The original information is called plaintext. After it is encrypted, it is called ciphertext. The ciphertext message contains all the information of the plaintext message, but it’s not in a format readable by a human or computer without the proper mechanism to decrypt it; it should resemble random gibberish to those not intended to read it.
A cipher usually depends on a piece of auxiliary information, called a key. The key is incorporated into the encryption process; the same plaintext encrypted with two different keys should have two different ciphertexts. Without the key, it should be difficult to decrypt the resulting ciphertext into readable plaintext.  

This assignment will deal with a well-known (though not very secure) encryption method called the Caesar cipher. In this problem set you will need to devise your own algorithms and will practice using recursion to solve a non-trivial problem.

## Caesar Cipher

In this problem set, we will examine the Caesar cipher. The basic idea in this cipher is that you pick an integer for a key, and shift every letter of your message by the key. For example, if your message was __"hello"__ and your key was __2__, __"h"__ becomes __"j"__, __"e"__ becomes __"g"__, and so on. If you're interested in learning more about the Caesar cipher, check out the Wikipedia article.

In this problem set, we will use a variant of the standard Caesar cipher where the space character is included in the shifts: space is treated as the letter after __"z"__, so with a key of 2, __"y"__ would become " ", __"z"__ would become __"a"__, and " " would become __"b"__.

## Getting Started

* ps4.py: the skeleton you’ll fill in
* words.txt: a list of English words
* fable.txt: an encoded fable

Run the code without making any modifications to it, in order to ensure that everything is set up correctly. The code that we have given you loads a list of words from a file. If everything is okay, after a small delay, you should see the following printed out:

```
Loading word list from file...
55902 words loaded.
```

If you see an IOError instead (e.g., No such file or directory), you should change the value of the WORDLIST_FILENAME constant (defined near the top of the file) to the complete pathname for the file words.txt (this will vary based on where you saved the file).
The file, ps4.py, has a few functions already implemented that you can use while writing up your solution. You can ignore the code between the following comments, though you should read and understand everything else.


## Problem 1. Encryption and Decryption


Write a program to encrypt plaintext into ciphertext using the Caesar cipher.

```
Example: >>> build_coder(3)
{' ': 'c', 'A': 'D', 'C': 'F', 'B': 'E', 'E': 'H', 'D': 'G', 'G': 'J',
'F': 'I', 'I': 'L', 'H': 'K', 'K': 'N', 'J': 'M', 'M': 'P', 'L': 'O',
'O': 'R', 'N': 'Q', 'Q': 'T', 'P': 'S', 'S': 'V', 'R': 'U', 'U': 'X',
'T': 'W', 'W': 'Z', 'V': 'Y', 'Y': 'A', 'X': ' ', 'Z': 'B', 'a': 'd',
'c': 'f', 'b': 'e', 'e': 'h', 'd': 'g', 'g': 'j', 'f': 'i', 'i': 'l',
'h': 'k', 'k': 'n', 'j': 'm', 'm': 'p', 'l': 'o', 'o': 'r', 'n': 'q',
'q': 't', 'p': 's', 's': 'v', 'r': 'u', 'u': 'x', 't': 'w', 'w': 'z',
'v': 'y', 'y': 'a', 'x': ' ', 'z': 'b'}
```
(The order of the key-value pairs may be different.)


## Problem 2. Code-breaking

Your friend, who is also taking 6.00, is really excited about the program she wrote for Problem 1 of this problem set. She sends you emails, but they’re all encrypted with the Caesar cipher!
The problem is, you don’t know which shift key she is using. The good news is, you know your friend only speaks and writes English words. So if you can write a program to find the decoding that produces the maximum number of words, you can probably find the right decoding (There’s always a chance that the shift may not be unique. Accounting for this would probably use statistical methods that we won’t require of you.)

##  Problem 3. Multi-level Encryption & Decryption

Clearly the basic Caesar cipher is not terribly secure. To make things a little harder to crack, you will now implement a multi-level Caesar cipher. Instead of shifting the entire string by a single value, you will perform additional shifts at specified locations throughout the string. This function takes a string text and a list of tuples shifts. The tuples in shifts represent the location of the shift, and the shift itself. For example a tuple of (0,2) means that the shift starts are position 0 in the string and is a Caesar shift of 2. Additionally, the shifts are layered. This means that a set of shifts [(0,2), (5, 3)] will first apply a Caesar shift of 2 to the entire string, and then apply a Caesar shift of 3 starting at the 6th letter in the string.

##  Problem 4. Multi-level Code-breaking

Your friend has sent you another message, but this one can’t be decrypted by your solution to Problem 2 — it must be using a multi-layer shift.
To keep things from getting too complicated, we will add the restriction that a shift can begin only at the start of a word. This means that once you have found the correct shift at one location, it is guaranteed to remain correct at least until the next occurrence of a space character.

### Advice
To solve this problem successfully, we highly recommend that you use recursion (did we say use recursion again?). The non-recursive version of this function is much more difficult to understand and code. The key to getting the recursion correct is in understanding the seemingly unnecessary parameter "start". As always with recursion, you should begin by thinking about your base case, the simplest possible sub-problem you will need to solve. What value of start would make a good base case? (Hint: the answer is NOT zero.)
To help you test your code, we’ve given you two simple helper functions: random_string(wordlist, n) generates n random words from wordlist and returns them in a string.

random_scrambled(wordlist, n) generates n random words from wordlist and returns them in a string after encrypting them with a random multi-level Caesar shift. You can start by making sure your code decrypts a single word correctly, then move up to 2 and higher.  

__NOTE:__ This function depends on your implementation of `apply_shifts`, so it will not work correctly until you have completed `Problem 3`.

## Problem 5. The Moral of the Story

Now that you have all the pieces to the puzzle, please use them to decode the file, fable.txt. At the bottom of the skeleton file, you will see a method `get_fable_string()` that will return the encrypted version of the fable. Create the following method and include as a comment at the end of the problem set how the fable relates to your education at MIT.

