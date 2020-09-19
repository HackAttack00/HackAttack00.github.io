---
title: "Swap two numbers"
date: 2020-09-20 00:23:00 -0400
categories: algorithm
---

### QUESTION
Swap two positive variable integers, a and b, without using a temporary variable.
### SOLUTION
```markdown
class Solution {
    func challenge19(number1: Int, number2: Int) -> (Int, Int) {
        var num1 = number1 ^ number2
        let num2 = num1 ^ number2
        num1 = num1 ^ num2
        return (num1, num2)
    }
    
    func challenge19a(number1:inout Int, number2:inout Int) -> (Int, Int) {
        swap(&number1, &number2)
        return (number1, number2)
    }
    
    func challenge19b(number1: Int, number2: Int) -> (Int, Int) {
        return (number2, number1)
    }
}

var n1 = 9
var n2 = 6
let solution = Solution.init()
solution.challenge19a(number1: &n1, number2: &n2)
solution.challenge19b(number1: n1, number2: n2)
```





class Solution {
    func challenge19(number1: Int, number2: Int) -> (Int, Int) {
        var num1 = number1 ^ number2
        let num2 = num1 ^ number2
        num1 = num1 ^ num2
        return (num1, num2)
    }
    
    func challenge19a(number1:inout Int, number2:inout Int) -> (Int, Int) {
        swap(&number1, &number2)
        return (number1, number2)
    }
    
    func challenge19b(number1: Int, number2: Int) -> (Int, Int) {
        return (number2, number1)
    }
}

var n1 = 9
var n2 = 6
let solution = Solution.init()
solution.challenge19a(number1: &n1, number2: &n2)
solution.challenge19b(number1: n1, number2: n2)
