---
share: true
created: 2023-10-30T14:29
updated: 2024-05-14T13:12
---
[[useEffect được sinh ra là để side effect không tự động chạy mỗi khi component được render]]
[[Trong useEffect chỉ dùng được promise, không dùng async được]] 
```ts
const [data, setData] = useState()

useEffect(() => {
  const fetchData = async () => {
    const data = await fetch('https://yourapi.com')
    const json = await response.json();
    setData(json);
  }
  // call the function
  fetchData().catch(console.error);
}, [])
```
Nguồn:: 