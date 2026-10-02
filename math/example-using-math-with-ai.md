---
name: example-using-math-with-ai.md
description: Illustrate how you use code to do math with your AI.
---

## When to Use

-- AI is bad at math. But most AIs now have the ability to process code within a prmopt or even as uploaded files with the prompt.
-- This eaxmple uses a simple Python function to calculate prime numbers between [start] and [end].
-- Obviously this is an extremely expensive way to run this. Using a spreadsheet formula would be less CPU/Energy intense, but this is meant to be an example of how you do math within a prompt and response.

## Input Variables

-- **`start`**: description (e.g., `74`).
-- **`end`**: description (e.g., `500`).

## System Prompt

```text
Using the included python function "findPrimes(start,End)" tell me the prime numbers where [start]=70 and [end]=200.

"
def findPrimes(start,end):
    #Returns a list of prime numbers between start and end (inclusive).

    primes = []

    for num in range(start, end + 1):
        if num > 1:
            # Check for factors up to the square root of the number
            for i in range(2, int(num ** 0.5) + 1):
                if num % i == 0:
                    break  # Not a prime, exit the inner loop
            else:
                # The else block runs only if the loop didn't break
                primes.append(num)

    return primes
" 
