---
title: "Count the characters"
date: 2020-09-01 1:19:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts a string, and returns how many times a specific character appears, taking case into account.

### SOLUTION
```markdown
class Solution {
  func challenge5a(input: String, count: Character) -> Int {
     var letterCount = 0
     for letter in input {
        if letter == count {
           letterCount += 1
        }
      }
      return letterCount
  }

  func challenge5b(input: String, count: Character) -> Int {
     return input.reduce(0) {
        $1 == count ? $0 + 1 : $0
     }
  }
}

let solution = Solution.init()
solution.challenge5a(input: "hello", count: "l")
solution.challenge5b(input: "whatthehell", count: "h")
```
