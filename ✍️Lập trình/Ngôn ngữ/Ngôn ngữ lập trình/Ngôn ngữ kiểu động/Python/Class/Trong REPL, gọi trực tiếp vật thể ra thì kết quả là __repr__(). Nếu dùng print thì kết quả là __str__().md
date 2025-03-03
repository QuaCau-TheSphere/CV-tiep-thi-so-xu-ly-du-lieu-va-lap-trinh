---
share: true
created: 2023-09-26T21:04
updated: 2025-03-03T18:48
---
```python
>>> import datetime
>>> today = datetime.datetime.now()

>>> today
datetime.datetime(2023, 2, 18, 18, 40, 2, 160890)

>>> print(today)
2023-02-18 18:40:02.160890
```
Nguồn:: [[Real Python]], [When Should You Use .\_\_repr\_\_() vs .\_\_str\_\_() in Python? – Real Python](https://realpython.com/python-repr-vs-str/)
[[__repr__() trả về mô tả chi tiết để người lập trình bảo trì và sửa lỗi. __str__() trả về mô tả đơn giản cho người dùng sử dụng]] 

```python
from datetime import datetime
class Event:
    def __init__(self, summary:str, description:str, location:str, startDate:datetime, endDate:datetime):
        self.summary = summary
        self.description = description
        self.location = location
        self.startDate = startDate
        self.endDate = endDate
    def __str__(self):
        return f'{self.summary}\t{self.startDate.strftime("%Y-%m-%d %H:%M:%S")}'
startDate = datetime(2023, 12, 14, 16, 00, 00)
endDate = datetime(2023, 12, 14, 17, 00, 00)

event = Event('summary', 'description', 'location', startDate, endDate)

print(event)
```