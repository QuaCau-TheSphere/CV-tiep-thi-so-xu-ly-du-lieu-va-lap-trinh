---
share: true
created: 2023-10-24T18:26
updated: 2023-10-30T18:19
---
- Install expat library (`sudo apt install libexpat1-dev`)
- Install pangocairo library (`sudo apt install libpango1.0-dev`)
- Compile and install graphviz from source ([https://graphviz.org/download/source/](https://graphviz.org/download/source/)):
	```xml
	./configure --with-pangocairo
	make
	sudo make install
	```
    
Nguồn:: [[✍️ Lập trình/Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [Why do texts with non-ASCII characters have right padding?](https://stackoverflow.com/a/76630218/3416774)
