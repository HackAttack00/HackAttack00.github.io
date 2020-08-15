---
title: "Copy on write"
date: 2020-08-15 23:04:00 -0400
categories: cow
---

fileprivate class BackendQueue<T> {
    private var items = [T]()
    public init() {}
    private init(_ items: [T]) {
        self.items = items
    }
    
    public func addItem(item: T) {
        items.append(item)
    }
    
    public func getItem() -> T? {
        if items.count > 0 {
            return items.remove(at: 0)
        } else {
            return nil
        }
    }
    
    public func count() -> Int {
        return items.count
    }
    
    public func copy() -> BackendQueue<T> {
        return BackendQueue<T>(items)
    }
}

struct Queue {
    private var internalQueue = BackendQueue<Int>()
    
    mutating private func checkUniquelyReferencedInternalQueue() {
        if !isKnownUniquelyReferenced(&internalQueue) {
            print("Making a copy of internalQueue")
            internalQueue = internalQueue.copy()
        } else {
            print("Not making a copy of internalQueue")
        }
    }
    
    public mutating func addItem(item: Int) {
        checkUniquelyReferencedInternalQueue()
        internalQueue.addItem(item: item)
    }
    
    public mutating func getItem() -> Int? {
        checkUniquelyReferencedInternalQueue()
        return internalQueue.getItem()
    }
    
    public func count() -> Int {
        return internalQueue.count()
    }
    
    mutating public func uniquelyReferenced() -> Bool {
        return isKnownUniquelyReferenced(&internalQueue)
    }
}
