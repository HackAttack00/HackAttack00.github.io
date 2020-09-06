---
title: "Vowels and consonants"
date: 2020-09-06 11:25:00 -0400
categories: algorithm
---

### QUESTION
Given a string in English, return a tuple containing the number of vowels and consonants.
### SOLUTION
```markdown
class Solution {
    func challenge10a(input: String) -> (vowels:Int, consonants:Int) {
        let vowels = CharacterSet(charactersIn: "aeiou")
        let consonants = CharacterSet(charactersIn: "bcdfghjklmnpqrstvwxyz")
        
        var vowelCounts = 0
        var consonantCounts = 0
        for letter in input.lowercased() {
            let stringLetter = String(letter)
            if stringLetter.rangeOfCharacter(from: vowels) != nil {
                vowelCounts = vowelCounts + 1
            }
            else if stringLetter.rangeOfCharacter(from: consonants) != nil {
                consonantCounts = consonantCounts + 1
            }
        }
        
        return (vowelCounts, consonantCounts)
    }

    func challenge10b(input: String) -> (vowels:Int, consonants:Int) {
        let vowels = "aeiou"
        let consonants = "bcdfghjklmnpqrstvwxyz"
        
        var vowelCounts = 0
        var consonantCounts = 0
        
        for letter in input.lowercased() {
            if vowels.contains(letter) {
                vowelCounts += 1
            }
            else if consonants.contains(letter) {
                consonantCounts += 1
            }
        }
        
        return (vowelCounts, consonantCounts)
    }
}

let solution = Solution.init()
solution.challenge10a(input: "The quick brown fox jumps over the lazy dog")
solution.challenge10b(input: "abcdefghijklmnopqrstuvwxyz")
```
