---
share: true
created: 2023-10-30T14:29
updated: 2024-03-02T14:19
---

In TeX, you learn the **basic things** and use that to do what you want.

[![TeX](https://i.stack.imgur.com/IGvRS.png)](https://i.stack.imgur.com/IGvRS.png)

In LaTeX, you look for a specific package that already does what you want and use it.

[![LaTeX](https://i.stack.imgur.com/IyGwT.png)](https://i.stack.imgur.com/IyGwT.png)

The implications are:

- In TeX, you need to learn **all** the basic before being able to do most tasks. Thus the initial learning curve is steep.
    
    - But you also learn how to _program_, thus you have the power of the computer (e.g. doing repetitive task)
        
        LaTeX has e.g. `python` package, but it only has _loose_ integration with the TeX layer (e.g. it's not very easy to measure the width of a box, if you e.g. want to automatically determine column width).
        
- However, once you've learnt _all_ the basics, you can do everything1, instead of looking up a new package you define your own command to do what you want.
    
    - For a comparison, TeX is a full programming language **(imagine Python)**, and LaTeX is like a DSL (domain-specific language) **(imagine the game engines that allow you to make games without coding)**.
        
        [Wikipedia link for DSL](https://en.wikipedia.org/wiki/Domain-specific_language#External_and_Embedded_Domain_Specific_Languages). (_for whatever reason, at the moment the Wikipedia page lists LaTeX as external domain-specific language, while it's obviously embedded in TeX..._)

Nguồn:: [What is the difference between TeX and LaTeX?](https://tex.stackexchange.com/a/638092/50146)
[[TeX dùng cho máy in. LaTeX dùng cho tác giả]] 