---
title: "Are the letters unique"
date: 2020-08-26 1:42:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function the accepts a String as its only parameter, and returns true if the string has only unique letters, taking letter case into account.

### SOLUTION
```markdown
class Solution {
    func challenge1(input: String) -> Bool {
        
        var usedLetters = [Character]()
        
        for letter in input {
            if usedLetters.contains(letter) {
                return false
            }
            
            usedLetters.append(letter)
        }
        
        return true
    }
}

let solution = Solution.init()
print("abcdefghijklmnop \(solution.challenge1(input: "abcdefghijklmnop"))")
print("Hello, world \(solution.challenge1(input: "Hello, world"))")
```
