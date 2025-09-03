# Lego Table Basketball

The Wixams Coding Club uses the [32-in-1 Wonder Building Kit from ElecFreaks](https://www.elecfreaks.com/micro-bit-wonder-building-kit-without-micro-bit-board.html) as a tool for learning programming on the BBC micro:bit. The Lego Table Basketball project started with the [Basketball Counter](https://elecfreaks.com/learn-en/microbitKit/Wonder_Building_Kit/Case_07.html) case from ElecFreaks.

![Image of the Basketball Counter project from ElecFreaks](/assets/ElecFreaks-32-in-1-Case-7-Basketball-Counter.png)

The project worked fine but was very basic, so we decided to take things further and make a tabletop game with two basketball hoops (using two 32-in-1 kits), a scoreboard and some sounds. The Kitronik :VIEW text32 LCD screen is used for the scoreboard, displaying the game time and team scores.

![Image of the Kitronik :VIEW text32 LCD screen](/assets/Kitronik-View-Text32.png)

## Game Rules
A game is very simple:
1. A game last 2 minutes.
2. Each player takes turns to throw the ball and score baskets in the opponents hoop.
3. At the end of the 2 minutes the player with the highest score wins.


## How it Works
This project comprises of 3 micro:bits connected together:
* 2 micro:bits for the basketball hoops
* 1 micro:bit for the scoreboard

The scoreboard is the time keeper and manager for the game. When switched on the text32 LCD screen shows the two teams with a score of 0 and the clock ready to start the countdown.

When switched on the hoops allow the user to set a team letter, A or B, for each side, they then display a score of 0 and are ready to start counting the number of baskets scored. 

To start a new game player presses the A button on the scoreboard's micro:bit. This starts the 2 minute countdown timer.

When a player scores a basket the micro:bit displays the new score and sends it via Bluetooth to the scoreboard. The scoreboard simply displays the new score.

At the end of a game the scoreboard displays "Game Over", the final scores and no longer accepts score updates from the hoops. The user must reset the scoreboard micro:bit to start a new game.

> [!NOTE]
> As the hoops display their own scores, they can function without a scoreboard, either as a single hoop or as 2 player game. When playing with the scoreboard, in case one or both of the hoops is already displaying a score when a game starts, the scoreboard micro:bit sends out a `RESET` command to set the hoop scores to 0.


## Hoop micro:bit Requirements
* When turned on, allows the user to select a team, A or B.
* Detects when a ball has passed through the hoop and increment the current score.
* Display how many baskets have been scored on the micro:bit's LED display.
* Send its team name and current score via Bluetooth when a ball is scored.
* Upon receiving the command `RESET` via Bluetooth, resets its own score.


## Scoreboard micro:bit Requirements
Before a game:
* Displays the initial game time (2 minutes).
* Displays the team scores, A and B, set to 0 points.
* Scrolls a prompt to the user on the micro:bit "Press A to start".
* When the A button is pressed a new game is started.

During a game:
* At the start of a new game a `RESET` command is sent via Bluetooth.
* Runs and displays a countdown timer.
* Receives new scores from a hoop via Bluetooth, including the team and the updated score.
* Displays the new score.
* At the end of the timer the game is ended.
* When the B button is pressed the game is ended early.

When a game ends:
* Displays "Game Over"
* Displays the final scores for both teams.
* No longer accepts score updates.
* Plays a tone to indicate the end of the game.