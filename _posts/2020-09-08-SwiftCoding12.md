---
title: "Find longest prefix"
date: 2020-09-08 12:35:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a string of words with a simiar prefix, separated by spaces, and returns the longest substring that prefixes all words.
### SOLUTION
```markdown
class Solution {
    func challenge12(input: String) -> String {
        let parts = input.components(separatedBy: " ")
        guard let first = parts.first else { return ""}
        
        var currentPrefix = ""
        var bestPrefix = ""
        
        for letter in first {
            currentPrefix.append(letter)
            
            for word in parts {
                if !word.hasPrefix(currentPrefix) {
                    return bestPrefix
                }
            }
            
            bestPrefix = currentPrefix
        }
        
        return bestPrefix
    }

    func myChallenge12(input: String) -> String {
        let words = input.components(separatedBy: " ")
        
        
        let parts = words.first
        
        var prefix = ""
        for (index, word) in words.enumerated() {
            for nextWord in words {
                if word[word.index(word.startIndex, offsetBy: index)] != nextWord[nextWord.index(nextWord.startIndex, offsetBy: index)] {
                    return prefix
                }
            }
            prefix.append(word[word.index(word.startIndex, offsetBy: index)])
        }
        return prefix
    }
}

let solution = Solution.init()
solution.challenge12(input: "swift switch swill swim")
```
