---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
Vấn đề từ `useState`:
![Image showing how the depth of the component tree directly affects rendering performance when using standard state updates.](https://preactjs.com/signals/state-updates.png) 

Vấn đề từ context:
![Context can skip updating components until you read the value out of it. Then it's back to memoization.](https://preactjs.com/signals/context-chaos.png)

Điều kiện lý tưởng:
```jsx
// Imagine this is some global state and the whole app needs access to:
let count = 0;

function Counter() {
 return (
   <button onClick={() => count++}>
     value: {count}
   </button>
 );
}
```

Điều mà signal có thể tạo ra:
```jsx
// Imagine this is some global state that the whole app needs access to:
const count = signal(0);

function Counter() {
 return (
   <button onClick={() => count.value++}>
     Value: {count.value}
   </button>
 );
}
```
Thậm chí còn có thể viết `Value: {count.value}` cũng được. (`count++` thì không được.) 

Nguồn:: [Introducing Signals – Preact](https://preactjs.com/blog/introducing-signals/)
[Signals – Preact Guide](https://preactjs.com/guide/v10/signals/)
![Why Signals Are Better Than React Hooks - YouTube](https://youtu.be/SO8lBVWF2Y8?si=e5ufEuX6SJqA2wjO)
![PREACT Signals: Everything you need to know in 15 minutes - YouTube](https://youtu.be/aDVl8vORUUg?si=2DbxsNx-1fZxhhua)

I just refactor my code from using `useState` to signals. By being able to gather all the signals in one file, now I don't have to use so many props to send states and their setters, don't have to import many types for them, and having to manage all the variables. It just feels... great ![🫠](https://discord.com/assets/5ba2d0026109e7402c0e.svg)![🫠](https://discord.com/assets/5ba2d0026109e7402c0e.svg)![🫠](https://discord.com/assets/5ba2d0026109e7402c0e.svg)
![](https://media1.tenor.com/m/AbAExTbXCQsAAAAC/kid-kid-evil-spiderman-dance.gif) 

Nếu phải truyền setter thì dùng signal sẽ không phải truyền cả getter lẫn setter. Prop bây giờ gọn hơn nhiều, chủ yếu chỉ còn dữ liệu từ server truyền sang client, và việc tách 
Trước:
```tsx
export default function KhungTìmBàiĐăngHoặcNơiĐăng({tênDanhSách, fuse}: {tênDanhSách: TênDanhSách; fuse: Fuse}) {
  const [searchList, setSearchList] = useState<DanhSáchKếtQuảTìmKiếm>(undefined);
  const [cursor, setCursor] = useState<Cursor>(0);
  const [mụcĐượcChọn, setMục] = useState<MụcĐượcChọn>(undefined);
  const [query, setQuery] = useState<string>("");
  switch (tênDanhSách) {
    case "nơi đăng":
      nơiĐăngChưaXácĐịnhVịTríĐượcChọn.value =
        mụcĐượcChọn as NơiĐăngChưaXácĐịnhVịTrí;
      break;

    case "bài đăng":
      bàiĐăngĐượcChọn.value = mụcĐượcChọn as BàiĐăng;
      break;
  }
  return (
    <div id={`div-${kiểuKebab(tênDanhSách)}`} >
      <InputTìmBàiĐăngHoặcNơiĐăng fuse={fuse} tênDanhSách={tênDanhSách} />
	  <DanhSáchKếtQuảTìmKiếm
	    tênDanhSách={tênDanhSách}
	    danhSáchKếtQuảTìmKiếm={searchList}
	    cursor={cursor}
	    setCursor={setCursor}
	    setSelectedItem={setMục}
	  />
	  <ModalTạoMới
	    tênDanhSách={tênDanhSách}
	    URL={query}
	    setSelectedItem={setMục}
	  />
      <KếtQuảĐượcChọn loạiVậtThể={tênDanhSách} />
      <br />
    </div>
  );
}
```
Sau:
```tsx
export default function DivTìmBàiĐăngHoặcNơiĐăng({ tênDanhSách }: { tênDanhSách: TênDanhSách }) {
  let mụcĐượcChọn: Signal<MụcĐượcChọn>;
  let query: Signal<string>;
  let flexSearch: FlexSearchBàiĐăngHoặcNơiĐăng;
  switch (tênDanhSách) {
    case "bài đăng":
      mụcĐượcChọn = bàiĐăngĐượcChọn;
      query = queryBàiĐăng;
      flexSearch = flexSearchBàiĐăngSignal.value;
      break;
    case "nơi đăng":
      mụcĐượcChọn = nơiĐăngChưaXácĐịnhVịTríĐượcChọn;
      query = queryNơiĐăng;
      flexSearch = flexSearchNơiĐăngSignal.value;
      break;
  }
  return (
    <div id={`div-tìm-${kiểuKebab(tênDanhSách)}`}>
      <InputTìmBàiĐăngHoặcNơiĐăng tênDanhSách={tênDanhSách} mụcĐượcChọn={mụcĐượcChọn} query={query} flexSearch={flexSearch} />
      <DanhSáchKếtQuảTìmKiếm tênDanhSách={tênDanhSách} mụcĐượcChọn={mụcĐượcChọn} query={query} />
      <KếtQuảĐượcChọn loạiVậtThể={tênDanhSách} />
      <ModalTạoMới tênDanhSách={tênDanhSách} mụcĐượcChọn={mụcĐượcChọn} />
    </div>
  );
}
```

[[Dùng setState gọn hơn signal nếu không phải truyền setter qua nhiều hàm khác nhau]]