---
title: "Counting binary ones"
date: 2020-10-14 1:58:00 -0400
categories: algorithm
---

### QUESTION
Create a function that accepts any positive integer and returns the next highest and next lowest number that has same number of ones in its binary representation. if either number is not possible, return nil for it.

### SOLUTION
```markdown
func challenge21(number: Int) -> (nextHighest: Int?, nextLowest: Int?) {
    func ones(in number: Int) -> Int {
        let currentBinary = String(number, radix: 2)
        return currentBinary.filter{ $0 == "1"}.count
    }
    
    let targetOnes = ones(in: number)
    var nextHighest: Int? = nil
    var nextLowest: Int? = nil
    
    for i in number + 1...Int.max {
        if ones(in: i) == targetOnes {
            nextHighest = i
            break
        }
    }
    
    for i in (0 ..< number).reversed() {
        if ones(in: i) == targetOnes {
            nextLowest = i
            break
        }
    }
    
    return (nextHighest, nextLowest)
}

challenge21(number: 22)
```
