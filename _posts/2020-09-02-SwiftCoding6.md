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
  func challenge6a(string: String) -> String {
    let array = string.map{ String($0) }
    let set = NSOrderedSet(array: array)
    let letters = Array(set) as! Array<String>
    return letters.joined()
  }
}

let solution = Solution.init()
solution.challenge6a(string: "Hello")
```
