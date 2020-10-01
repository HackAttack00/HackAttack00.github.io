---
title: "Proxy Pattern"
date: 2020-10-02 00:38:00 -0400
categories: pattern
---

### QUESTION
추상레이어 생성이 필요할때, 의존성 있는 API를 변경해야할때
### SOLUTION
```markdown
public typealias DataFromURLCompletionClosure = (Data?) -> Void

public struct ITunesProxy {
    public func sendGetRequest(searchTeam: String, _ handler: @escaping DataFromURLCompletionClosure) {
        
        let sessionConfiguration = URLSessionConfiguration.default
        
        var url = URLComponents()
        url.scheme = "https"
        url.host = "itunes.apple.com"
        url.path = "/search"
        
        url.queryItems = [
            URLQueryItem(name: "term", value: searchTeam)
        ]
        
        if let queryUrl = url.url {
            var request = URLRequest(url: queryUrl)
            request.httpMethod = "GET"
            let urlSession = URLSession(configuration: sessionConfiguration, delegate: nil, delegateQueue: nil)
            let sessionTask = urlSession.dataTask(with: request) {
                (data, response, error) in
                handler(data)
            }
            
            sessionTask.resume()
        }
    }
}

let proxy = ITunesProxy()
proxy.sendGetRequest(searchTeam: "jimmy_buffett", {
                        if let data = $0, let sString = String(data:data, encoding: String.Encoding(rawValue: String.Encoding.utf8.rawValue)) {
                            print(sString)
                        } else {
                            print("Data is nil")
                        }
})
```
