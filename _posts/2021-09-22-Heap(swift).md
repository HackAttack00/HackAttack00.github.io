---
layout: post
title: Heap (swift)
date: 2021-09-22 17:13:27 +0900
category: algorithm

---

# 힙 구현 (swift)

> 힙을 구현해보자



~~~swift
import UIKit

class BinaryHeap<T: Comparable> {
    var parent:Int! = nil
    var items:[T] = []
    
    init(data:T){
        self.items = []
        self.items.append(data)
    }
    
    func len() -> Int {
        return self.items.count - 1
    }
    
    func percolateUP() {
        var i = self.len()
        self.parent = i / 2
        while (self.parent != nil && self.parent > 0) {
            if self.items[i] < self.items[parent] {
                self.items.swapAt(parent, i)
            }
            i = parent
            parent = i / 2
        }
    }
    
    func insert(k: T) {
        self.items.append(k)
        self.percolateUP()
    }
    
    func percolateDown(idx:Int) {
        let left = idx * 2
        let right = idx * 2 + 1
        var smallest = idx
        
        if left <= self.len() && self.items[left] < self.items[smallest] {
            smallest = left
        }
        
        if right <= self.len() && self.items[right] < self.items[smallest] {
            smallest = right
        }
        
        if smallest != idx {
            self.items.swapAt(idx, smallest)
            self.percolateDown(idx: smallest)
        }
    }
    
    func extract() -> T? {
        if self.len() == 0 {
            return nil
        }
        let extract = self.items[1]
        self.items[1] = self.items[self.len()]
        self.items.popLast()
        self.percolateDown(idx: 1)
        return extract
    }
}

let BH = BinaryHeap<Int>(data: -999)
BH.insert(k: 8)
BH.insert(k: 5)
BH.insert(k: 19)
BH.insert(k: 1)
BH.insert(k: 18)
BH.insert(k: 7)
BH.insert(k: 4)
BH.insert(k: 15)
BH.insert(k: 6)
BH.insert(k: 10)
BH.insert(k: 12)

print(BH.items)
print(BH.extract())
print(BH.items)
print(BH.extract())
print(BH.items)
print(BH.extract())
print(BH.items)

~~~

