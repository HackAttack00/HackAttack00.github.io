---
title: "Recreate the pow() function"
date: 2020-09-16 24:00:00 -0400
categories: algorithm
---

### QUESTION
Write a function that accepts positive minimum and maximum integers, and returns a random nmber between those two bounds, inclusive.
### SOLUTION
```markdown
class Solution {
    func challenge18(number: Int, power: Int) -> Int {
      guard number > 0, power > 0 else { return 0 }
      if power == 1 { return number }
      return number * challenge18(number: number, power: power - 1)
    }
}

let solution = Solution.init()
solution.challenge18(number: 8, power: 3)
```

