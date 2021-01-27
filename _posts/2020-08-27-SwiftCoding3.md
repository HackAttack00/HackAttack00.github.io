---
title: "Do two strings contain the same characters?"
date: 2020-08-27 1:03:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a String as its only parameter, and returns true if the string reads the same when reversed, ignoring case.

### SOLUTION
```markdown
class Solution {
    func challenge3a(string1: String, string2: String) -> Bool {
        
        let trimmedStr1 = string1.replacingOccurrences(of: " ", with: "")
        let trimmedStr2 = string2.replacingOccurrences(of: " ", with: "")
        var checkString = trimmedStr2
        
        for letter in trimmedStr1 {
            if let index = checkString.firstIndex(of: letter) {
                checkString.remove(at: index)
            } else {
                return false
            }
        }
        
        return checkString.count == 0
    }
    
    func challenge3b(string1: String, string2: String) -> Bool {
        
        let trimmedStr1 = string1.replacingOccurrences(of: " ", with: "")
        let trimmedStr2 = string2.replacingOccurrences(of: " ", with: "")
        
        let array1 = Array(trimmedStr1)
        let array2 = Array(trimmedStr2)
        
        return array1.count == array2.count && array1.sorted() == array2.sorted()
    }
}

let solution = Solution.init()

solution.challenge3a(string1: "a1 b2    ", string2: "b 1 a 2")
solution.challenge3b(string1: "a1 b2    ", string2: "b 1 a 2")
```
