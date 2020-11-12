# Techdegree Project 1
 Random Guessing
import random

def start_game():
    print("Howdy and Welcome to THE Random Game!")

    ran_num = random.randrange(1,11)
    global num_of_guess
    num_of_guess = 0
    
    while True:
        user_num = input("Pick a number between 1 and 10, friend: ")
        try:
            user_num = int(user_num)
            if user_num > 10:
                raise ValueError("Your number is higher than 10! You'll never win if you guess out of the range.")
            elif user_num < 1:
                raise ValueError("Your number is lower than 1! You'll never win if you guess out of the range.")
        except ValueError as err:
            print("{}".format(err))
            print("Please try again.")
        else:
            if user_num < ran_num:
                print("Oops! You're a tad low! Give it another try")
                num_of_guess += 1
            elif user_num > ran_num:
                print("Uh oh! You went too high! Go again, pal")
                num_of_guess += 1
            else:
                num_of_guess += 1
                print("Bingo! You're right! Great job! It took you {} guesses.".format(num_of_guess))
                return num_of_guess

play_game = input("Woukd you like to play a random game? (yes/no)  ") 
    
high_score = 11

while play_game == 'yes':    
    start_game()
    if num_of_guess < high_score:
        high_score = num_of_guess
        print("New High Score! {} guesses.".format(high_score))
    else:
        print("High Score is {}.".format(high_score))
    play_game = input("Woukd you like to play again? (yes/no)  ")

    
print("Don't be shy! Come play again soon!")
