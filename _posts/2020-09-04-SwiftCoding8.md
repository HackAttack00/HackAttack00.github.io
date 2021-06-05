---
title: "String is rotated"
date: 2020-09-04 4:40:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts two strings, and returns true if one string is rotation of the other, taking letter case into account.

### SOLUTION
~~~ swift
class Solution {
    func challenge8(input: String, rotated: String) -> Bool {
        let combined = input + input
        return combined.contains(rotated)
    }
    
    func challenge8a(input: String, rotated: String) -> Bool {
        guard input.count == rotated.count else {
            return false
        }
        let combined = input + input
        return combined.contains(rotated)
    }
}

let solution = Solution.init()
solution.challenge8(input: "hello", rotated: "llohe")
solution.challenge8a(input: "hello", rotated: "llohe")
~~~
