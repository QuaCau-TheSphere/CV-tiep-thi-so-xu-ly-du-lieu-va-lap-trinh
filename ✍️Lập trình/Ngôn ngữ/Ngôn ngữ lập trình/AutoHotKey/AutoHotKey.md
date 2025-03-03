---
share: true
created: 2023-05-30T15:56
updated: 2025-03-03T18:48
---
# Tạo phím tắt bằng AutoHotKey
AutoHotKey là một phần mềm hỗ trợ người dùng Window, giúp thực hiện các thao tác nhanh và thuận tiện hơn, phù hợp với người làm văn phòng.

Thay thế các nút vô dụng trên bàn phím, như <kbd>F1</kbd>, <kbd>Pause</kbd> bằng các nút khác
```
::->::→
:*:<->::↔
:*:(::() {Left 2}
;~ :*:'::'' {Left 2}
:*:"::"" {Left 2}
:*:[::{[ 2}{bs}}{]} {Left 2}
:*:{::{{ 2}{bs}{}} {Left 2}
:*:\cross::❌❌
:*:\check:✔️✅
:*:lnaiv::[naïve realism](https://en.wikipedia.org/wiki/Na%C3%AFve_realism_(psychology\))
:*:lsce::[self-conscious emotions](https://en.wikipedia.org/wiki/Self-conscious_emotions)
:*:chaoban::Chào bạn. Cho mình hỏi bạn là ai vậy? Cám ơn nhé
Capslock::Ctrl
+NumLock::CapsLock
```
![](https://youtu.be/YmQPxkS3HjQ) 


The thing is, even when it was a terrible language, AHK was still worth using. Nothing else filled or even cared about its niche: modifying the behavior of other programs. Normally, if I want to extend a program, I need to use its plugin system. That means learning:

1. The provided APIs
2. The capabilities, limits, and idiosyncrasies of the system
3. The entire development environment needed to write plugins in whatever language
4. How to actually deploy the plugin, which always takes way more time than I’d hope.

And that’s _if_ there’s a plugin system in the first place; there is no way to extend the desktop Spotify app short of writing a new client from scratch.
Trích từ:: [Somehow AutoHotKey is kinda good now](https://www.hillelwayne.com/post/ahk-v2/#fnref:caveat)

