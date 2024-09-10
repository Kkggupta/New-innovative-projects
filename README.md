import random
from collections import Counter

# Function to roll a die
def roll_die():
    return random.randint(1, 6)

# Function to roll multiple dice
def roll_multiple_dice(num_dice):
    rolls = []
    for _ in range(num_dice):
        rolls.append(roll_die())
    return rolls

# Die simulator with multiple features
def die_simulator():
    roll_history = []
    
    while True:
        roll = input("Press 'r' to roll the die(s), 'h' for history, 's' for statistics, 'q' to quit: ").lower()
        
        if roll == 'r':
            num_dice = int(input("How many dice do you want to roll? "))
            current_rolls = roll_multiple_dice(num_dice)
            print(f"You rolled: {current_rolls}")
            roll_history.extend(current_rolls)
        
        elif roll == 'h':
            if not roll_history:
                print("No rolls have been made yet.")
            else:
                print(f"Roll History: {roll_history}")
        
        elif roll == 's':
            if not roll_history:
                print("No rolls have been made yet.")
            else:
                roll_counts = Counter(roll_history)
                most_common = roll_counts.most_common(1)[0]
                print(f"The most frequent roll is {most_common[0]} with {most_common[1]} occurrences.")
        
        elif roll == 'q':
            print("Exiting the simulator. Goodbye!")
            break
        
        else:
            print("Invalid input. Please press 'r' to roll, 'h' for history, 's' for stats, or 'q' to quit.")

# Run the simulator
die_simulator()

