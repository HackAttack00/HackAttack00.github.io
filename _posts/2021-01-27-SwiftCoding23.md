---
title: "Integer disguised as string"
date: 2021-01-27 18:01:00 -0400
categories: algorithm
tag: algorithm
---

### QUESTION
Write a function that accepts a string and returns true if it contains only numbers, i.e. the digits through 9.

### SOLUTION
~~~ swift
func challenge23(input: String) -> Bool {
  return UInt(input) != nil
}

challenge23(input: "12345")
~~~

