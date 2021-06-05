---
title: "Bridge Pattern"
date: 2020-09-29 01:024:00 -0400
categories: pattern
---

### QUESTION
구현체에서 추상화를 분리, 새로운 요구 사항에 쉽게 대응
### SOLUTION
~~~ swift
protocol Message {
    var messageString: String {get set}
    init(messageString: String)
    func prepareMessage()
}

//protocol Sender {
//    func sendMessage(message: Message)
//}

protocol Sender {
    var message: Message? {get set}
    func sendMessage()
    func verifyMessage()
}

class PlainTextMessage: Message {
    var messageString: String
    required init(messageString: String) {
        self.messageString = messageString
    }

    func prepareMessage() {

    }
}

class DESEncryptedMessage: Message {
    var messageString: String
    required init(messageString: String) {
        self.messageString = messageString
    }
    func prepareMessage() {
        self.messageString = "DES: " + self.messageString
    }
}

//class EmailSender: Sender {
//    func sendMessage(message: Message) {
//        print("Sending through E-mail:")
//        print("\(message.messageString)")
//    }
//}
//
//class SMSSender: Sender {
//    func sendMessage(message: Message) {
//        print("Sending through SMS:")
//        print("\(message.messageString)")
//    }
//}

class EmailSender: Sender {
    var message: Message?
    func sendMessage() {
        print("Sending through E-Mail:")
        print("\(message!.messageString)")
    }
    func verifyMessage() {
        print("Verifying E-Mail message")
    }
}

class SMSSender: Sender {
    var message: Message?
    func sendMessage() {
        print("Sending through SMS:")
        print("\(message!.messageString)")
    }
    func verifyMessage() {
        print("Verifying SMS message")
    }
}

var myMessage = PlainTextMessage(messageString: "Plain Text Message")
myMessage.prepareMessage()
var sender = SMSSender()
sender.message = myMessage
sender.verifyMessage()
sender.sendMessage()


struct MessagingBridge {
    static func sendMessage(message: Message, sender: Sender) {
        var sender = sender
        message.prepareMessage()
        sender.message = message
        sender.verifyMessage()
        sender.sendMessage()
    }
}

let message = DESEncryptedMessage.init(messageString: "whatIsThis")
let smsSender = SMSSender.init()
let messagingBridge = MessagingBridge.init()
MessagingBridge.sendMessage(message: message, sender: smsSender)

~~~
