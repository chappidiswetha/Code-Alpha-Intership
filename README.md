✨Code-Alpha-Intership✨
  I am currently doing my 3-month internship at Code Alpha, where I am building Python projects to strengthen my programming skills. 
TASK 1: Hangman Game
Goal: Create a text-based Hangman game where the player guesses a word one letter at a time.
Simplified Scope:
Use a small list of 5 predefined words (no file or API).
Limit incorrect guesses to 6.
Basic console input/output (no graphics/audio).
Key Concepts Used: random, while loop, if-else, strings, lists
Code:
import random
words = ["python","hangman","random","string","loops"]
word = random.choice(words)
guessed = ["_"] * len(word)  
attempts_left = 6
guessed_letters = []
print("Welcome to Hangman!")
print("Guess the word: ", " ".join(guessed))
while attempts_left > 0 and "_" in guessed:
    guess = input("\nEnter a letter: ").lower()
    if len(guess) != 1 or not guess.isalpha():
        print("Please enter a single valid letter.")
        continue
    if guess in guessed_letters:
        print("You already guessed that letter. Try again.")
        continue
    guessed_letters.append(guess)
    if guess in word:
        print("Good guess!")
        for i in range(len(word)):
            if word[i] == guess:
                guessed[i] = guess
    else:
        attempts_left -= 1
        print(f"Wrong guess! Attempts left: {attempts_left}")

    print("Word: ", " ".join(guessed))
    print("Guessed letters:", " ".join(guessed_letters))
if "_" not in guessed:
    print("Congratulations! You guessed the word:", word)
else:
    print("Game Over! The word was:", word)

TASK 2: Stock Portfolio Tracker
Goal: Build a simple stock tracker that calculates total investment based on manually defined stock prices.
Simplified Scope:
User inputs stock names and quantity.
Use a hardcoded dictionary to define stock prices (e.g., "AAPL": 188, "TSLA":250).
Display total investment value.
Optionally save results in a.txt or .csv file.
Code:
stock_prices = {
    "AAPL": 188,
    "TSLA": 250,
    "GOOG": 2800,
    "AMZN": 135,
    "MSFT": 330
}
portfolio = {}
total_investment = 0
print("Welcome to Stock Portfolio Tracker!")
print("Available stocks:", ", ".join(stock_prices.keys()))
while True:
    stock = input("\nEnter stock symbol (or 'done' to finish): ").upper()
    if stock == "DONE":
        break
    if stock not in stock_prices:
        print("Stock not available. Choose from:", ", ".join(stock_prices.keys()))
        continue
    try:
        quantity = int(input(f"Enter quantity of {stock}: "))
    except ValueError:
        print("Invalid input. Please enter a number.")
        continue
    portfolio[stock] = portfolio.get(stock, 0) + quantity
print("\nYour Portfolio:")
for stock, qty in portfolio.items():
    value = stock_prices[stock] * quantity
    total_investment += value
    print(f"{stock} - {qty} shares @ {stock_prices[stock]} each = ${value}")

print("Total Investment Value:", total_investment)
save = input("\nDo you want to save portfolio to file? (yes/no): ").lower()
if save == "yes":
    with open("portfolio.txt", "w") as f:
        f.write("Stock Portfolio:\n")
        for stock, qty in portfolio.items():
            value = stock_prices[stock] * quantity
            f.write(f"{stock} - {qty} shares = ${value}\n")
        f.write(f"\nTotal Investment Value: ${total_investment}\n")
    print("Portfolio saved to portfolio.txt")

