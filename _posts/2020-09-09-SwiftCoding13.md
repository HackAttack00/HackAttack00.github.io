---
title: "Run-length encoding"
date: 2020-09-09 23:00:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a string as input, then return often each letter is repeated in a single run, taking case into account.
### SOLUTION
```markdown
class Solution {
    func challenge13(input: String) -> String {
        var currentLetter: Character?
        var returnValue = ""
        var letterCounter = 0
        
        for letter in input {
            if letter == currentLetter {
                letterCounter += 1
            } else {
                if let current = currentLetter {
                    returnValue = returnValue.appending("\(current)\(letterCounter)")
                }
                
                currentLetter = letter
                letterCounter = 1
            }
        }
        
        if let current = currentLetter {
            returnValue = returnValue.appending("\(current)\(letterCounter)")
        }
        
        return returnValue
    }
    
    func challenge13b(input: String) -> String {
        var returnValue = ""
        var letterCounter = 0
        let letterArray = Array(input)
        
        for i in 0..<letterArray.count {
            letterCounter += 1
            
            if i + 1 == letterArray.count || letterArray[i] != letterArray[i + 1] {
                returnValue += "\(letterArray[i])\(letterCounter)"
                letterCounter = 0
            }
        }
        
        return returnValue
    }
}

let solution = Solution.init()
solution.challenge13(input: "aaabbbccccaaaaaa")
solution.challenge13b(input: "aaabbbccccaaaaaa")
```
