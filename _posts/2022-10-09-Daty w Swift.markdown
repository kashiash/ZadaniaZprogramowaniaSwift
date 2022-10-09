*Konwersja dat w swift*


``` Ruby
class MyClass
end
```

``` Swift
let currentDate = Date()
let dateFormatter = DateFormatter()
dateFormatter.dateFormat = "YYYY-MM-dd"

let currentDayString = dateFormatter.string(from: currentDate)
```
