# Concentration-checker-python-
import time
import random

def ask_question():
    num1 = random.randint(1, 10)
    num2 = random.randint(1, 10)
    operation = random.choice(['+', '-', '*'])
    
    if operation == '+':
        correct_answer = num1 + num2
    elif operation == '-':
        correct_answer = num1 - num2
    else:
        correct_answer = num1 * num2

    print(f"What is {num1} {operation} {num2}?")
    start_time = time.time()
    try:
        user_answer = int(input("Your answer: "))
        end_time = time.time()
        response_time = end_time - start_time
    except ValueError:
        print("Invalid input.")
        return False, 0

    if user_answer == correct_answer:
        print("Correct!")
        return True, response_time
    else:
        print(f"Wrong! The correct answer was {correct_answer}")
        return False, response_time

# Main program
print("🧠 Concentration Checker")
score = 0
total_time = 0
rounds = 5

for i in range(rounds):
    print(f"\nQuestion {i + 1} of {rounds}")
    correct, time_taken = ask_question()
    total_time += time_taken
    if correct:
        score += 1

avg_time = total_time / rounds
print("\n===== Results =====")
print(f"Score: {score} out of {rounds}")
print(f"Average response time: {avg_time:.2f} seconds")

if score == rounds and avg_time < 3:
    print("💪 Excellent concentration!")
elif score >= rounds - 1 and avg_time < 5:
    print("👍 Good focus.")
else:
    print("🧘 Try again when you're more focused.")
