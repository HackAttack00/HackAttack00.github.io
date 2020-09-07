---
title: "Three different letters"
date: 2020-09-07 22:40:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts two strings, and returns true if they are identical in length but have no more than three different letters, taking case and string order into account.
### SOLUTION
```markdown
class Solution {
    func challenge11(first: String, second: String) -> Bool {
        guard first.count == second.count else {
            return false
        }
        
        let firstArray = Array(first)
        let secondArray = Array(second)
        var differences = 0
        
        for (index, letter) in firstArray.enumerated() {
            if secondArray[index] != letter {
                differences += 1
            }
            
            if differences > 3 {
                return false
            }
        }
        
        return true
    }
}

let solution = Solution.init()
solution.challenge11(first: "Clamp", second: "Cramp")
solution.challenge11(first: "Clamp", second: "Grans")

```
