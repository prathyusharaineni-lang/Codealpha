import random
words = ["apple", "banana", "grape", "orange", "mango"]
word = random.choice(words)
guessed_letters = []
wrong_guesses = 0
max_wrong_guesses = 6
display_word = ["_"] * len(word)
print("Welcome to Hangman Game!")
while wrong_guesses < max_wrong_guesses and "_" in display_word:
    print("\nWord:", " ".join(display_word))
    print("Wrong guesses left:", max_wrong_guesses - wrong_guesses)
    guess = input("Enter a letter: ").lower()
    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue
    guessed_letters.append(guess)
    if guess in word:
        print("Correct guess!")
        for i in range(len(word)):
            if word[i] == guess:
                display_word[i] = guess
    else:
        print("Wrong guess!")
        wrong_guesses += 1
if "_" not in display_word:
    print("\nCongratulations! You guessed the word:", word)
else:
    print("\nGame Over! The word was:", word)
