Tic Tac Toe: Chaos, Battles & Dungeon Campaign
A command-line Tic Tac Toe game that goes far beyond the classic. Play a standard match with random board-shaking events, duel a friend using class-based special moves, or fight through a dungeon of monsters (and a dragon) where every round is a game of Tic Tac Toe.

Table of Contents:

Overview
Features
Demo
Installation and Usage
How to Play
Game Details
Reflections
Next Steps
Contributors
License
Overview

Everyone knows Tic Tac Toe, and everyone knows how it ends: a tie. This project asks what happens when you add surprises, special abilities, and a boss fight. The result is three game modes in one program, all played in the terminal:

Normal Game: 
classic two-player Tic Tac Toe, with a small chance of chaos on every move.
Battle Mode: 
pick a custom symbol and a class (Paladin or Alchemist) and use special moves to outsmart your opponent.
Campaign Mode:
create a hero, fight five enemies, grab upgrades along the way, and try to defeat the Dragon.
Features
Three distinct game modes with a replayable main menu
Random board events: earthquakes, snake attacks, and lucky landings
Two playable archetypes with unique special moves
Custom player symbols (letters and select punctuation)
RPG-style campaign with stats (health, attack, defense), five enemies, and unique enemy abilities
Branching path choices and an in-game shop
Input validation to handle invalid moves and menu choices
Built-in assertion tests for win detection, tie detection, and adjacency logic

Tech:

C++ (standard library only: iostream, vector, cassert)

Git Actions for CI (test, build)

Vitest (unit testing)

Tailwind CSS (styling)

1 | 2 | 3
---------
4 | X | 6
---------
O | 8 | 9

A mid-game board in Normal mode. Empty slots show their number.

Installation and Usage

Requirements: 
a C++ compiler such as g++ or clang++.

bash
# Clone the repository
git clone <your-repo-url>
cd <your-repo-folder>

# Compile (replace main.cpp with your file name)
g++ -std=c++11 main.cpp -o tictactoe

# Run
./tictactoe

On Windows, run tictactoe.exe instead.

How to Play

On launch, the game runs its built-in tests, then shows the main menu:

-----TIC TAC TOE-----
Select Game Mode:
1. Normal Game
2. Battle Mode
3. Campaign Mode

Enter a number from 1 to 9 to place your mark in that slot. Get three in a row to win.

Game Details
Normal Game

Two players enter their names and take turns as X and O. After each move there is a 20% chance that a random event triggers:

Event	Effect
Earthquake	Two random slots on the board swap contents
Snake attack	A random placed mark is destroyed
Lucky landing	A free slot is filled with the current player's mark
Battle Mode

Each player picks a symbol and an archetype. On your turn, choose a regular move or a special move.

Archetype	Special Move
Paladin	Move one of your pieces to an adjacent empty slot
Alchemist	Swap the positions of two pieces already on the board
Campaign Mode

Create a hero and fight through five enemies. Each battle is a series of Tic Tac Toe rounds: win a round to damage the enemy, lose one and the enemy damages you. Damage is the attacker's attack minus the defender's defense. Ties deal no damage.

Hero	Health	Attack	Defense
Paladin	250	50	20
Alchemist	250	30	50
Enemy	Health	Attack	Defense	Special Ability
Goblin	100	30	30	20% chance to dodge
Orc	100	30	30	25% chance to go berserk (double attack)
Giant	100	30	30	15% chance to crush (+20 attack)
Necromancer	200	50	35	30% chance to heal 15 HP
Dragon (final boss)	300	40	40	Fire breath, scale armor, or wing flap

Between fights you choose a path for a stat boost and can visit the shop (each item costs 10 coins) for attack, health, or defense potions.

Reflections:

Reusing one game engine. The same win-check and board logic powers all three modes. Campaign Mode simply wraps it in a battle loop with an AI opponent that picks random open slots.
Making Tic Tac Toe less predictable. Random events and special moves were added to break the "always a tie" problem. Tuning the probabilities so chaos feels fun rather than unfair took trial and error.
Testing the core logic. Assertion tests cover win detection across rows, columns, and diagonals, tie detection, and the adjacency rules used by the Paladin.
Next Steps
Seed the random number generator (srand) so events and enemy moves differ between runs
Smarter enemy AI instead of random slot selection
Split the code into multiple files (game logic, battle system, UI)
Add more archetypes, enemies, and campaign paths
Add a save system and score tracking
