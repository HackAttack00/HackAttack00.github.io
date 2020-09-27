---
title: "Builder Pattern"
date: 2020-09-27 10:04:00 -0400
categories: pattern
---

### QUESTION
복잡한 생성자를 단순화 시키기위한 빌더 패턴
### SOLUTION
```markdown
protocol PizzaBase {
    var name: String { get }
    var cheeze: Bool { get }
    var shrimp: Bool { get }
}

struct SuperDeluxePizza: PizzaBase {
    var name = "SuperDeluxe"
    var cheeze = true
    var shrimp = false
}

struct BlackShrimpPizza: PizzaBase {
    var name = "BlackShrimp"
    var cheeze = true
    var shrimp = true
}

struct Pizza {
    var name: String
    var cheeze: Bool
    var shrimp: Bool
    
    init(builder: PizzaBase) {
        self.name = builder.name
        self.cheeze = builder.cheeze
        self.shrimp = builder.shrimp
    }
    
    func showPizza() {
        print("Name = \(self.name)")
        print("Cheeze = \(self.cheeze)")
        print("Shrimp = \(self.shrimp)")
    }
}

let superDeluxePizza = SuperDeluxePizza()
var myPizzaOrder = Pizza(builder: superDeluxePizza)
myPizzaOrder.showPizza()

let blackShrimpPizza = BlackShrimpPizza()
var myPizzaOrder2 = Pizza(builder: blackShrimpPizza)
myPizzaOrder2.showPizza()
```
