# Codealpha_HangmanGame

import random

# Condition 1: Small list of 5 predefined words

words = ["python", "intern", "coding", "laptop", "mobile"]

# Select Random word 
secret_word = random.choice(words)  # random used
guessed_letters = []  # list used
wrong_guesses = 0
max_wrong = 6  # Condition 2: Limit incorrect guesses to 6

print("=== Hangman Game ===")
print("Guess the word one letter at a time")
print("You can make 6 wrong guesses only\n")

# Condition: while loop used
while wrong_guesses < max_wrong:
    # String banane ke liye display word
    display_word = ""  # string used
    for letter in secret_word:  # string iteration
        # Condition: if-else used
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "
    
    # Condition 3: Basic console input/output
    print("Word:", display_word)
    print("Wrong guesses left:", max_wrong - wrong_guesses)
    
    # Win condition check
    if "_" not in display_word:
        print("\nYou won! The word was:", secret_word)
        break

    # User input
    guess = input("Enter a letter: ").lower()  # string method used

    # Input validation - if-else
    if len(guess) != 1 or not guess.isalpha():
        print("Enter only 1 letter\n")
        continue
    
    if guess in guessed_letters:
        print("Already guessed that letter\n")
        continue

    guessed_letters.append(guess)  # list method used

    # if-else for correct/wrong guess
    if guess in secret_word:
        print("Correct!\n")
    else:
        wrong_guesses += 1
        print("Wrong!\n")

# Game over condition
if wrong_guesses == max_wrong:
    print("Game Over! The word was:", secret_word)
