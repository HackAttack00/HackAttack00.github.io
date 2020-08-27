---
title: "Do two strings contain the same characters?"
date: 2020-08-27 1:03:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts a String as its only parameter, and returns true if the string reads the same when reversed, ignoring case.

### SOLUTION
```markdown
class Solution {
    func challenge2(input: String) -> Bool {
        let lowercase = input.lowercased()
 
        return lowercase.reversed() == Array(lowercase)
    }
}

let solution = Solution.init()
print("Rats live on no evil star \(solution.challenge2(input: "Rats live on no evil star"))")
print("rotator \(solution.challenge2(input: "rotator"))")
```
