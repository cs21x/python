# Caesar Cipher

In this problem set you will need to devise your own algorithms and will practice using recursion to solve a non-trivial problem.

## Background

Encryption is the process of obscuring information to make it unreadable without special knowledge. For centuries, people have devised schemes to encrypt messages — some better than others — but the advent of the computer and the Internet revolutionized the field. These days, it's hard not to encounter some sort of encryption, whether you are buying something online or logging into Athena.  

A cipher is an algorithm for performing encryption (and the reverse, decryption). The original information is called __plaintext__. After it is encrypted, it is called __ciphertext__. The ciphertext message contains all the information of the plaintext message, but it's not in a format readable by a human or computer without the proper mechanism to decrypt it; it should resemble random gibberish to those not intended to read it.
A cipher usually depends on a piece of auxiliary information, called a key. The __key__ is incorporated into the encryption process; the same plaintext encrypted with two different keys should have two different ciphertexts. Without the key, it should be difficult to decrypt the resulting ciphertext into readable plaintext.  

This assignment will deal with a well-known (though not very secure) encryption method called the Caesar cipher. The basic idea in this cipher is that you pick an integer for a key, and shift every letter of your message by the key. For example, if your message was `hello` and your key was `2`, `h` becomes `j`, `e` becomes `g`, and so on. If you're interested in learning more about the Caesar cipher, check out the Wikipedia [article](https://en.wikipedia.org/wiki/Caesar_cipher).

In this problem set, we will use a variant of the standard Caesar cipher where the space character is included in the shifts: space is treated as the letter after `z`, so with a key of `2`, `y` would become `" "`, `z` would become `a`, and `" "` would become `b`.

## Getting Started

TODO

* ps4.py: the skeleton you'll fill in
* words.txt: a list of English words
* fable.txt: an encoded fable

Run the code without making any modifications to it, in order to ensure that everything is set up correctly. The code that we have given you loads a list of words from a file. If everything is okay, after a small delay, you should see the following printed out:

```
Loading word list from file...
55902 words loaded.
```

If you see an __IOError__ instead (e.g., No such file or directory), you should change the value of the `WORDLIST_FILENAME` constant (defined near the top of the file) to the complete pathname for the file words.txt (this will vary based on where you saved the file).
The file, `cipher.py`, has a few functions already implemented that you can use while writing up your solution. You can ignore the code between the following comments, though you should read and understand everything else.


## Encryption and Decryption

Write a program to encrypt plaintext into ciphertext using the Caesar cipher by implementing the below functions

* `build_coder(shift)`
* `build_encoder(shift)`
* `build_decoder(shift)`
* `apply_coder(text, coder)` 
* `apply_shift(text, shift)`

Sample runs of the functions are given below.

```
>>> build_coder(3)
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

```
>>> build_encoder(3)
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

```
>>> build_decoder(3)
{' ': 'x', 'A': 'Y', 'C': ' ', 'B': 'Z', 'E': 'B', 'D': 'A', 'G': 'D',
'F': 'C', 'I': 'F', 'H': 'E', 'K': 'H', 'J': 'G', 'M': 'J', 'L': 'I',
'O': 'L', 'N': 'K', 'Q': 'N', 'P': 'M', 'S': 'P', 'R': 'O', 'U': 'R',
'T': 'Q', 'W': 'T', 'V': 'S', 'Y': 'V', 'X': 'U', 'Z': 'W', 'a': 'y',
'c': ' ', 'b': 'z', 'e': 'b', 'd': 'a', 'g': 'd', 'f': 'c', 'i': 'f',
'h': 'e', 'k': 'h', 'j': 'g', 'm': 'j', 'l': 'i', 'o': 'l', 'n': 'k',
'q': 'n', 'p': 'm', 's': 'p', 'r': 'o', 'u': 'r', 't': 'q', 'w': 't',
'v': 's', 'y': 'v', 'x': 'u', 'z': 'w'}
```
(The order of the key-value pairs may be different.)

```
>>> apply_coder("Hello, world!", build_encoder(3))
'Khoor,czruog!'
>>> apply_coder("Khoor,czruog!", build_decoder(3))
'Hello, world!'
```

```
>>> apply_shift('This is a test.', 8)
'Apq hq hiham a.'
```


## Code-breaking

Your friend, who is also taking this course, is really excited about the program she wrote for the above problem. She sends you emails, but they're all encrypted with the Caesar cipher!

The problem is, you don't know which shift key she is using. The good news is, you know your friend only speaks and writes English words. So if you can write a program to find the decoding that produces the maximum number of words, you can probably find the right decoding (There's always a chance that the shift may not be unique. Accounting for this would probably use statistical methods that we won't require of you.)

Implement `find_best_shift`. This function takes a wordlist and a bit of encrypted text and attempts to find the shift that encoded the text. A simple indication of whether or not the correct shift has been found is if all the words obtained after a shift are valid words. Note that this only means that all the words obtained are actual words. It is possible to have a message that can be decoded by two separate shifts into different sets words. While there are various strategies for deciding between ambiguous decryptions, for this problem we are only looking for a simple solution.

To assist you in solving this problem, we have provided a helper function: `is_word(wordlist, word)`. This simply determines if word is a valid word according to wordlist. This function ignores capitalization and punctuation.

A sample run of the function is given below.

```
>>> s = apply_coder('Hello, world!', build_encoder(8))
>>> s
'Pmttw,hdwztl!'
>>> find_best_shift(wordlist, s) returns
8
>>> apply_coder(s, build_decoder(8)) returns
'Hello, world!'
```

### Hint
 You may find the function string.split to be useful for dividing the text up into words.

##  Multi-level Encryption & Decryption

Clearly the basic Caesar cipher is not terribly secure. To make things a little harder to crack, you will now implement a multi-level Caesar cipher. Instead of shifting the entire string by a single value, you will perform additional shifts at specified locations throughout the string. 

Implement `apply_shifts(text, shifts)` function that takes a string text and a list of tuples shifts. The tuples in shifts represent the location of the shift, and the shift itself. For example a tuple of `(0,2)` means that the shift starts are position `0` in the string and is a Caesar shift of `2`. Additionally, the shifts are layered. This means that a set of shifts `[(0,2), (5, 3)]` will first apply a Caesar shift of `2` to the entire string, and then apply a Caesar shift of `3` starting at the `6th` letter in the string.

A sample run of the function is given below.

```
>>> apply_shifts("Do Androids Dream of Electric Sheep?", [(0,6), (3, 18), (12, 16)])
'JufYkaolfapxQdrnzmasmRyrpfdvpmEurrb?'
```

##  Multi-level Code-breaking

Your friend has sent you another message, but this one can't be decrypted by your solution to the above problem — it must be using a multi-layer shift.

Implement function `find_best_shifts_rec(wordlist, text, start)`. To keep things from getting too complicated, we will add the restriction that a shift can begin only at the start of a word. This means that once you have found the correct shift at one location, it is guaranteed to remain correct at least until the next occurrence of a space character.

### Hint

To solve this problem successfully, we highly recommend that you use recursion. The non-recursive version of this function is much more difficult to understand and code. The key to getting the recursion correct is in understanding the seemingly unnecessary parameter "start". As always with recursion, you should begin by thinking about your base case, the simplest possible sub-problem you will need to solve. What value of start would make a good base case? (Hint: the answer is NOT zero.)

To help you test your code, we've given you two simple helper functions: 

`random_string(wordlist, n)` generates n random words from wordlist and returns them in a string.
`random_scrambled(wordlist, n)` generates n random words from wordlist and returns them in a string after encrypting them with a random multi-level Caesar shift. 

You can start by making sure your code decrypts a single word correctly, then move up to 2 and higher.  

__NOTE:__ This function depends on your implementation of `apply_shifts`.

## The Moral of the Story

Now that you have all the pieces to the puzzle, please use them to decode the file, `fable.txt`. At the bottom of the skeleton file, you will see a method `get_fable_string()` that will return the encrypted version of the fable.

