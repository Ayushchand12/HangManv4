# HangManv4
import random
#list of key words related to plastic pollution in oceans 
keywords = ("plastic","pollution","ocean","marine","environment","waste")
def draw_hangman(attempts):
    hangman_graphics = [
        """
          _______
         |       |
         |
         |
         |
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |
         |
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |       |
         |
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |      /|
         |
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |      /|\\
         |
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |      /|\\
         |      /
         |
        _|_
        """,
        """
          _______
         |       |
         |       O
         |      /|\\
         |      / \\
         |
        _|_
        """
    ]
    if attempts < len(hangman_graphics):
        print(hangman_graphics[attempts])
    else:
        print(hangman_graphics[-1])

def hangman_game():
    words = ["plastic", "pollution", "ocean", "marine", "environment", "waste"]
    word_to_guess = random.choice(words)
    guessed_letters = []
    attempts_left = 8
    correct_guesses = 0

    print("Welcome to the Plastic Pollution Hangman Game!")
    print("Guess the letters to uncover the word related to plastic pollution in the oceans.")

    while attempts_left > 0 and correct_guesses < len(word_to_guess):
        print("\nWord:", end=" ")
        for letter in word_to_guess:
            if letter in guessed_letters:
                print(letter, end=" ")
            else:
                print("_", end=" ")

        guess = input("\nGuess a letter: ").lower()

        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word_to_guess:
            correct_guesses += word_to_guess.count(guess)
        else:
            attempts_left -= 1
            draw_hangman(8 - attempts_left)

        print("Attempts left:", attempts_left)

    if correct_guesses == len(word_to_guess):
        print("\nCongratulations! You've uncovered the word:", word_to_guess)
    else:
        print("\nGame over! The word was:", word_to_guess)
        draw_hangman(7)

    play_again = input("Do you want to play again? (yes/no): ").lower()
    if play_again == "yes":
        hangman_game()
    else:
        print("Thank you for playing!")

hangman_game()
