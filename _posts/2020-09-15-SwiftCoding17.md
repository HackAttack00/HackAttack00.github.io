---
title: "Generate a random number in a range"
date: 2020-09-15 23:43:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts positive minimum and maximum integers, and returns a random nmber between those two bounds, inclusive.
### SOLUTION
```markdown
class Solution {
    func challenge17(min: Int, max: Int) -> Int {
        return Int(arc4random_uniform(UInt32(max - min + 1))) + min
    }
}

let solution = Solution.init()
solution.challenge17(min: 8, max: 14)
```



