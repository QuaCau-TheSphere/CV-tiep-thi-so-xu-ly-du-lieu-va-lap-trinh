---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
[[Lớp thực ra là một cú pháp ]]
```javascript
function Hero(name, level) {
    this.name = name;
    this.level = level;
}

// Adding a method to the constructor
Hero.prototype.greet = function() {
    return `${this.name} says hello.`;
}
```

Class:
```javascript
class Hero {
    constructor(name, level) {
        this.name = name;
        this.level = level;
    }

    // Adding a method to the constructor
    greet() {
        return `${this.name} says hello.`;
    }
}
```
Nguồn:: [function - JavaScript - What exactly does the "class" keyword actually do? How is it implemented? - Stack Overflow](https://stackoverflow.com/q/77602331/3416774)