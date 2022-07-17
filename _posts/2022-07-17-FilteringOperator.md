---
title: "필터링 오퍼레이터"
date: 2022-07-17 00:00:00 -0400
categories: combine
tag: filtering operator


---

필터링 오퍼레이터

1. collect()

~~~swift
example(of: "collect") {
  ["A", "B", "C", "D", "E"].publisher
  .collect()
  .sink(receiveCompletion: { print($0) },
        receiveValue: { print($0) })
  .store(in: &subscriptions)
}
~~~



2. map(_ :)

~~~swift
example(of: "map") {
  let formatter = NumberFormatter()
  formatter.numberStyle = .spellOut
  
  [123, 4, 56].publisher
    .map {
      formatter.string(for: NSNumber(integerLiteral: $0)) ?? ""
    }
    .sink(receiveValue: { print($0) })
    .store(in: &subscriptions)
}

example(of: "mapping key paths") {
  let publisher = PassthroughSubject<Coordinate, Never>()
  
  publisher
    .map(\.x, \.y)
    .sink(receiveValue: { x, y in
      print(
        "The coordinate at (\(x), \(y)) is in quadrant",
        quadrantOf(x: x, y: y)
      )
    })
    .store(in: &subscriptions)

  publisher.send(Coordinate(x: 10, y: -8))
  publisher.send(Coordinate(x: 0, y: 5))
}

example(of: "tryMap") {
  // 1
  Just("Directory name that does not exist")
    // 2
    .tryMap { try FileManager.default.contentsOfDirectory(atPath: $0) }
    // 3
    .sink(receiveCompletion: { print($0) },
          receiveValue: { print($0) })
    .store(in: &subscriptions)
}

example(of: "flatMap") {
  func decode(_ codes: [Int]) -> AnyPublisher<String, Never> {
    Just(
      codes
        .compactMap { code in
          guard (32...255).contains(code) else { return nil }
          return String(UnicodeScalar(code) ?? " ")
        }
        .joined()
    )
    .eraseToAnyPublisher()
  }
  
[72, 101, 108, 108, 111, 44, 32, 87, 111, 114, 108, 100, 33]
  .publisher
  .collect()
  .flatMap(decode)
  .sink(receiveValue: { print($0) })
  .store(in: &subscriptions)
}

~~~

