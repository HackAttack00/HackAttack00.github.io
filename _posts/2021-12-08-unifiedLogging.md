---
layout: post
title: iOS14 Logger API (통합 로깅 api)
date: 2021-12-08 17:13:27 +0900
category: wwdc

---

## iOS14 Logger API (통합 로깅 api)

## wwdc20에서 애플은 메세지를 수집, 처리, 예기치 않은 동작을 디버깅하는데 도움을 주는 통합 로깅 api를 발표했다. 

> 프로젝트에 메시지를 기록하기 위해 자주 사용하는 간단한 print문을 변환해보자
>
```swift
print("network start")
```

이걸 os_log를 사용하면

```swift
let log = OSLog.init(subsystem: "com.afreecatv.demo", category: "main") 
os_log("network start")
```

요로케 되는 거고

ios14부터 지원되는 logger api를 사용하면

```swift
let logger = Logger.init(subsystem: "com.afreecatv.demo", category: "main")
logger.debug("network start")
```

요렇게 된다.

> 통합로깅 api 이점

- 낮은 퍼포먼스 오버헤드

- 문자열 보간

- 다른 사용에 대한 다른 로깅 유형(디버그, 정보, 경고, 오류, 오류, 알림)

- 지속적이고 효율적인 로깅 — 장치에서 드문 경우의 버그를 디버그하고 수정할 수 있습니다.

- 런타임에 부하가 적은 다양한 형식 및 표현 옵션

- Visibiltiy 이건...뭐라고 번역을 해야하나.. 일단 보안기능이다.

  

> 문자열 보간 및 문자열 형식 지정

구형 os_log시절

```swift
let count = 0 
let log = OSLog.init(subsystem: "com.afreecatv.demo", category: "main") 
os_log("%d network start", log: log, type: OSLogType.debug, count)
```

에서... 스위프트 스타일로..

```swift
let count = 0 
let logger = Logger.init(subsystem: "com.afreecatv.demo", category: "main") 
logger.debug("\(count) network start")
```

이렇게 사용 가능



> 다른 사용에 대한 다른 로깅 유형

ios14이전의 os_log는 

```swift
os_log("%d network start", log: log, type: OSLogType.debug, count)
```

라서.. 일일이 enum형식의 타입을 직접 넣어줘야했지만

logger에서는 좀 더 개발자 친화적으로

```swift
logger.debug("\(count) network start")
```

요런식으로 사용이 가능하도록 바뀜

>지속적이고 효율적인 로깅

Debug는 휘발성이고,

Info는 로깅 툴로 수집한 경우만 디스크에 지속

그외는 보관 한도까지 수집.. 한도가 꽉차면 제일 오래된 데이터부터 삭제.

퍼포먼스는 지속 가능 순서의 역순으로 생각하면 되겠다.

![스크린샷 2021-12-08 오전 10.41.17](/Users/hack/Desktop/스크린샷 2021-12-08 오전 10.41.17.png)

![스크린샷 2021-12-08 오전 10.41.21](/Users/hack/Desktop/스크린샷 2021-12-08 오전 10.41.21.png)

>Visibility

콘솔로 막 패스워드나 은행정보 같은게 노출되면 곤란하니까

비공개 처리하거나 마스킹 할 수가 있다.

```swift
os_log(“Bank account number %{private}s, “, log: log, type: .info, 00011112222)
logger.log(“Bank account number \(XXXXXXXX, privacy: .private)”)
logger.log(“Bank account number \(XXXXXXXX, privacy: .private(mask: .hash))”)
```



> 로그 아카이브

콘솔에서 아래와 같은 명령으로 아카이브를 열고 필터링하여 로그를 열어 문제를 찾을 수 있다.

```swift
log collect --device --start '2020-06-22 9:41:00' --output yourapp.logarchive
```



관련해서 아프리카TV에 통합 로깅을 적용해서 써야겠다는 생각으로

UnifiedLogging.swift를 추가해 넣었다.

사용방법은

Log.debug("메세지", "1", "2", 3")

과 같고

ios14부터는 Logger로 

그 아래 버전은 기존 os_log로 동작하도록 분기 되어있다.

현재 파이어베이스에 노출되는 정보로 디버깅하고 있지만

테이블셀과 같이 데이터 리프레시가 잦아서 파이어베이스에 전달하기가 애매한 경우

도움이 될 것 같다.

점차 print문 사용을 피하고 전부다 바꿔가야겠지만.. 

