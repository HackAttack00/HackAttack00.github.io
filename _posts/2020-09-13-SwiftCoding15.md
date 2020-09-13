---
title: "Reverse the words in a string"
date: 2020-09-10 23:41:00 -0400
categories: algorithm
---

### QUESTION
Write a function that returns a string with each of its words reversed but in the original order, without using a loop.
### SOLUTION
```markdown
class Solution {
    func challenge15(input: String) -> String {
        let words = input.split(separator: " ")
        let reversedWords = words.map {String($0.reversed())}
        
        return reversedWords.joined(separator: " ")
    }
}

let solution = Solution.init()
solution.challenge15(input: "Swift Coding Challenges")
```


