###### 2/9 - Play Rock, Paper, Scissors against CPU 
- Else, elif, if statements
```
import random

options = ['Rock', 'Paper', 'Scissors']
welcome_str = "Let's play! Your options are: "
print(welcome_str +",".join(options))

def playgame(wincount):
    """Define game logic"""
    print('playing to ' + str(wincount))
    cpu_score = 0
    player_score = 0

    while cpu_score < wincount and player_score < wincount:
        cpu_choice = random.choice(options)
        player_choice = input("Type an option.")
        if player_choice not in options:
            print("Invalid. Try again!")
        else:
            #print("{0} is cpu choice, and {1} is your choice.".format(cpu_choice,player_choice))
            if cpu_choice == player_choice:
                print("Draw - No one scores")
            elif (cpu_choice =="Scissors" and player_choice =="Paper") or (cpu_choice =="Paper" and player_choice =="Rock") or (cpu_choice == "Rock" and player_choice =="Scissors"):
                print("CPU Wins")
                cpu_score = cpu_score + 1
            else:
                print("You win")
                player_score = player_score + 1

    return player_score == wincount

while True:
    num_times = input("How many rounds would you like to play? Enter number")
    player_won = playgame(int(num_times))

    if player_won:
        print("You win!")
    else:
        print("CPU wins :(")
    play_again = input("Play again? (y/n)")
    if play_again == "n":
        print("Goodbye")
        break
```
###### 2/10 - Exercise from CS50 class to create "super mario stairs" in text
- While loop
- Functions
```
def hashmaker(x):
    """Define function to create hash blocks"""
    res = ""
    for i in range(1,x+1):
        res = res + "#"
    return res

def indentmaker(y):
    """Define function to right-align steps"""
    res = ""
    for i in range(1,y):
        res = res + " "
    return res

pick = int(input("Pick a number"))
while True:
    if pick < 1 or pick > 8:
        pick = int(input("Try Again"))
    else:
        count = 0
        countb = pick + 1
        while count < pick:
            count = count + 1
            countb = countb - 1
            str1 = indentmaker(countb)
            str2 = hashmaker(count)
            print(str1 + str2)
        break
```
