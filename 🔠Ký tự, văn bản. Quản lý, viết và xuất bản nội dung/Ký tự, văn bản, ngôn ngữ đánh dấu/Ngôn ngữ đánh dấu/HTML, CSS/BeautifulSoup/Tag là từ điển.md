---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
---
```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>', 'html.parser')
tag = soup.b
type(tag)
# <class 'bs4.element.Tag'>
```

```python
tag = BeautifulSoup('<b id="boldest">bold</b>', 'html.parser').b
tag['id']
# 'boldest'
```
Nguồn:: [Beautiful Soup Documentation — Beautiful Soup 4.12.0 documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#bs4.Tag.attrs) 
[[Những vật thể đơn giản dùng để tra cứu dữ liệu theo từ khoá gọi là từ điển]]. [[Vật thể là dạng dữ liệu có những thuộc tính thành phần]]