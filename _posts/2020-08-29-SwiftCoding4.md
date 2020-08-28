---
title: "Does one string contain another?"
date: 2020-08-29 7:03:00 -0400
categories: algorithm
---

### QUESTION
Write your own version of the contains() method on String that ignores letter case, and without using the existing contains() method.

### SOLUTION
```markdown
extension String {
    func fuzzyContains(_ string: String) -> Bool {
        return self.uppercased().range(of: string.uppercased()) != nil
    }
}

extension String {
    func fuzzyContains2(_ string: String) -> Bool {
        return range(of: string, options: .caseInsensitive) != nil
    }
}
```
