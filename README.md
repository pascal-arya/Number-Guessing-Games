# Number Guessing Games
Inspired from https://www.geeksforgeeks.org/number-guessing-game-in-python/

## How to play this games?
1. Insert lower bound number.
2. Insert upper bound number. Upper bound must be greater than lower bound, if upper bound is smaller than lower bound you'll be asked to insert upper bound again.
3. The range of lower and upper bound must greater or equal to 10. For example, if the lower bound is 3 and upperbound is 7 then the range is five, because there's five number in that range (3, 4, 5, 6, 7)
4. The code will pick one random number from the range you pick and your job is to guess that random number. Everytime you make guess you'll get a hint if your guess is too low or too high from the correct number.
5. Well done! You guess the correct number successfully.

## The code
### Import random module
This module pick random number from the determined range of number. 
```python
import random
```
### Generating random number to be guessed
1. Input lower bound
2. Input upper bound
    1. If upper bound is smaller than lower bound ask player to reinsert upperbound.
    2. If upper bound is greater than lower bound check if the range is at least 10.
```python
def get_number():
    a = input("Select your lower bound: ")
    num_range = [a]
    while True:
        b = input("Select your upper bound: ")
        i = a
        if b > a:
            if b-a+1 >= 10:
                while i < b:
                    i += 1
                    num_range.append(i)
                break
            else:
                print("Your range must be greater or equal to 10")
        else:
            print("Upper bound must be greater than lower bound")
    number = random.choice(num_range)
    return number
```

### Guess the number
Gives player hint if their number is too high or too low from the correct number.
```python
def guessing():
    correct_num = get_number()
    attempt = 0
    while True:
        attempt += 1
        guess = input("Guess: ")
        if guess == correct_num:
            print("Success in " + str(attempt) + " attempt, congratulation!")
            break
        elif guess > correct_num:
            print("Too high, try again!")
        elif guess < correct_num:
            print("Too low, try again!")
```
