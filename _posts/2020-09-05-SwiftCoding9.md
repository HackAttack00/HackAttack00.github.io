---
title: "Find pangrams"
date: 2020-09-05 4:40:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that returns true if it is given a string that is an English pangram, ignoring letter case.

### SOLUTION
~~~ swift
class Solution {
    func challenge9(input: String) -> Bool {
        let set = Set(input.lowercased())
        let letters = set.filter({$0 >= "a" && $0 <= "z"})
        return letters.count == 26
    }
}

let solution = Solution.init()
solution.challenge9(input: "The quick brown fox jumps over the lazy dog")
~~~
