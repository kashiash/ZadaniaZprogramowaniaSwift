*Konwersja dat w swift*


Zamiana daty na string

``` Swift
let currentDate = Date()
let dateFormatter = DateFormatter()
dateFormatter.dateFormat = "YYYY-MM-dd"
dateFormatter.locale = Calendar.current.locale

let currentDayString = dateFormatter.string(from: currentDate)
```

**Uwaga: Jesli nie wskazemy locale/timezone to uzywany jest czas UTC !!!**

można to zamienić na funkcję: 

``` Swift
func extractDate(date: Date, format: String) -> String{
    let formatter = DateFormatter()
    
    formatter.dateFormat = format
    return formatter.string(from: date)
}
``` 

i wywoływac np tak: 

``` Swift
print(extractDate(date: currentDate, format: "EEE")) 

print(extractDate(date: currentDate, format: "YYYY-MM-dd"))

print(extractDate(date: currentDate, format: "YY/MM/dd"))
``` 

można rozszerzyć typ Data:


``` Swift
extension Date {
   func getFormattedDate(format: String) -> String {
        let dateformat = DateFormatter()
        dateformat.dateFormat = format
      //  dateFormatter.locale = Locale(identifier: "pl-PL")
         dateFormatter.locale = Calendar.current.locale
        return dateformat.string(from: self)
    }
}
``` 

i wywoływać tak:

``` Swift
let format = date.getFormattedDate(format: "yyyy-MM-dd HH:mm:ss") 
``` 


zamiana String -> Date
``` Swift
extension String {

    func toDate(withFormat format: String = "yyyy-MM-dd HH:mm:ss")-> Date?{

        let dateFormatter = DateFormatter()
     //   dateFormatter.timeZone = TimeZone(identifier: "Asia/Tehran")
     //   dateFormatter.locale = Locale(identifier: "fa-IR")
     //   dateFormatter.calendar = Calendar(identifier: .gregorian)
        dateFormatter.locale = Calendar.current.locale

        dateFormatter.dateFormat = format
        let date = dateFormatter.date(from: self)

        return date

    }
}
``` 


przykłady formatów:
``` txt
Wednesday, Sep 12, 2018           --> EEEE, MMM d, yyyy
09/12/2018                        --> MM/dd/yyyy
09-12-2018 14:11                  --> MM-dd-yyyy HH:mm
Sep 12, 2:11 PM                   --> MMM d, h:mm a
September 2018                    --> MMMM yyyy
Sep 12, 2018                      --> MMM d, yyyy
Wed, 12 Sep 2018 14:11:54 +0000   --> E, d MMM yyyy HH:mm:ss Z
2018-09-12T14:11:54+0000          --> yyyy-MM-dd'T'HH:mm:ssZ
12.09.18                          --> dd.MM.yy
10:41:02.112                      --> HH:mm:ss.SSS
```


więcej tutaj:

http://www.unicode.org/reports/tr35/tr35-31/tr35-dates.html#Date_Format_Patterns
