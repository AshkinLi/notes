[⬆ 返回顶部 ⬆](#)

---

- [CalendarView](#calendarview)

---

## CalendarView

```Swift
//
//  CalendarView.swift
//  Cocount
//
//  Created by Ashkin on 2023-08-12.
//

import SwiftUI

struct WeekView<DateView>: View where DateView: View {
    @Environment(\.calendar) var calendar
    
    let week: Date
    let content: (Date, Bool) -> DateView
    
    init(week: Date, @ViewBuilder content: @escaping (Date, Bool) -> DateView) {
        self.week = week
        self.content = content
    }
    
    private var days: [Date] {
        guard let weekInterval = calendar.dateInterval(of: .weekOfYear, for: week)
        else { return [] }
        return calendar.generateDate(
            inside: weekInterval,
            matching: DateComponents(hour: 0, minute: 0, second: 0)
        )
    }
    
    var body: some View {
        VStack {
            HStack {
                ForEach(days, id: \.self) { date in
                    self.content(
                        date,
                        self.calendar.isDate(self.week, equalTo: date, toGranularity: .month)
                    )
                    .frame(maxWidth: .infinity)
                }
            }
            
            Divider()
        }
        .padding(.vertical, 8)
    }
}

struct MonthView<DateView>: View where DateView: View {
    @Environment(\.calendar) var calendar
    
    @State private var month: Date
    let showHeader: Bool
    let content: (Date, Bool) -> DateView
    
    init(
        month: Date,
        showHeader: Bool = true,
        @ViewBuilder content: @escaping (Date, Bool) -> DateView
    ) {
        self._month = State(initialValue: month)
        self.content = content
        self.showHeader = showHeader
    }
    
    private var weeks: [Date] {
        guard let monthInterval = calendar.dateInterval(of: .month, for: month) else {
            return []
        }
        return calendar.generateDate(
            inside: monthInterval,
            matching: DateComponents(hour: 0, minute: 0, second: 0, weekday: calendar.firstWeekday)
        )
    }
    
    func changeDateBy(_ months: Int) {
        if let date = Calendar.current.date(byAdding: .month, value: months, to: month) {
            self.month = date
        }
    }
    
    private var header: some View {
        let formatter = DateFormatter.monthAndYear
        return HStack {
            Text(formatter.string(from: month))
                .font(.title)
                .padding(.horizontal)
            
            Spacer()
            
            HStack {
                Group {
                    Button(action: {
                        self.changeDateBy(-1)
                    }) {
                        Image(systemName: "chevron.left.square")
                            .resizable()
                    }
                    
                    Button(action: {
                        
                    }) {
                        Image(systemName: "dot.square")
                            .resizable()
                    }
                    
                    Button(action: {
                        
                    }) {
                        Image(systemName: "chevron.right.square")
                            .resizable()
                    }
                }
                .foregroundColor(.blue)
                .frame(width: 25, height: 25)
            }
            .padding(.trailing, 20)
        }
        
    }
    
    var body: some View {
        VStack {
            if showHeader {
                header
            }
            
            HStack {
                ForEach(0..<7, id:\.self) { index in
                    Text(getWeekDaysSorted()[index])
                }
                .frame(maxWidth: .infinity)
            }
            .padding(.vertical, 8)
            
            ForEach(weeks, id: \.self) { week in
                WeekView(week: week, content: self.content)
            }
        }
        .gesture(DragGesture().onEnded { value in
            if value.detechDirection == .left {
                changeDateBy(-1)
            }
            if value.detechDirection == .right {
                changeDateBy(1)
            }
        })
    }
    
    func getWeekDaysSorted() -> [String] {
        var calendar = Calendar.current
        calendar.locale = Locale(identifier: Constants.LOCALE_CN)
        let weekDays = calendar.shortWeekdaySymbols
        let sortedWeekDays = Array(weekDays[calendar.firstWeekday - 1..<calendar.shortWeekdaySymbols.count] + weekDays[0..<calendar.firstWeekday - 1])
        
        return sortedWeekDays
    }
}

struct CalendarView: View  {
    @Environment(\.calendar) var calendar
    
    let interval: DateInterval
    
    init(interval: DateInterval) {
        self.interval = interval
    }
    
    private var months: [Date] {
        calendar.generateDate(
            inside: interval,
            matching: DateComponents(day: 1, hour: 0, minute: 0, second: 0)
        )
    }
    
    var body: some View {
        ScrollView(.vertical, showsIndicators: false) {
            VStack {
                ForEach(months, id: \.self) { month in
                    MonthView(month: month) { date, isDate in
                        let day = String(self.calendar.component(.day, from: date))
                        
                        Button(action: {
                            print("current date = \(day)")
                        }) {
                            Text(day)
                                .foregroundColor(isDate ? .black : .gray)
                        }
                    }
                }
            }
        }
    }
}

struct CalendarView_Preview : PreviewProvider {
    @Environment(\.calendar) static var calendar
    
    static var previews: some View {
        CalendarView(
            interval: calendar.dateInterval(of: .month, for: Date())!
        )
    }
}
```

---
