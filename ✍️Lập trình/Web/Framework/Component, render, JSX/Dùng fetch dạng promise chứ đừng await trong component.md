---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
Lý do:: [[Không có async component vì hiệu suất quá tệ]]

[[Promise được sinh ra là để không phải dùng if lồng quá nhiều]]
```js
fetch('https://jsonplaceholder.typicode.com/postses').then(function (response) {
	// The API call was successful
	// (wait, it was?)
	console.log(response.status);
	return response.json();
}).then(function (data) {
	// This is the JSON from our response
	console.log(data);
}).catch(function (error) {
	// There was an error
	console.warn(error);
});
```
Tham khảo:: [The JavaScript fetch() method | Go Make Things](https://gomakethings.com/the-javascript-fetch-method/)