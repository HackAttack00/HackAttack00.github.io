---
title: "String permutations"
date: 2020-09-10 23:41:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that prints all possible permutations of a given input string.
### SOLUTION
```markdown
class Solution {
    func challenge14(string: String, current: String = "") {
        let length = string.count
        let strArray = Array(string)
        
        if (length == 0) {
            print(current)
            print("******")
        } else {
            print(current)
            
            for i in 0 ..< length {
                let left = String(strArray[0 ..< i])
                let right = String(strArray[i+1 ..< length])
                
                print("\(left) | \(right)")
                challenge14(string: left + right, current: current + String(strArray[i]))
            }
        }
    }

}

let solution = Solution.init()
solution.challenge14(string: "wombat", current: "")
```
