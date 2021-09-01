# GuessYourNumber

This logisim project consists of the implementation of machine that guesses numbers.  

You pick a number from 1 to 63, then answer 6 questions and the machine will show the number you thought of on the screen. The "questions" are basically 6 tables that contains a set of number: if you see your number, you select 'yes', otherwise, 'no'. After answering all questions your choice will be displayed on a double 7 segment display!

## How it works

The main concept behind the "guessing" is the following:

there are 6 tables, each one contains a specific set of numbers that in binary form contain a '1' at a certain position; for example the first one will contain only numbers that have a '1' at index 0 (1 [00000**1**], 3 [00001**1**], 5 [00010**1**] ...), the second one will contain numbers that have a '1' at index 1 and so on. If the player answers yes, the machine sets the bit at index *n* '1', otherwise '0', in this way it "builds" the chosen number.

### Components

- **DisplayWrapper**: this wrapping component is used to wrap the 2 TTYs and contains the *TTYLogic* component and the ROM that stores the sentences, question and tables;
- **TTYLogic**: as the name suggests, this is the logic that manges the TTYs, so it outputs the address for the ROM, signals when the header TTY, or the main one, should display something or reset its content;
- **7SegDriver**: this circuit it is used to handle the 7 Segment Driver;
- **BinToBCD**: Binary To Binary-Coded Decimal converter; as I need two 7 Seg. displays to display a 2 digit decimal number, I have to convert my 6-bit number in two 4-bit digits (ex. 12 [001100] -> 0001 [1], 0010 [2]);
- **Display**: another wrapping component, this one combines the *BinToBCD* and 2 *7SegDrivers* to show the final number on the double 7 Segment Display;
- **Thinker**: this component is the one that does the trick! When you press 'yes' or 'no' it stores the correct bit and then it shifts it to the right position during the process.

## Configuration

For the correct use of the game, you must set the Tick Frequency (Clock) to 128Hz-256Hz and zoom to 200%.

## How to play

1. Pick a number from 1 to 63
2. Click 'Start' to start the game
3. Answer the questions by clicking 'Y' or 'N'
4. If You want to play again, click 'Reset'

## Sample Image

![A sample image of the main game](./img/sample_img.png)
