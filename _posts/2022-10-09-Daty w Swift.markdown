*Konwersja dat w swift*


Zamiana daty na string

``` Swift
let currentDate = Date()
let dateFormatter = DateFormatter()
dateFormatter.dateFormat = "YYYY-MM-dd"

let currentDayString = dateFormatter.string(from: currentDate)
```
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

przykłady formatów:

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
