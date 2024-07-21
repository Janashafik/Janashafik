import time
import random

score = 0

def victor():
    global score
    input("Congratulations! You've successfully crossed the bridge. Your legend begins now.")
    time.sleep(2)
    print("Your final score is", score)
    play_again = input("Do you want to play again? (y/n): ")
    if play_again.lower() == "y":
        reset_score()
        one_or_two()
    else:
        print("Goodbye!")
        time.sleep(1)
        exit()

def wasted():
    global score
    print("Hahaha! You slipped into the river. Game Over.")
    time.sleep(1)
    print("Your final score is", score)
    time.sleep(1)
    print("Try again.")
    play_again = input("Do you want to play again? (y/n): ")
    if play_again.lower() == "y":
        reset_score()
        one_or_two()
    else:
        print("Goodbye!")
        time.sleep(1)
        exit()

def reset_score():
    global score
    score = 0

def one_or_two():
    global score
    print("You find yourself on an old bridge with a river underneath it")
    time.sleep(3)
    print("and a lion behind you.")
    time.sleep(2)
    print("To pass safely through the bridge, you must solve its puzzle.")
    time.sleep(3)
    
    questions = [
        ("3 * 5", [10, 15], 1),
        ("4 * 4", [16, 12], 0),
        ("5 * 2", [10, 12], 0)
    ]
    
    question = random.choice(questions)
    print(f"You are now on the first plank of the bridge with '{question[0]}' written on it.")
    time.sleep(3)
    print(f"1.   {question[1][0]}")
    time.sleep(2)
    print(f"2.   {question[1][1]}")

    while True:
        try:
            inp = int(input("Choose 1 or 2: "))
            if inp == question[2] + 1:
                print("Now you have arrived safely, and the second plank of the bridge appears before you, with '3 * 3' written on it.")
                time.sleep(1)
                print("1.   9")
                time.sleep(2)
                print("2.  12")
                while True:
                    try:
                        inp = int(input("Choose 1 or 2: "))
                        if inp == 1:
                            print("You arrived safely! You are victorious.")
                            time.sleep(1)
                            third_plank()
                            score += 5
                            print("Your Score is", score)
                        elif inp == 2:
                            score -= 5
                            wasted()
                        else:
                            print("Invalid input. Please choose 1 or 2.")
                    except ValueError:
                        print("Invalid input. Please enter a number.")
            elif inp == question[2] + 2:
                score -= 5
                wasted()
            else:
                print("Invalid input. Please choose 1 or 2.")
        except ValueError:
            print("Invalid input. Please enter a number.")

def third_plank():
    global score
    print("You've reached the third plank of the bridge.")
    time.sleep(2)
    print("This plank has a choice:")
    print("1. Solve a riddle.")
    print("2. Jump into the river.")
    while True:
        try:
            choice = int(input("Choose 1 or 2: "))
            if choice == 1:
                score += 5
                riddle_plank()
            elif choice == 2:
                score -= 5
                wasted()
            else:
                print("Invalid input. Please choose 1 or 2.")
        except ValueError:
            print("Invalid input. Please enter a number.")

def riddle_plank():
    global score
    print("Here's the riddle:")
    print("I speak without a mouth and hear without ears. I have no body, but I come alive with the wind. What am I?")
    print("1. Echo")
    print("2. Whisper")
    while True:
        try:
            choice = int(input("Choose 1 or 2: "))
            if choice == 1:
                print("Correct! You may proceed to the next plank.")
                score += 5
                fourth_plank()
            elif choice == 2:
                score -= 5
                wasted()
            else:
                print("Invalid input. Please choose 1 or 2.")
        except ValueError:
            print("Invalid input. Please enter a number.")

def fourth_plank():
    global score
    print("The fourth plank has a math problem:")
    print("What is the square root of 144?")
    print("1. 12")
    print("2. 9")
    while True:
        try:
            answer = int(input("Choose 1 or 2: "))
            if answer == 1:
                score += 5
                victor()
            else:
                score -= 5
                wasted()
        except ValueError:
            print("Invalid input. Please enter a number.")

# Start the game
reset_score()
one_or_two()
