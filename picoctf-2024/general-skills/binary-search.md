# Binary Search

**Category:** General Skills  
**Difficulty:** Easy  
**Date:** 2024-11-04

## Challenge Description
```
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.
Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!
```

## Files Provided
- `guessing-game.sh` - A Bash script that challenges the user to guess a number between 1 and 1000, with a maximum of 10 guesses, to reveal the flag.

## Approach & Solution

### Script Analysis (`guessing-game.sh`)
The provided Bash script generates a random target number between 1 and 1000. The user must guess this number within 10 attempts to retrieve the flag. Key details:

- **Random Target Generation:** A random target number is set between 1 and 1000 using `RANDOM % 1000 + 1`.
- **Input Validation:** The script checks if the guess is a valid number; invalid inputs prompt the user to try again.
- **Feedback Loop:** The script responds with hints of "Higher!" or "Lower!" depending on the guess relative to the target number.
- **Flag Retrieval:** If the guess matches the target, the script retrieves and displays the flag from `/challenge/metadata.json`.
- **Attempts Limit:** The player is allowed a maximum of 10 attempts; if they exceed this, the script ends with a "Sorry" message and an error code.

### Solution: Binary Search Approach
Binary search is ideal here because it’s an efficient method to home in on a target in a sorted range. With each guess, we can halve the remaining possibilities by comparing the midpoint guess to the target.

#### Execution Walkthrough:
1. **Initial Guess (500):** Start with the midpoint (500). Based on the feedback ("Higher!"), the target must be in the range 501–1000.
2. **Second Guess (750):** Midpoint of the new range (501–1000). Feedback "Higher!" narrows the range to 751–1000.
3. **Third Guess (875):** Midpoint of 751–1000. Feedback "Lower!" reduces the range to 751–874.
4. **Subsequent Guesses:** By continuing this midpoint strategy, we quickly close in on the target number with just a few additional guesses.
5. **Final Guess (839):** After narrowing the range through binary search, we find the target and receive the flag.

Sample Output:
```
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 750
Higher! Try again.
Enter your guess: 875
Lower! Try again.
Enter your guess: 812
Higher! Try again.
Enter your guess: 843
Lower! Try again.
Enter your guess: 827
Higher! Try again.
Enter your guess: 835
Higher! Try again.
Enter your guess: 839
Congratulations! You guessed the correct number: 839
Here's your flag: picoCTF{g00d_gu355_de9570b0}
```

## Flag
```
picoCTF{g00d_gu355_de9570b0}
```

## Key Takeaways
### Techniques Learned:
- **Binary Search Algorithm:** This challenge demonstrates the effectiveness of binary search for finding a specific item in a sorted list quickly. This algorithm minimises the search space by half each time, making it much more efficient than a linear search.
- **Signal Handling with `trap`:** The script uses `trap` to handle interruptions, a technique often used to prevent unintended exits or modifications to script behaviour in security-sensitive applications.