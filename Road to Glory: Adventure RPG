
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <vector>
#include <fstream>
#include <chrono>
#include <thread>
using namespace std;

/*
    created by
        1. arezyh.s
        2. shylniac
*/

// Player class.
class Player {
public:
    string name;
    int level;
    int exp;
    int health;
    int attack;
    int coins;
    int defense;

    Player(const string& n) : name(n), level(1), exp(0), health(100), attack(10), coins(0), defense(0) {}

    // Display player stats during gameplay.
    void displayStats() const {
        system("cls");
        cout << name << "'s stats" << endl;
        cout << "Level  : " << level << endl;
        cout << "Exp    : " << exp << "/100" << endl;
        cout << "Health : " << health << endl;
        cout << "Damage : " << attack << "\t Defence : " << defense << endl;
        cout << "Coins  : " << coins << endl;
    }

    // Load game feature to resume progress.
    void loadGame() {
        ifstream file("player_progress.txt");
        if (file.is_open()) {
            file >> level >> exp >> health >> attack >> coins;
            file.close();
            cout << "Game successfully loaded" << endl;
        } else {
            cout << "Failed to open game progress!" << endl;
        }
    }
};

// Enemy class. Feel free to create new enemies...
class Enemy {
public:
    string name;
    int health;
    int defense;
    int damage;
    int rewardCoins;
    int rewardExp;

    Enemy(const string& n, int h, int d, int dmg, int coins, int exp)
        : name(n), health(h), defense(d), damage(dmg), rewardCoins(coins), rewardExp(exp) {}

    virtual ~Enemy() {}

    virtual void displayIntro() const {
        cout << "Oh no! You encountered " << name << " on the road!" << endl;
    }

    virtual void attackPlayer(Player& player) const {
        player.health -= max(0, damage - player.defense); // Ensuring damage is not negative
        cout << name << " attacks you. You have " << player.health << " health remaining." << endl;
    }
};

class GoblinEnemy : public Enemy {
public:
    GoblinEnemy() : Enemy("Goblin", 80, 1, 12, 5, 10) {}
    void displayIntro() const override {
        cout << "Oh no! You encountered a small " << name << endl;
    }
};

class WizardEnemy : public Enemy {
public:
    WizardEnemy() : Enemy("Wizard", 70, 0, 18, 8, 15) {}
    void displayIntro() const override {
        cout << "Oh no! A powerful " << name << " stands before you!" << endl;
    }
};

class DarkKnightEnemy : public Enemy {
public:
    DarkKnightEnemy() : Enemy("Corrupted Knight", 90, 5, 20, 13, 17) {}
    void displayIntro() const override {
        cout << "You encounter " << name << "! He waits for you in the middle of the road..." << endl;
    }
};

class GiantEnemy : public Enemy {
public:
    GiantEnemy() : Enemy("Giant", 120, 2, 18, 15, 20) {}
    void displayIntro() const override {
        cout << "Your path is blocked by a " << name << " Giant" << endl;
    }
};

class FinalBossEnemy : public Enemy {
public:
    FinalBossEnemy() : Enemy("[BOSS] Dragon Lord", 500, 20, 30, 50, 100) {}
    void displayIntro() const override {
        cout << "You are at the final level. Level 10." << endl;
        cout << "In front of you, there is the last enemy you must face!" << endl;
        cout << "Dragon Lord!" << endl;
    }
};

// Function prototypes
void combat(Player& player, Enemy& enemy);

// Function to heal with coins
void heal(Player& player) {
    if (player.coins < 35) {
        cout << "You don't have enough coins!" << endl;
    } else {
        player.coins -= 35;
        player.health += 50;
        cout << "Health increased by 50!" << endl;
    }
    system("pause");
}

// Explore feature in the game and events that can occur while traveling.
void explore(Player& player) {
    system("cls");
    cout << "You continue your endless journey..." << endl;

    // Random events during gameplay.
    int randomEvent = rand() % 3;

    if (randomEvent == 0) {
        // Player finds coins
        player.coins += 5;
        cout << "Hooray! You found 5 coins during your journey!" << endl;
        system("pause");
    }
    else if (randomEvent == 1) {
        // Player encounters a trap!
        player.health -= 3;
        cout << "You fell into a pit!" << endl;
        cout << "Your health decreases by 3" << endl;
        system("pause");
    } else {
        // Player encounters an enemy
        int randomEnemyType = rand() % 5;
        Enemy* enemy;

        if (player.level != 10) { // If not at level 10, encounter a random regular enemy
            switch (randomEnemyType) {
                case 0:
                    enemy = new GoblinEnemy();
                    break;
                case 1:
                    enemy = new WizardEnemy();
                    break;
                case 2:
                    enemy = new GiantEnemy();
                    break;
                case 3:
                    enemy = new DarkKnightEnemy();
                    break;
                default:
                    enemy = new GoblinEnemy();
            }

            enemy->displayIntro();
            combat(player, *enemy);

            delete enemy;
        } else { // If at level 10, encounter the final boss
            enemy = new FinalBossEnemy();
            enemy->displayIntro();
            combat(player, *enemy);

            delete enemy;

            if (player.health > 0) {
                // Win condition
                system("pause");
                cout << "Congratulations! You have defeated the guardian of this road!" << endl;
                cout << "You have completed your journey!" << endl;
                cout << "Thank you for playing!" << endl;
                system("pause");
                exit(0);
            } else {
                // Lose condition
                cout << "You were defeated by the Final Boss!" << endl;
                cout << "GAME OVER" << endl;
                exit(0);
            }
        }
    }
}

// Function for combat against enemies
void combat(Player& player, Enemy& enemy) {
    while (player.health > 0 && enemy.health > 0) {
        // Player's turn
        cout << "1. Attack" << endl;
        cout << "2. Run" << endl;
        int choice;
        cout << ">> Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1: // Player attacks the encountered enemy
                enemy.health -= player.attack;
                cout << "You attack " << enemy.name << ". They have " << enemy.health << " health left!" << endl;
                break;
            case 2:
                // Option for the player to attempt escape, 50:50 chance
                if (rand() % 2 == 0) {
                    cout << "You successfully escaped from the enemy!" << endl;
                    return;
                } else {
                    cout << "You failed to escape from the enemy!" << endl;
                }
                break;
            default:
                cout << "Choose the appropriate option (1/2)" << endl;
        }

        // Enemy's turn
        if (enemy.health >= 0) {
            enemy.attackPlayer(player);
        }
    }

    if (player.health > 0) {
        cout << "You defeated " << enemy.name << "!" << endl;
        player.coins += enemy.rewardCoins;
        player.exp += enemy.rewardExp;

        if (player.exp >= 100) {
            player.level += 1;
            player.exp = 0;
            player.attack += 1;
        }

    } else {
        cout << "You were defeated by " << enemy.name << endl;
        cout << "GAME OVER" << endl;
        exit(0);
    }
}

// Function to save progress
void save(Player& player) {
    ofstream file("player_progress.txt");
    if (file.is_open()) {
        file << player.level << endl;
        file << player.exp << endl;
        file << player.health << endl;
        file << player.attack << endl;
        file << player.coins << endl;
        file.close();
        cout << "Your game progress has been saved!" << endl;
    } else {
        cout << "Failed to save your game progress!" << endl;
    }
    system("pause");
}

int main() {
    system("cls");
    srand(time(0));

    // Welcome message
    cout << "************************************" << endl;
    cout << "\t GAME ADVENTURE RPG" << endl;
    cout << "\t\t LEVEL 10" << endl;
    cout << "************************************" << endl;
    system("pause");

    // Enter character creation menu
    string playerName;
    cout << "Enter your character's name";
        // Enter character's name
    getline(cin, playerName);
    system("cls");

    Player player(playerName);

    // Choose character class
    int chooseRole;
    do {
        cout << "1. Warrior" << endl;
        cout << "2. Archer" << endl;
        cout << "3. Knight" << endl;
        cout << "Choose your character class (1/2/3): ";
        cin >> chooseRole;
    } while (chooseRole != 1 && chooseRole != 2 && chooseRole != 3);

    if (chooseRole == 1) { // Warrior
        player.health = 100;
        player.attack = 20;
        player.defense = 5;
        cout << "You chose Warrior" << endl;
        system("pause");
    } else if (chooseRole == 2) { // Archer
        player.health = 75;
        player.attack = 20;
        player.defense = 20;
        cout << "You chose Archer" << endl;
        system("pause");
    } else if (chooseRole == 3) { // Knight
        player.health = 150;
        player.attack = 25;
        player.defense = 10;
        cout << "You chose Knight" << endl;
        system("pause");
    }

    // Introduction message entering the game
    system("cls");
    cout << "\tINTRO" << endl;
    string intro = "You are a Traveler who is lost on the road...\nTo get out of here, you must defeat the guardians of this road. \nEnjoy the game!";
    for (char c : intro) {
        cout << c << flush;
        this_thread::sleep_for(50ms);
    }
    cout << endl;
    system("pause");

    // Game loop
    while (true) {
        system("cls");
        player.displayStats();

        // Game menu options
        cout << "1. Explore" << endl;
        cout << "2. Heal (35 coins)" << endl;
        cout << "3. Save" << endl;
        cout << "4. Load" << endl;
        cout << "5. Exit" << endl;
        int choice;
        cout << ">> Enter your choice (1/2/3/4/5): ";
        cin >> choice;

        switch (choice) {
            case 1:
                explore(player);
                break;
            case 2:
                heal(player);
                break;
            case 3:
                save(player);
                break;
            case 4:
                player.loadGame();
                break;
            case 5:
                cout << "Thank you for playing!" << endl;
                return 0;
            default:
                cout << "Choose the appropriate option (1/2/3/4/5)" << endl;
        }
    }
    return 0;
}










