---
title: "Remove duplicate letters from a string"
date: 2020-09-01 1:19:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a string as its input, and returns the same string just with duplicate letters removed.

### SOLUTION
```markdown
class Solution {
  func challenge6a(string: String) -> String {
    let array = string.map{ String($0) }
    let set = NSOrderedSet(array: array)
    let letters = Array(set) as! Array<String>
    return letters.joined()
  }
  
  func challenge6c(string: String) -> String {
    var used = [Character: Bool]()
  
    let result = string.filter({
        used.updateValue(true, forKey: $0) == nil
    })

    return String(result)
}

let solution = Solution.init()
solution.challenge6a(string: "Hello")
solution.challenge6c(string: "Hello,world")
```
