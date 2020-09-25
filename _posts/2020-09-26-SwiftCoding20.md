---
title: "Number is prime"
date: 2020-09-26 00:04:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts an integer as its parameter and returns true if the number is prime.
### SOLUTION
```markdown
class Solution {
    func challenge20(number: Int) -> Bool {
        guard number >= 2 else { return false }
        guard number != 2 else { return true }
        
        let max = Int(ceil(sqrt(Double(number))))
        
        for i in 2 ... max {
            if number % i == 0 {
                return false
            }
        }
        
        return true
    }
}

let solution = Solution.init()
solution.challenge20(number: 17)
```
