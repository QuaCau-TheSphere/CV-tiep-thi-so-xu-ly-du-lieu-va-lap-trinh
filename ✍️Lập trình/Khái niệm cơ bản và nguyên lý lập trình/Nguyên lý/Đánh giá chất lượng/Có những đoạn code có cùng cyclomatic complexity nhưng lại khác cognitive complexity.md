---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
Hai đoạn code dưới đây đều có cyclomatic complexity là 4, nhưng khi xét về cognitive complexity thì cái đầu là 7, cái sau là 1:

```c
int sumOfPrimes(int max) { // +1
    int total = 0;
    OUT: for (int i = 1; i <= max; ++i) { // +1
        for (int j = 2; j < i; ++j) { // +1
            if (i % j == 0) { // +1
                continue OUT;
            }
        }
        total += i;
    }
    return total;
} // Cyclomatic Complexity 4
```
```c
String getWords(int number) { // +1
    switch (number) {
        case 1: // +1
            return “one”;
        case 2: // +1
            return “a couple”;
        case 3: // +1
            return “a few”;
        default:
            return “lots”;
    }
} 
```
Nguồn:: ![[Cognitive_Complexity_Sonar_Guide_2023.pdf]]