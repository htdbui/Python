---
title: "Datetime Object"
author: "db"
---

# datetime.date Object
- Ngày tháng nam 
## Creating a Date
```
from datetime import date
birthday = date(1989, 12, 13)
birthday
print(birthday)
# Not exist date
not_a_date = date(2005, 2, 29)
```
## Methods
### binary operator
```
date.today() - birthday
```
### comparison operator
```
birthday < date.today()
```
### today()
```
date.today()
```
### weekday()
Mon = 0, Tue = 1, Wed = 2, Thu = 3, Fri = 4, Sam = 5, Sun = 6
```
birthday.weekday()
```
### isoformat()
ISO 8601 YYYY-MM-DD
```
birthday.isoformat()
```
### isoweekday()
Mon = 1, Tue = 2, Wed = 3, Thu = 4, Fri = 5, Sam = 6, Sun = 7
```
birthday.isoweekday()
```
### ctime()
C-Standard time output
```
birthday.ctime()
```

# datetime.time Object
- Gi? phút giây mili-giây
## Creating a Time
```
from datetime import time
start_time = time(hour=13, minute=30, second=45)
start_time
print(start_time)
# Not exist time
not_exist_time = time(hour=24)
```
## Methods
### isoformat()
ISO 8601 format HH:MM:SS
```
start_time.isoformat()
```
### comparing operator
```
end_time = time(15, 20, 30, 999)
end_time > start_time
```

# datetime.datetime Object
- Ngày tháng nam gi? phút giây mili-giây
## Create a Datetime
```
from datetime import datetime
datetime(2023, 1, 30, 22, 55, 59, 999999)
```
## Methods
### binary operator
```
datetime(2023, 1, 30, 22, 55, 59) - datetime(2022, 1, 30, 22, 55, 55)
```
### comparision operator
```
datetime(2023, 1, 30, 22, 55, 59) > datetime(2023, 1, 30, 22, 55, 59)
```
### now()
```
datetime.now()
```
### isoformat()
ISO 8601
```
datetime.now().isoformat()
```
### ctime()
C-Standard format
```
datetime.now().ctime()
```

# Import and Export
## strptime
String Parse Time. Parsing a string into a datetime.datetime object
```
time_string = '08:32:45 July 16, 2022'
datetime.strptime(time_string, '%H:%M:%S %B %d, %Y')
```
## strftime
String Format Time. Outputting as formatted string
<div class="alert alert-block alert-info">
- %a: Abbreviate weekday <br>
- %A: Full weekday <br>
- %w: Weekday number (Sun=0...Saturday=6) <br>
- %d: Zero-padded day of month: 01...31 <br>
- %b: Abbreviate month name (Jan...) <br>
- %B: Full month name <br>
- %m: Zero-padded month number: 01...12 <br>
- %y: Year without century <br>
- %Y: Year with century <br>
- %H: 24-hour clock hour, zero-padded: 00...23 <br>
- %I: 12-hour clock hour, zero-padded: 00...12 <br>
- %p: AM or PM <br>
- %M: Minutes: 00...59 <br>
- %S: Seconds: 00..59 <br>
- %f: Microseconds: 000000...999999 <br>
- %%: % <br>
</div>

```
birthday = date(1989, 12, 13)
birthday.strftime('%A, %d %B %Y')
a_date_time = datetime(2023, 1, 30, 21, 50, 55, 999)
a_date_time('%I:%M:%S %p on %d/%m/%y')
```
