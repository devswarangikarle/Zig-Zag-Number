# Zig-Zag-Number

In a kingdom of numbers, there's a special type of number called a "Zig-Zag Number." These numbers are magical because each pair of adjacent digits differs by exactly 1. Single-digit numbers are naturally considered Zig-Zag Number, while others, like 8987 or 4343456, also possess this beauty. However, numbers like 796 or 89098 break this pattern and are not considered Zig-Zag Number.
You are given a large number X and tasked with finding the largest Zig-Zag Number that is smaller than or equal to X. Your mission is to uncover the most beautiful number that stays within this limit.

def dfs(num, X):

    global max_zigzag
    if num > X:
        return
    max_zigzag = max(max_zigzag, num)
    last_digit = num % 10
    if last_digit > 0:
        dfs(num * 10 + (last_digit - 1), X)
    if last_digit < 9:
        dfs(num * 10 + (last_digit + 1), X)

def largest_zigzag(X):

    global max_zigzag
    max_zigzag = -1
    for digit in range(1, 10):  
        dfs(digit, X)
    return max_zigzag

if __name__ == "__main__":
    X = int(input().strip())  
    print(largest_zigzag(X))  
