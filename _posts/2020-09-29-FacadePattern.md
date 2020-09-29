---
title: "Facade Pattern"
date: 2020-09-29 22:50:00 -0400
categories: pattern
---

### QUESTION
API의 복잡성을 간단한 인터페이스 뒤로 숨겨서 단순화
### SOLUTION
```markdown
struct Hotel {
    
}

struct HotelBooking {
    static func getHotelNameForDates(to:NSDate, from:NSDate) -> [Hotel]? {
        let hotels = [Hotel]()
        return hotels
    }
    
    static func bookHotel(hotel: Hotel) {
        
    }
}

struct Flight {

}

struct FlightBooking {
    static func getFlightNameForDates(to:NSDate, from:NSDate) -> [Flight]? {
        let flights = [Flight]()
        return flights
    }
    
    static func bookFlight(flight: Flight) {
        
    }
}

struct TravelFacade {
    var hotels: [Hotel]?
    var flights: [Flight]?
    
    init(to: NSDate, from: NSDate) {
        hotels = HotelBooking.getHotelNameForDates(to: to, from: from)
        flights = FlightBooking.getFlightNameForDates(to: to, from: from)
    }
    
    func bookTrip(hotel: Hotel, flight: Flight) {
        HotelBooking.bookHotel(hotel: hotel)
        FlightBooking.bookFlight(flight: flight)
    }
}
```
