---
title: "Binary reverse"
date: 2020-11-01 23:58:00 -0400
categories: algorithm
---

### QUESTION
Create a function that accepts an unsigned 8-bit integer and returns its binary reverse, padded so that it holds precisely eight binary digits.

### SOLUTION
```markdown
func challenge22(number: UInt) -> UInt {
  let binary = String(number, radix: 2)
  let paddingAmount = 8 - binary.count
  let paddingBinary = String(repeating: "0", count: paddingAmount) + binary
  let reversedBinary = String(paddingBinary.reversed())
  
  return UInt(reversedBinary, radix: 2)!
}

challenge22(number: 20)
```
