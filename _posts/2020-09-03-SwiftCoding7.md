---
title: "Condense whitespace"
date: 2020-09-03 3:10:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that returns a string with any consecutive spaces replaced with a single space.

### SOLUTION
~~~ swift
class Solution {
  func challenge7a(string: String) -> String {
    let arrayStr = string.components(separatedBy: .whitespacesAndNewlines)
    let condensedSpaceStr = arrayStr.filter {!$0.isEmpty}.joined(separator: " ")
    return condensedSpaceStr
  }
  func challenge7b(string: String) -> String {
    string.replacingOccurrences(of: " +", with: " ", options: .regularExpression, range: nil)
  }
}

let solution = Solution.init()
solution.challenge7a(string: "Hello      hello      hello")
solution.challenge7b(string: "Hello      hello      hello?")
~~~
