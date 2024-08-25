---
share: true
created: 2023-08-25T14:20
updated: 2024-08-25T20:56
---
## Tạo query DQL từ danh sách các key
Do that in several steps. 
1) `^.*$` ⇒ `$& as "$&"`
2) `(?:\G|^\S*)\K\h+(?=.* as ".*"$)` ⇒ `-,`
3)  `(?:\G-|^)[^-]+(?=\S* as ".*"$)` ⇒ `\L$&`
https://stackoverflow.com/questions/75015542/how-to-convert-multiple-words-into-multiple-words-as-multiple-words

[[Tự học regex]]

