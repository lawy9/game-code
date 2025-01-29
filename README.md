import random

def guessing_game():
    """A simple number guessing game."""

    secret_number = random.randint(1, 10)
    print("I've chosen a number between 1 and 10. Can you guess it?")

    attempts = 0
    while True:
        attempts += 1
        while True:  # Input validation loop
            try:
                guess = input("Enter your guess: ")
                if guess.isdigit():
                    guess = int(guess)
                    break
                else:
                    print("Invalid input. Please enter a number.")
            except ValueError:  #Handles potential errors if the user enters a non-integer value
                print("Invalid input. Please enter a number.")

        if guess < secret_number:
            print("Too low! Try again.")
        elif guess > secret_number:
            print("Too high! Try again.")
        else:
            print("Congratulations! You guessed the number.")
            print(f"It took you {attempts} attempts.")
            break

    play_again = input("Do you want to play again? (yes/no): ").lower()
    return play_again == "yes"


if __name__ == "__main__":
    while True:
        if not guessing_game():
            break
    print("Thanks for playing!")
