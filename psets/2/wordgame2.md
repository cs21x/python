# Multiplayer Word Game

In this problem set, you decide to teach your computer to play the game you just built so that you can prove once and for all that computers are inferior to human intellect. 

## Getting Started

TODO

## Computer Word Choose

First we must create a function that allows the computer to choose a word.
We have provided the function `get_perms(hand, n)` (defined in `perm.py`, but usable by simply calling `get_perms(hand, n)`). 

`get_perms(hand, n)` takes in the current `hand` and a number which must be less than or equal to the size of the `hand`. It returns all possible permutations of size n given the letters in the `hand`.

You are not required to know how get_perms works. It is your responsibility to create the function `comp_choose_word(hand, word_list)` which given a `hand` and a `word_list`, find a valid `word`, and return it.

## Computer's turn to play a hand

Now you need to write a function similar to `play_hand` written for the single player word game.
Implement the `comp_play_hand` function according to the below specification. This function should allow the computer to play the game through completion.

* The `hand` is displayed.
* The computer chooses a word.
* After every valid word: the score for that word is displayed,
the remaining letters in the `hand` are displayed, and the computer
chooses another word.
* The sum of the word scores is displayed when the `hand` finishes.
* The `hand` finishes when the computer has exhausted its possible
choices (i.e. `comp_play_hand` returns None).

## You & Your Computer

Now that your computer can choose a word, you need to give the computer the option to play.

Write the code that re-implements the `play_game` function according to the below specification.

As before, you should use the `HAND_SIZE` constant to determine the number of cards in a hand. If you like, you can try out different values for `HAND_SIZE` with your program.

* Asks the user to input `n` or `r` or `e`.
    * If the user inputs `n`, play a new (random) hand.
    * If the user inputs `r`, play the last hand again.
    * If the user inputs `e`, exit the game.
    * If the user inputs anything else, ask them again.
* Ask the user to input a `u` or a `c`.
    * If the user inputs `u`, let the user play the game as before using `play_hand`.
    * If the user inputs `c`, let the computer play the game using `comp_play_hand`.
    * If the user inputs anything else, ask them again.
* After the computer or user has played the hand, repeat from step 1





