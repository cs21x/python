# Hangman

For this problem, you will implement a variation of the classic wordgame Hangman. For those of you who are unfamiliar with the rules, you may read all about it [here](https://en.wikipedia.org/wiki/Hangman_(game)). In this problem, the second player will always be the computer, who will be picking a word at random.

## Getting Started

TODO

Implement a function, `hangman()`, that will start up and carry out an interactive Hangman game between a player and the computer.
For this problem, you will need the code files `hangman.py` and `words.txt`, which were included in the zip file. Make sure your file runs properly before editing. You should get the following output when running the unmodified version of hangman.py.

```
Loading word list from file...
55900 words loaded.
```

You will want to do all of your coding for this problem within this file as well because you will be writing a program that depends on each function you write.

## Specifications

* The computer must select a word at random from the list of available words that was provided in `words.txt`. The functions for loading the word list and selecting a random word have already been provided for you in `hangman.py`.

* The game must be interactive: it should let a player know how many letters the word the computer has picked contains and ask the user to supply guesses. The user should receive feedback immediately after each guess. You should also display to the user the partially guessed word so far, as well as either the letters that the player has already guessed or letters that the player has yet to guess.

* A player is allowed some number of guesses. Once you understand how the game works, pick a number that seems reasonable to you. Make sure to remind the player of how many guesses s/he has left after each turn.

* A player loses a guess only when s/he guesses incorrectly.

* The game should end when the player constructs the full word or runs out of guesses. If the player runs out of guesses (s/he "loses"), reveal the word to the player when the game ends.

An example game should look like this:

```
$ hangman.py
Welcome to the game, Hangman!
I am thinking of a word that is 4 letters long.
------------
You have 8 guesses left.
Available letters: abcdefghijklmnopqrstuvwxyz
Please guess a letter: a
Good guess: _a_ _ _
------------
You have 8 guesses left.
Available letters: bcdefghijklmnopqrstuvwxyz
Please guess a letter: s
Oops! That letter is not in my word: _a _ _
------------
You have 7 guesses left.
Available letters: bcdefghijklmnopqrtuvwxyz
Please guess a letter: t
Good guess: ta _t
------------
You have 7 guesses left.
Available letters: bcdefghijklmnopqruvwxyz
Please guess a letter: r
Oops! That letter is not in my word: ta _t
------------
You have 6 guesses left.
Available letters: bcdefghijklmnopquvwxyz
Please guess a letter: m
Oops! That letter is not in my word: ta _t
------------
You have 5 guesses left.
Available letters: bdefghijklmnopquvwxyz
Please guess a letter: c
Good guess: tact
------------
Congratulations, you won!
```

Do not be intimidated by this problem! It’s actually easier than it looks. Make sure you break down the problem into logical subtasks. What functions will you need to have in order for this game to work?

## Hints
* You should start by using the provided functions to load the words and pick a random one.
* Consider using string.lowercase.
* Consider writing helper functions. For instance, we found that creating functions to fill in guessed letters (generating strings like __ta_t__) and to display unused letters made partitioning the problem easier.