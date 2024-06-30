---
share: true
created: 2023-10-30T14:29
updated: 2024-05-06T17:30
---
Một document có thể có nhiều article. Một article cũng có thể chứa nhiều article khác. :
```html
<article class="forecast">
  <h1>Weather forecast for Seattle</h1>
  <article class="day-forecast">
    <h2>03 March 2018</h2>
    <p>Rain.</p>
  </article>
  <article class="day-forecast">
    <h2>04 March 2018</h2>
    <p>Periods of rain.</p>
  </article>
  <article class="day-forecast">
    <h2>05 March 2018</h2>
    <p>Heavy rain.</p>
  </article>
</article>
```
![[article html tag.png]]
Nguồn:: [\<article\>: The Article Contents element - HTML: HyperText Markup Language | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article)

Tuy nhiên, nó nên dùng cho những thứ nếu tách ra khỏi web thì vẫn hiểu được
Nguồn:: [Should I use 'li' or 'article' for products listing?](https://stackoverflow.com/a/30845498/3416774)