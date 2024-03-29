---
title: "Log code sample"
date: 2020-10-03 08:49:00 -0400
categories: pattern
---

### CODE
~~~ swift
protocol LoggerProfile {
    var loggerProfileId: String {get}
    func writeLog(level: String, message: String)
}

extension LoggerProfile {
    func getCurrentDateString() -> String {
        let date = Date()
        let dateFormatter = DateFormatter()
        dateFormatter.dateFormat = "MM/dd/yyyy hh:mm"
        return dateFormatter.string(from: date)
    }
}

struct LoggerNull: LoggerProfile {
    let loggerProfileId: String = "hoffman.jon.logger.null"
    func writeLog(level: String, message: String) {
        //Do nothing
    }
}

struct LoggerConsole: LoggerProfile {
    let loggerProfileId: String = "hoffman.jon.logger.console"
    func writeLog(level: String, message: String) {
        let now = getCurrentDateString()
        print("\(now): \(level) - \(message)")
    }
}

struct LoggerRemote: LoggerProfile {
    let loggerProfileId: String = "hoffman.jon.logger.remote"
    func writeLog(level: String, message: String) {
        let now = getCurrentDateString()
        print("\(now): \(level) - \(message)")
    }
}

enum LogLevels: String {
    case Fatal
    case Error
    case Warn
    case Debug
    case Info
    
    static let allValues = [Fatal, Error, Warn, Debug, Info]
}

protocol Logger {
    static var loggers: [LogLevels:[LoggerProfile]] {get set}
    static func writeLog(logLevel: LogLevels, message: String)
}

extension Logger {
    static func logLevelContainsProfile(logLevel: LogLevels, loggerProfile: LoggerProfile) -> Bool {
        if let logProfiles = loggers[logLevel] {
            for logProfile in logProfiles where logProfile.loggerProfileId == loggerProfile.loggerProfileId {
                return true
            }
        }
        return false
    }
    
    static func setLogLevel(logLevel: LogLevels, loggerProfile: LoggerProfile) {
        if let _ = loggers[logLevel] {
            if !logLevelContainsProfile(logLevel: logLevel, loggerProfile: loggerProfile) {
                loggers[logLevel]?.append(loggerProfile)
            }
        } else {
            var a = [LoggerProfile]()
            a.append(loggerProfile)
            loggers[logLevel] = a
        }
    }
    
    static func addLogProfileToAllLevels(defaultLoggerProfile: LoggerProfile) {
        for level in LogLevels.allValues {
            setLogLevel(logLevel: level, loggerProfile: defaultLoggerProfile)
        }
    }
    
    static func removeLogProfileFromLevel(logLevel: LogLevels, loggerProfile:LoggerProfile) {
        if var logProfiles = loggers[logLevel] {
            if let index = logProfiles.firstIndex(where: {$0.loggerProfileId == loggerProfile.loggerProfileId}) {
                logProfiles.remove(at: index)
            }
            loggers[logLevel] = logProfiles
        }
    }
    
    static func removeLogProfileFromAllLevels(loggerProfile: LoggerProfile) {
        for level in LogLevels.allValues {
            removeLogProfileFromLevel(logLevel: level, loggerProfile: loggerProfile)
        }
    }
    
    static func hasLoggerForLevel(logLevel: LogLevels) -> Bool {
        guard let logProfiles = loggers[logLevel] else {
            return false
        }
        
        return !logProfiles.isEmpty
    }
}

struct MyLogger: Logger {
    static var loggers = [LogLevels : [LoggerProfile]]()
    static func writeLog(logLevel: LogLevels, message: String) {
        guard hasLoggerForLevel(logLevel: logLevel) else {
            print("No logger")
            return
        }
        
        if let logProfiles = loggers[logLevel] {
            for logProfiles in logProfiles {
                logProfiles.writeLog(level: logLevel.rawValue, message: message)
            }
        }
    }
}

MyLogger.addLogProfileToAllLevels(defaultLoggerProfile: LoggerConsole())
MyLogger.writeLog(logLevel: .Debug, message: "Debug Message 1")
MyLogger.writeLog(logLevel: .Debug, message: "Debug Message 2")
MyLogger.writeLog(logLevel: .Error, message: "Error Message 1")
MyLogger.writeLog(logLevel: .Error, message: "Error Message 2")
~~~
