---
title: "Design Pattern"
date: 2020-08-29 7:03:00 -0400
categories: Disign Pattern
---

###Builder Design Pattern
```markdown
protocol BurgerBuilder {
    var name: String {get}
    var patties: Int {get}
    var bacon: Bool {get}
    var cheese: Bool {get}
    var pickles: Bool {get}
    var ketchup: Bool {get}
    var mustard: Bool {get}
    var lettuce: Bool {get}
    var tomato: Bool {get}
}

struct HamburgerBuilder: BurgerBuilder {
    var name: String = "Burger"
    var patties: Int = 1
    var bacon: Bool = false
    var cheese: Bool = false
    var pickles: Bool = true
    var ketchup: Bool = true
    var mustard: Bool = true
    var lettuce: Bool = false
    var tomato: Bool = false
}

struct CheeseBurgerBuilder: BurgerBuilder {
    var name: String = "CheeseBurger"
    var patties: Int = 1
    var bacon: Bool = false
    var cheese: Bool = true
    var pickles: Bool = true
    var ketchup: Bool = true
    var mustard: Bool = true
    var lettuce: Bool = false
    var tomato: Bool = false
}

struct Burger {
    var name: String
    var patties: Int
    var bacon: Bool
    var cheese: Bool
    var pickles: Bool
    var ketchup: Bool
    var mustard: Bool
    var lettuce: Bool
    var tomato: Bool
    
    init(builder: BurgerBuilder) {
        self.name = builder.name
        self.patties = builder.patties
        self.bacon = builder.bacon
        self.cheese = builder.cheese
        self.pickles = builder.pickles
        self.ketchup = builder.ketchup
        self.mustard = builder.mustard
        self.lettuce = builder.lettuce
        self.tomato = builder.tomato
    }
    
    func showBurger() {
        print("Name: \(name)")
        print("patties: \(patties)")
        print("bacon: \(bacon)")
        print("cheese: \(cheese)")
        print("pickles: \(pickles)")
        print("ketchup: \(ketchup)")
        print("mustard: \(mustard)")
        print("lettuce: \(lettuce)")
        print("tomato: \(tomato)")
    }
}

var myBurger = Burger(builder: HamburgerBuilder())
myBurger.showBurger()

var myCheeseBurgerBuilder = CheeseBurgerBuilder()
var myCheeseBurger = Burger(builder: myCheeseBurgerBuilder)
myCheeseBurger.tomato = false
myCheeseBurger.showBurger()
```

###Factory Design Pattern
```markdown
코드
```
