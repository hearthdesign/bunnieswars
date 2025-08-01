# 🐰🐰🐰 BUNNIES-WARS 🐰🐰🐰

---

## Description:

As is often the case in life, 'the grass is greener on the other side of the fence'. In this case, the field belonging to your opponent, the PC-Bunny, is greener.

Try to find all the carrots that the PC-Bunny has planted: enter the coordinates (x, y) to check each position. In the meantime, the PC-Bunny has had a similar idea and is digging up the carrots that you planted.

The game ends when all the carrots have been found. Try to find them all! (before the PC-Bunny)!

---

## How to play:

- The game starts by idea of a battleship game. Since doesn´t need bombs or missiles, it is a more peaceful version of it. 

- Before the game starts, the player has the option of entering a name. If no name is entered, a default name will appear in the messages.

- The player can choose the size of the field by entering '1' (4x4), '2' (6x6) or '3' (8x8).

- In each field, a ratio of 1/4 of the total number of tiles will be hidden carrots.

- The player and the PC Bunny take turns to play.

- The player must enter two values: the first for the row and the second for the column.

- If a value has already been entered, is outside the field's range, or is not numeric, a message will prompt the player to enter a different value.

- The first person to find all the hidden carrots wins.

---

##       IPO flowchart

        ┌────────────────────────────┐
        │      Welcome Message       │
        └────────────┬───────────────┘
                     │
        ┌────────────▼───────────────┐
        │         Start Game         │
        └────────────┬───────────────┘
                     │
           ┌─────────▼─────────┐
           │     INPUT (I)     │
           ├───────────────────┤
           │• Choose board     │
           │   size (e.g. 5x5) │
           │• Place carrots    │
           └─────────┬─────────┘
                     │
           ┌─────────▼─────────┐
           │   PROCESSING (P)  │
           ├───────────────────┤
           │ • Initialize game │
           │ • Dig @ x,y coord.│
           │ • Check hits/miss │
           │ • Track scores    │
           │ • Switch turns    │
           │ • Check winner    │
           └─────────┬─────────┘
                     │
           ┌─────────▼─────────┐
           │     OUTPUT (O)    │
           ├───────────────────┤
           │ • Show board      │
           │ • Show result     │
           │ • Show winner     │
           └─────────┬─────────┘
                     │
              ┌──────▼──────┐
              │   END GAME  │
              └─────────────┘
---

## Features

Intro and small instruction

<img width="590" height="169" alt="Image" src="https://github.com/user-attachments/assets/0ef6ba9a-b912-4e44-8060-c9f94368389a" />

Personalized welcome message

<img width="447" height="30" alt="Image" src="https://github.com/user-attachments/assets/f5ff64ff-c66a-4dfa-99cd-7eb9d2774dfc" />


Possibility to set the field within three options.

<img width="278" height="169" alt="Image" src="https://github.com/user-attachments/assets/d43a41b9-512a-4278-aab3-fd050f777783" />

The generated field with coordinates for better readability

<img width="247" height="247" alt="Image" src="https://github.com/user-attachments/assets/a37f5e13-c0b4-479a-adc3-684577c68d67" />

Both fields and points

<img width="363" height="587" alt="Image" src="https://github.com/user-attachments/assets/55fa330d-cc2d-493f-88d1-a3f473faf727" />

Title with the player's name

<img width="464" height="197" alt="Image" src="https://github.com/user-attachments/assets/8cc16dbf-32e0-4486-804b-5284e26d79ba" />

win message

<img width="561" height="183" alt="Image" src="https://github.com/user-attachments/assets/b34410c6-624b-4f61-8a8d-2e61667ab4af" />

Lose Message

<img width="582" height="147" alt="Image" src="https://github.com/user-attachments/assets/f6226bcd-1c5c-4bda-b0b1-840a208894ce">

---

## Future features 

- Side by side view of the fields
- Dinamic writings to adapt to the screen and to variable names
- A score record in a database file
- Sounds

---

## Programming Overview

This project is designed with clean, modular code following the principles of Object-Oriented Programming (OOP).

### Design Notes
#### Classes and Objects:

The game uses custom classes to represent the game logic and field state.
No Player or PC class needed — the logic is handled directly in the Game class via its methods.

The Game class orchestrates both turns and field interactions.

Field is a self-contained entity that manages its own state (carrot locations, digs, etc.).

#### Encapsulation and Atomized Functionality

The game's architecture showcases strong encapsulation, with clearly defined responsibilities assigned to each component. Each class, such as 'Field' and 'Game', contains:

Private state management. Internal data, such as the carrot grid, dug positions or game settings, is managed within its respective class, shielding it from outside interference.

Modular, single-responsibility methods: The functions within each class are purpose-built and concise, making behaviour easy to follow and debug.

##### Some examples:

```python
def random_place_carrots(self):
    '''Randomly place carrots on the field.'''
    while len(self.carrots) < self.num_carrots:
        row = random.randint(0, self.size - 1)
        col = random.randint(0, self.size - 1)
        self.no_repeat_carrots(row, col)
```
- This function belongs to the Field class and is solely responsible for populating the grid with carrots—clean, atomic, and self-contained.

```python
def dig(self, row: int, col: int, silent=False):
    '''Dig at coordinates and check for carrots.'''
    # Validates input, updates grid, handles feedback
```
- Also part of Field, this method encapsulates the digging logic: validation, state update, and user messaging—all in one tidy unit.
  
```python
def setup_game(self):
    '''Get user input to configure field size and carrot count.'''
    # Repeated until valid choice is selected
```
- Found in the Game class, this function guides players through initial configuration while keeping the setup logic completely isolated.
  
```python
def player_turn(self, field):
    '''Executes player's digging attempt for a turn.'''
def pc_turn(self, field):
    '''Executes PC-Bunny’s automated digging turn.'''
def print_scores(self, player_score, pc_score):
    '''Displays current game scores.'''
```
- These Game class methods execute distinct actions while interacting with the Field class.
- Smooth inter-class interaction: by maintaining tight, purpose-specific interfaces, each component communicates with others while keeping the overall logic. 

### Testing

The game as been tested:
- on the PEP8 online validator.
- with the CI Python Lintner (Heroku App)
 
#### Fixes

The program has been rearranged since the beginning and some function was then appearing in inadequate positions leaving no space for the text and being difficult to read. There was also a double field for the computer-opponent (or PC-Bunny in the game).

The code has been restructured to leave sufficient space for readability and an intuintive understanding of the logic.

Screen and messages don´t appear duplicated after the fixes.

#### Still to be fixed

- No bug detected

#### In-Game Error Handling & Validation

Instead of a standalone test suite, Bunny Wars embeds input validation and edge-case handling directly into the gameplay flow. This provides real-time feedback and prevents disruptive behavior while keeping the game lean and responsive.

#### Some examples of Built-In Testing Logic

Input Validation in setup_game() The game ensures that players choose a valid grid size:
```python
try:
    choice = int(input("Enter choice (1-3): "))
    if choice in self.size_options:
        return self.size_options[choice]
``` 
Invalid selections trigger a helpful prompt without crashing the game:

```python
print("Invalid choice. Please enter 1, 2, or 3.")
```
Digging Logic in dig() Attempts to dig outside the grid or re-dig spots are gracefully handled:

```python
if not (0 <= row < self.size and 0 <= col < self.size):
    print('Oh, no! Invalid coordinates...')
    return False

if (row, col) in self.found:
    print('Already dug this spot...')
    return False
```
These checks act as live guardrails, helping ensure predictable behavior and preserving game integrity.

- Keeps the game intuitive for casual players
- Reduces setup complexity—no external testing framework needed
- Focuses on user experience and immediate feedback

### CLI Interface:

Played entirely from the command line, the game accepts input and displays output using standard Python terminal features.

## Credits:

Additionally to the great course at Code Institute, to write the code and get deeper in the pythonic universe I was reading mainly: 
 - "Invent your own computer games with Python" by Al Sweigart (No Starch Press - 2017)
 - "Expert Python Programming" by Michael Jaworkski and Tarek Ziadé (Packt - 2019)
 - "Python crash course" by Eric Matthes (Nostarch Press - 2023)

These Books have been very helpful to understand some mechanic and logic of the language.