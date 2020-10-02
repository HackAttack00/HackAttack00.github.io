---
title: "Command Pattern"
date: 2020-10-03 08:49:00 -0400
categories: pattern
---

### QUESTION
커맨드 실행과 호출을 분리해야하는 경우, 런타임에서 행동을 선택
### SOLUTION
```markdown
protocol MathCommand {
    func execute(num1: Double, num2: Double) -> Double
}

struct AdditionCommand: MathCommand {
    func execute(num1: Double, num2: Double) -> Double {
        return num1 + num2
    }
}

struct SubtractionCommand: MathCommand {
    func execute(num1: Double, num2: Double) -> Double {
        return num1 - num2
    }
}

struct MultiplicationCommand: MathCommand {
    func execute(num1: Double, num2: Double) -> Double {
        return num1 * num2
    }
}

struct DivisionCommand: MathCommand {
    func execute(num1: Double, num2: Double) -> Double {
        return num1 / num2
    }
}

struct Calculator {
    func performCalculaton(num1: Double, num2: Double, command: MathCommand) -> Double {
        return command.execute(num1: num1, num2: num2)
    }
}

var calc = Calculator()
var startValue = calc.performCalculaton(num1: 25, num2: 10, command: SubtractionCommand())
var answer = calc.performCalculaton(num1: startValue, num2: 5, command: MultiplicationCommand())


```
