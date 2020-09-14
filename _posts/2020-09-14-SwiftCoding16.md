---
title: "Fizz Buzz"
date: 2020-09-14 23:28:00 -0400
categories: algorithm
---

### QUESTION
Write a function that counts from 1 through 100, and prints "Fizz" if the counter is evenly divisible by 3, "Buzz" if it's evenly divisible by 5, "Fizz Buzz" if it's even divisibly by three and five, or the counter number for all other cases.
### SOLUTION
```markdown
class Solution {
    func challenge16() {
        var mod1: Int
        var mod2: Int
        var results: String
        
        for i in 1 ... 100 {
            results = ""
            mod1 = i % 3
            mod2 = i % 5
            
            if (mod1 == 0 && mod2 == 0) {
                results.append(contentsOf: "Fizz Buzz")
            } else if (mod1 == 0) {
                results.append(contentsOf: "Fizz")
            } else if (mod2 == 0) {
                results.append(contentsOf: "Buzz")
            } else {
                results.append(contentsOf: String(i))
            }
            print(results)
        }
    }
    
    func challenge16c() {
        (1 ... 100).forEach{
            print( $0 % 3 == 0 ? $0 % 5 == 0 ? "Fizz Buzz" : "Fizz" : $0 % 5 == 0 ? "Buzz" : "\($0)")
        }
    }
}

let solution = Solution.init()
solution.challenge16()
```
