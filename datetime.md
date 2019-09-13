
### This tutorial helps towards practicing Datetime module from python

* The contents are form https://www.programiz.com/python-programming/datetime


```python
import datetime
```


```python
# Check classes of the module (What's inside datetime?)
dir(datetime)
```




    ['MAXYEAR',
     'MINYEAR',
     '__builtins__',
     '__cached__',
     '__doc__',
     '__file__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     'date',
     'datetime',
     'datetime_CAPI',
     'sys',
     'time',
     'timedelta',
     'timezone',
     'tzinfo']




```python
# Create Date object to represent a date
# Check the type
d = datetime.date(2019, 4, 13)
print(d)
print(type(d))
print('What is the data type?', 'datetime.date')
```

    2019-04-13
    <class 'datetime.date'>
    What is the data type? datetime.date
    


```python
# Get LOCAL Current Date
print(datetime.date.today())
print(type(datetime.date.today()))
```

    2019-09-13
    <class 'datetime.date'>
    


```python
# Get LOCAL Current Date and Time
print(datetime.datetime.now())
print(type(datetime.datetime.now()))
```

    2019-09-13 13:15:11.592734
    <class 'datetime.datetime'>
    


```python
# Get date from a timestamp
# A Unix timestamp is the number of seconds between a particular date and January 1, 1970 at UTC. 
# You can convert a timestamp to date using fromtimestamp() method.
from datetime import date
timestamp = date.fromtimestamp(1326244364)
print("Date =", timestamp)
print('type is:',type('Date'))
```

    Date = 2012-01-11
    type is: <class 'str'>
    


```python
# Print today's year, month and day

from datetime import date
# date object of today's date
today = date.today() 
print("Current year:", today.year)
print("Current month:", today.month)
print("Current day:", today.day)

```

    Current year: 2019
    Current month: 9
    Current day: 12
    


```python
datetime.date.today().weekday() #Monday==0, Sunday==6
```




    4




```python
# Get today's day of the month
print(datetime.date.today().day)
# Get today's month
print(datetime.date.today().month)
# Get today's year
print(datetime.date.today().year)
# Get current time
print(datetime.time())
print(type(datetime.time()))

```

    13
    9
    2019
    00:00:00
    <class 'datetime.time'>
    


```python
# Time object to represent time
from datetime import time
# time(hour = 0, minute = 0, second = 0)
a = time()
print("a =", a)
# time(hour, minute and second)
b = time(11, 34, 56)
print("b =", b)
# time(hour, minute and second)
c = time(hour = 11, minute = 34, second = 56)
print("c =", c)
# time(hour, minute, second, microsecond)
d = time(11, 34, 56, 234566)
print("d =", d)
e = time(11, 34, 56, 1234566) # ValueError: microsecond must be in 0..999999 ('Why two periods after 0?')
```

    a = 00:00:00
    b = 11:34:56
    c = 11:34:56
    d = 11:34:56.234566
    


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-23-392a179fe008> in <module>
         13 d = time(11, 34, 56, 234566)
         14 print("d =", d)
    ---> 15 e = time(11, 34, 56, 1234566) # ValueError: microsecond must be in 0..999999 ('Why two periods after 0?')
    

    ValueError: microsecond must be in 0..999999



```python
# Print hour, minute, second and microsecond

from datetime import time
a = time(11, 34, 56)
print("hour =", a.hour)
print("minute =", a.minute)
print("second =", a.second)
print("microsecond =", a.microsecond)
```

    hour = 11
    minute = 34
    second = 56
    microsecond = 0
    


```python
# Python datetime object

# datetime.datetime
# The datetime module has a class named dateclass 
# that can contain information from both date and time objects.

from datetime import datetime
# datetime(year, month, day)
a = datetime(2018, 11, 28)
print('a =',a,'\n')
# datetime(year, month, day, hour, minute, second, microsecond)
b = datetime(2017, 11, 28, 23, 55, 59, 342380)
print('b =',b)
print('\n')
print("a.year =", a.year)
print("a.month =", a.month)
print("a.hour =", a.hour)
print("a.minute =", a.minute)
print("a.timestamp =", a.timestamp())
print('\n')
print("b.year =", b.year)
print("b.month =", b.month)
print("b.hour =", b.hour)
print("b.minute =", b.minute)
print("b.timestamp =", b.timestamp())



```

    a = 2018-11-28 00:00:00 
    
    b = 2017-11-28 23:55:59.342380
    
    
    a.year = 2018
    a.month = 11
    a.hour = 0
    a.minute = 0
    a.timestamp = 1543359600.0
    
    
    b.year = 2017
    b.month = 11
    b.hour = 23
    b.minute = 55
    b.timestamp = 1511909759.34238
    


```python
# datetime.timedelta

#A timedelta object represents the difference between two dates or two times.

from datetime import datetime, date
t1 = date(year = 2018, month = 7, day = 12)
t2 = date(year = 2017, month = 12, day = 23)
t3 = t1 - t2
print("t3 =", t3)
t4 = datetime(year = 2018, month = 7, day = 12, hour = 7, minute = 9, second = 33)
t5 = datetime(year = 2019, month = 6, day = 10, hour = 5, minute = 55, second = 13)
t6 = t4 - t5
print("t6 =", t6)
print("type of t3 =", type(t3)) 
print("type of t6 =", type(t6))  


```

    t3 = 201 days, 0:00:00
    t6 = -333 days, 1:14:20
    type of t3 = <class 'datetime.timedelta'>
    type of t6 = <class 'datetime.timedelta'>
    


```python
# Difference between two timedelta objects

from datetime import timedelta
t1 = timedelta(weeks = 2, days = 5, hours = 1, seconds = 33) # month or year argument in not available in timedelta object
t2 = timedelta(days = 4, hours = 11, minutes = 4, seconds = 54)
t3 = t1 - t2
print("t3 =", t3)
print("type of t1 =", type(t1))
print("type of t2 =", type(t2))
print("type of t3 =", type(t3))
print(t2-t1) # Notice the difference between outputs of datetime.timedelta with and without print cammand 
t2-t1
```

    t3 = 14 days, 13:55:39
    type of t1 = <class 'datetime.timedelta'>
    type of t2 = <class 'datetime.timedelta'>
    type of t3 = <class 'datetime.timedelta'>
    -15 days, 10:04:21
    




    datetime.timedelta(days=-15, seconds=36261)




```python

```


```python
# Get current date
datetime.date.today()
# Get current day of the month
print(datetime.date.day)
```

    <attribute 'day' of 'datetime.date' objects>
    
