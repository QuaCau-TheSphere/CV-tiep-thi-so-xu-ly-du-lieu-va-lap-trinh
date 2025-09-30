---
share: true
created: 2023-10-30T14:29
updated: 2024-01-10T20:00
---
Chúng chỉ khác component ở chỗ là được để vào `/islands`, không phải `/components`, chứ code thì giống nhau
[[Component hàm không có trạng thái (stateless). Component lớp có trạng thái (statef)]]
The way it works in Fresh is pretty simple. Basically we pass the files in `islands/` to esbuild as an entry point. Esbuild then bundles each entry point into a JS bundle and in the browser, when we first make islands interactive, we fetch the bundled script and run that. The way esbuild (and other bundlers work), is that they track dependencies based on `import` statements. Putting a random script tag with a script URL will likely not be bundled because esbuild doesn't understand that

Nguồn:: ![#4 Components - Viên Gạch Tạo Nên Bố Cục Của React.JS | React Cơ Bản Cho Beginners Từ A đến Z - YouTube](https://youtu.be/uzYSCOwhzxw?si=FlO3xgE55oHRubtD&t=535)