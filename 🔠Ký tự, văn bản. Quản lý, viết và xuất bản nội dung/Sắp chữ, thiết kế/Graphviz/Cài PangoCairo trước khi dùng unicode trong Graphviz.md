---
share: true
created: 2023-10-24T18:26
updated: 2024-08-25T20:39
---
- Install expat library (`sudo apt install libexpat1-dev`)
- Install PangoCairo library (`sudo apt install libpango1.0-dev`)
- Compile and install Graphviz from [source](https://graphviz.org/download/source):
	```bash
	./configure --with-pangocairo
	make
	sudo make install
	```

Nguồn:: [[Stack Overflow]], [Why do texts with non-ASCII characters have right padding?](https://stackoverflow.com/a/76630218/3416774)
