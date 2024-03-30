#include <iostream>
#include <string>
#include <vector>
#include <ctime>
#include <cstdlib>

using namespace std;

class GuessTheWordGame {
private:
    vector<string> words;
    string secretWord; 

public:
    GuessTheWordGame() {
        
        words = {"fruit", "soccer", "cooking", "headphones", "games"};

        srand(time(nullptr));

        secretWord = words[rand() % words.size()];
    }

    void play() {
        cout << "Welcome to Guess the Word Game!" << endl;
        cout << "Guess the word by entering one letter at a time." << endl;

        string guessedWord(secretWord.length(), '_');
        int attempts = 0;
        bool guessedCorrectly = false;

        while (attempts < 5) {
            cout << "Word: " << guessedWord << endl;
            char guess;
            cout << "Enter your guess: ";
            cin >> guess;

            bool correctGuess = false;
            for (int i = 0; i < secretWord.length(); ++i) {
                if (secretWord[i] == guess) {
                    guessedWord[i] = guess;
                    correctGuess = true;
                }
            }

            if (guessedWord == secretWord) {
                cout << "Congratulations! You guessed the word '" << secretWord << "'!" << endl;
                guessedCorrectly = true;
                break;
            }

            if (!correctGuess) {
                cout << "Incorrect guess. Try again." << endl;
                ++attempts;
                cout << "Attempts left: " << 5 - attempts << endl;
            }
        }

        if (!guessedCorrectly) {
            cout << "Sorry, you didn't guess the word. The word was '" << secretWord << "'." << endl;
        }
    }
};

int main() {
    GuessTheWordGame game;
    game.play();
    return 0;
} 

