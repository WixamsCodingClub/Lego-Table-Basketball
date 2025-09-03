# Lego Table Basketball

The Wixams Coding Club uses the [32-in-1 Wonder Building Kit from ElecFreaks](https://www.elecfreaks.com/micro-bit-wonder-building-kit-without-micro-bit-board.html) as a tool for learning programming on the BBC micro:bit. The Lego Table Basketball project started with the [Basketball Counter](https://elecfreaks.com/learn-en/microbitKit/Wonder_Building_Kit/Case_07.html) case from ElecFreaks.

![Image of the Basketball Counter project from ElecFreaks](/assets/ElecFreaks-32-in-1-Case-7-Basketball-Counter.png)

The project worked fine, so we decided to take things further and make a tabletop game with two basketball hoops (using two 32-in-1 kits), a scoreboard and some sounds. The Kitronik :VIEW text32 LCD screen is used for the scoreboard, displaying the game time and team scores.

![Image of the Kitronik :VIEW text32 LCD screen](/assets/Kitronik-View-Text32.png)

## Game Rules
TBC


## How it Works
This project comprises of 4 micro:bits connected together:
* 2 micro:bit for the basketball hoops
* 1 micro:bit for the scoreboard
* 1 micro:bit to play sounds

The scoreboard is the time keeper and manager for the game. When switched on the text32 LCD screen shows the the two teams with a score of 0 and the clock ready to start the countdown.

When switched on the two hoops display a score of 0 and are ready to start counting the number of baskets scored. Each is assigned a team name, 'A' or 'B'. When a player scores a basket the micro:bit displays the new score and sends it via Bluetooth to the scoreboard.


## Hoop micro:bit Requirements
* Know its own team name A or B.
* Detect when a ball has passed through the hoop.
* Play a sound or music when a basket is scored.
* Display how many baskets have been scored on the micro:bit's LED display.
* Send its team name and current score via Bluetooth when a ball is scored.


## Scoreboard micro:bit Requirements
* Display scores...
* Keep track of times
* 10 second countdown at the end of each quarter


## Music micro:bit Requirements
* Listen for trigger messages on Bluetooth.
* When the message *** is received it should play music to notify that a player scored a basket.
* When the message *** is received it should play music to indicate the quarter has finished.
* When the message *** is received it should play music to indicate the game has finished.

