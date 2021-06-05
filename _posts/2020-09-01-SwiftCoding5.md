---
title: "Count the characters"
date: 2020-09-01 1:19:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a string, and returns how many times a specific character appears, taking case into account.

### SOLUTION
~~~ swift
class Solution {
  func challenge5a(input: String, count: Character) -> Int {
     var letterCount = 0
     for letter in input {
        if letter == count {
           letterCount += 1
        }
      }
      return letterCount
  }

  func challenge5b(input: String, count: Character) -> Int {
     return input.reduce(0) {
        $1 == count ? $0 + 1 : $0
     }
  }
  
  func challenge5c(input: String, count: String) -> Int {
    let array = input.map{ String($0) }
    let counted = NSCountedSet(array: array)
    
    return counted.count(for: count)
  }
    
  func challenge5d(input: String, count: String) -> Int {
    let modified = input.replacingOccurrences(of: count, with: "")
      
    return input.count - modified.count
  }
}

let solution = Solution.init()
solution.challenge5a(input: "hello", count: "l")
solution.challenge5b(input: "whatthehell", count: "h")
solution.challenge5c(input: "goodmorning", count: "o")
solution.challenge5d(input: "idontknow", count: "n")
~~~
