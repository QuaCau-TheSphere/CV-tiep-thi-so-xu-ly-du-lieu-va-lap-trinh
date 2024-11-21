---
share: true
created: 2023-10-30T14:29
updated: 2024-11-14T20:47
---
My code:

```AutoHotKey 
#Requires AutoHotkey v2.0+ 
TextToSend := FileRead("textToSend.txt")
lines := StrSplit(TextToSend, "\n")

:*:st::{
    Loop    
        {
        SetKeyDelay 10000
        Send(lines[A_Index])
        Send, {Enter}
        Sleep 10000
    }
}
```

It used to work fine, but now the lines are rearranged. Say one line is:
```
abcdefghijkmnopqrstuvwxyz
```

Then it is sent as:
```
abcdhijkmnopqrstuvwxyzefg
```
Nguồn:: [autohotkey - Why would Send rearrange string? - Stack Overflow](https://stackoverflow.com/q/79177808/3416774)