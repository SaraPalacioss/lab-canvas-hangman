![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | Canvas Hangman

## Introduction

In this exercise, we are going to create the classic game [Hangman](<https://en.wikipedia.org/wiki/Hangman_(game)>). How to play this game, what are the rules? Just in case you don't know, in this game, we have to figure out a secret word by guessing one letter at a time. However, with each error, the man will get one step closer to death! The goal is to successfully guess the word before the man gets hanged.

![](https://i.imgur.com/wrQrY1T.png)

As we have learned, we can't confront the whole game without splitting it up into smaller steps. We will split it up into three different parts: structure, logic, and game layout. This technique is known as **incremental build.**

We will separate the game logic from the iteration with the `canvas`. We should be able to play from the console first and then add the graphics.

## Requirements

- Fork this repo
- Clone this repo

## Submission

Upon completion, run the following commands:

```
$ git add .
$ git commit -m "done"
$ git push origin master
```

Create Pull Request so your TAs can check up your work.

## Tests!

In order to do the game logic, we add some **Jasmine** tests to help you. Open the `SpecRunner.html` to check them.

## Instructions

### Iteration 1: The game logic

In the `hangman.js` file, create Hangman class and its methods as described below.

#### Hangman Class

First of at all, let's create our Hangman class. It should have the following properties:

- **words** - an `array` where we will store all the words that a player needs to guess. Every time a new game starts, a random word from this array needs to be picked as the secret word to be guessed by the player.
- **secretWord** - here we will store the word that has been picked as a secret word for the current game.
- **letters** - an `array` in which we will store the letters that the user has already picked while trying to guess the secret word. It is important to keep the track of these letters so we can, later on, apply some logic to prevent users from repeating them.
- **guessedLetter** - a `string` to store the _letters_ user chose and guessed. We will use this to know when the user wins.
- **errorsLeft** - the initial/start value should be 10, and decrease every time a user picks a letter that doesn't appear in the word.

#### The Hangman methods

- `getWord()` - a method that returns a random word from the array of `words`.
- `checkIfLetter(keyCode)` - a method that should return true or false depending if the key the user pressed has a value of any letter between `a-z` and `A-Z`. In case the key doesn't corresponds with any of the letters, but instead has a value of some special character or a number, this method should return false.
- `checkClickedLetters(letter)` - a method that should check if the currently picked letter has already been chosen. It should return true if it was not or false in the opposite case.
- `checkGameOver()` - a method that checks if the user has any errors left. If the number of errors is greater than 0, the method should return false (the game continues). In opposite case, if there is no more errors left, the method should return true.
- `checkWinner()` - a method that should check if the user won and return the corresponding boolean value.
- `addCorrectLetter(index)` - a method that should add the passed letter to the `guessedLetter` variable. This could be a good place to check if the user won.
- `addWrongLetter(letter)` - a method that should subtract one from the variable `errorsLeft`. It also should push this letter in the array of letters if the letter is not there already.

### Iteration 2: Draw in Canvas

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_3e1e1919b29ba77e77cdcec2ed7b92c5.png)

Now we need to start drawing the hangman in order to finish our game! As we said, we will do it in a different file separating it from the logic.

#### HangmanCanvas class

In the `canvas.js` file, you can see `HangmanCanvas` class and it should have the following properties:

- **context/ctx** - the canvas context has been already captured in its property `this.ctx`.
- **secretWord** - the _HangmanCanvas_ class should know which random secret word has been chosen. This is actually super doable since it receives this word as an argument, as we can see in its constructor.

#### The HangmanCanvas methods

- **createBoard()** - the method that should clear the `canvas`, so every time we start the game we have a clean one. This method also should call the next one we will define, the _drawLines()_.
- **drawLines()** - the method that should draw one line for each letter of the secret word. At this point we know the secret word the user has to guess.
- **writeCorrectLetter(index)** and **writeWrongLetter(letter, errorsLeft)** - the methods that should write the letter on which the user has just clicked, on the appropriate part of the canvas. After checking if the letter was not already clicked, we should write it on our board. If the secret word includes the letter, we should write it in the position where it belongs, and if the letter is not included in the secret word, we should write it on the top right corner, so that the user knows which letters were already clicked.
- **drawHangman(errorsLeft)** - the method that should draw **THE HANGMAN**. You'll see that the drawing is composed of multiple lines and one circle. Go ahead and experiment, you'll see it's pretty straightforward. :wink:

### Bonus

Your game is finished! Anybody can play it, but we need to show them something when they win or lose, so go ahead and create two additional methods **`gameOver()`** and **`winner()`**, to display the images available in the `images` folder.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_1dc0d7772d204da800d078c153c12e47.png)

Happy coding! :heart:
