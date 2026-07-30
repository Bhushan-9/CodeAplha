# CodeAplha
internship
import random

words = ["python", "coding", "alpha", "script", "lambda"]

def play_hangman():
    secret_word = random.choice(words)
    guessed_letters = []
    attempts = 6

    print("--- WELCOME TO HANGMAN GAME ---")
    print(f"Guess the word! You have {attempts} incorrect attempts allowed.\n")

    while attempts > 0:
        display_word = ""
        for letter in secret_word:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "
        
        print("Word: ", display_word.strip())
        print(f"Guessed letters: {', '.join(guessed_letters)}")
        print(f"Remaining attempts: {attempts}")

        if "_" not in display_word:
            print("\nCongratulations! You guessed the word correctly! 🎉")
            break

        guess = input("Enter a single letter: ").lower().strip()

        if len(guess) != 1 or not guess.isalpha():
            print("Invalid input! Please enter a single alphabetical letter.\n")
            continue
        
        if guess in guessed_letters:
            print("You already guessed that letter. Try another one!\n")
            continue

        guessed_letters.append(guess)

        if guess in secret_word:
            print(f"Good job! '{guess}' is in the word.\n")
        else:
            attempts -= 1
            print(f"Oops! '{guess}' is not in the word.\n")

    if attempts == 0:
        print(f"\nGame Over! You ran out of attempts. The word was: '{secret_word}'")

if __name__ == "__main__":
    play_hangman()s
