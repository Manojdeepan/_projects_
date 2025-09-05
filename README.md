# Adventure RPG Game (C++)

![C++](https://img.shields.io/badge/C++-17-blue.svg)
![Console](https://img.shields.io/badge/Platform-Console-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-success.svg)

## Project Overview

A text-based Adventure RPG game developed in C++ where players embark on a journey through a dangerous world filled with enemies, traps, and treasures. The objective is to reach Level 10 and defeat the Final Boss to complete your journey.

## Features

- **Character System**: Choose from three unique classes (Warrior, Archer, Knight) with different stats
- **Combat System**: Turn-based combat against various enemy types
- **Progression System**: Gain experience, level up, and improve your character
- **Inventory Management**: Collect and use coins for healing
- **Save/Load System**: Persist your progress between sessions
- **Random Events**: Encounter coins, traps, and enemies during exploration
- **Final Boss Battle**: Epic confrontation with the Dragon Lord at level 10

## Character Classes

| Class   | Health | Attack | Defense | Description |
|---------|--------|--------|---------|-------------|
| Warrior | 100    | 15     | 5       | Balanced fighter with good health |
| Archer  | 75     | 20     | 10      | High damage, lower health |
| Knight  | 120    | 18     | 8       | Tanky character with high survivability |

## Enemies

- **Goblin**: Weak enemy, good for beginners
- **Wizard**: Medium difficulty with higher damage
- **Giant**: High health, moderate damage
- **Corrupted Knight**: Well-rounded enemy with good defense
- **Dragon Lord (BOSS)**: Final challenge with massive health and damage

## Installation & Compilation

### Requirements
- C++ compiler (g++, clang, or Visual Studio)
- Standard C++ libraries

### Compilation Instructions

```bash
# Using g++
g++ adventure_rpg.cpp -o adventure_rpg -std=c++17

# Using clang++
clang++ adventure_rpg.cpp -o adventure_rpg -std=c++17

# On Windows with Visual Studio
cl adventure_rpg.cpp
```

## How to Play

1. **Start the Game**: Run the compiled executable
2. **Create Character**: Enter your name and choose a class
3. **Explore**: Select "Explore" to journey through the world
4. **Combat**: Fight enemies using attack or try to escape
5. **Heal**: Use coins to restore health when needed
6. **Save Progress**: Regularly save your game to avoid losing progress
7. **Level Up**: Gain experience to increase your power
8. **Final Battle**: Reach level 10 to face the Dragon Lord

## Game Commands

During gameplay, you can choose from these options:

1. **Explore**: Continue your journey (may encounter events)
2. **Heal**: Restore 50 health for 35 coins
3. **Save**: Save your current progress
4. **Load**: Load previously saved progress
5. **Exit**: Quit the game

During combat:
1. **Attack**: Fight the enemy
2. **Run**: Attempt to escape (50% success chance)

## File Structure

```
Adventure_RPG/
├── adventure_rpg.cpp      # Main game source code
└── README.md              # Project documentation

```

## Game Mechanics

### Experience System
- Gain EXP from defeating enemies
- 100 EXP required to level up
- Each level increases attack, defense, and health

### Combat System
- Turn-based combat
- Damage calculation: max(0, attack - defense)
- Escape chance: 50% success rate

### Economy
- Coins found during exploration
- Coins used for healing (35 coins = 50 health)
- Coins rewarded from defeating enemies

### Saving System
- Progress saved to "player_progress.txt"
- Saves: level, EXP, health, attack, coins, defense

## Development Details

### Technologies Used
- Standard C++17
- Object-Oriented Programming
- File I/O for save system
- Random number generation for events

### Code Structure
- **Player Class**: Handles player stats and actions
- **Enemy Class Hierarchy**: Base class with specialized enemy types
- **Combat System**: Turn-based battle mechanics
- **Event System**: Random encounters during exploration

## Sample Gameplay

```
************************************
         GAME ADVENTURE RPG
                 LEVEL 10
************************************

Enter your character's name: Hero
Choose your character class:
1. Warrior (High health, moderate attack, low defense)
2. Archer (Low health, high defense and attack)
3. Knight (High health and attack, moderate defense)
Choose your character class (1/2/3): 1

You chose Warrior

Oh no! You encountered a small Goblin
1. Attack
2. Run
>> Enter your choice: 1
```

## Troubleshooting

### Common Issues
1. **Save file not found**: The game will create it automatically when you save
2. **Input errors**: Make sure to enter numbers for menu choices
3. **Compilation errors**: Ensure you have a C++17 compatible compiler

### Platform Notes
- Designed for console/terminal play
- Uses `system("cls")` for Windows - may need adjustment for other platforms
- Save file compatibility across different systems

## Future Enhancements

Potential improvements for the game:
- More enemy varieties and abilities
- Equipment and inventory system
- Special attacks and skills
- Multiple difficulty levels
- Graphical interface version
- Sound effects and music

## Author

**Manoj Deepan M**



**Enjoy your adventure! May your journey be successful and your battles victorious!**
