---
share: true
created: 2023-10-30T14:29
updated: 2024-05-14T12:21
---
It is important because signals are reactive, meaning they need to keep track of who is interested in the state and notify subscribers of state changes. This is achieved by observing the context in which the state-getter is invoked, which creates a subscription.

In contrast, `useState()` in React returns only the state-value, meaning it has no idea how the state-value is used and must re-render the whole component tree in response to state changes.
Nguồn:: [useSignal() is the Future of Web Frameworks](https://www.builder.io/blog/usesignal-is-the-future-of-web-frameworks)

---

# Đơn giản hoá quản lý state với preact-signal

# 1. Quản lý State trong react và những bất lợi

- Khi xây dựng ứng dụng Front-end, việc quản lý trạng thái (state) là không thể thiếu. Trạng thái đại diện cho những dữ liệu mà ứng dụng theo dõi và hiển thị cho người dùng. React giúp đơn giản hóa quá trình này bằng cách cung cấp các Hooks như useState, useEffect, và useMemo.
- Do useState() trả về value và setter nên nó sẽ không thể biết value cụ thể được sử dụng ở đâu trong component. Điều này có nghĩa là sau khi gọi setter, React sẽ không biết được phần nào của component đã thay đổi để cập nhật, do đó nó sẽ phải re-render cả component. Dự án càng lớn, component càng lớn thì sẽ càng tốn thời gian re-render.
- Một vấn đề khác rất hay gặp phải là trường hợp nhiều component cùng truy cập đến cùng 1 state nhất định. Với useState(), chúng ta sẽ phải sử dụng kỹ thuật "lifting state up" (tức là chuyển nơi khai báo state đến component cha gần nhất chứa các component cần sử dụng state trên, sau đó truyền state xuống các component con thông qua properties)  
    Cùng xem ví dụ sau về 1 app hiển thị ảnh động vật dưới đây:

```tsx
// Container.tsx
const Container: React.FC = () => {
 const [generating, setGenerating] = useState(false);
 const [result, setResult] = useState<Image[]>([]);
 return (
   <div className={styles.container}>
     <Form generating={generating} result={result} setResult={setResult}
       setGenerating={setGenerating}
     />
     <Result result={result} setResult={setResult} generating={generating} />
   </div>
 );
};
```

_Container chứa 2 component trên trang_  
  

```tsx
// Result.tsx
const Result: FC<Props> = ({ generating, result = [], setResult }) => {
 const [mainImgIndex, setMainImgIndex] = useState<number>(0);
 return (
   <div className={classNames(styles.result, styles.right)}>
     <section className={styles.mainImg}>
       {generating ? <FcProcess className={styles.icon} size={40} />
       : result.length > 0 && <img src={getImageURL(result[mainImgIndex].url)} alt="image" />}
     </section>
     <section className={styles.subImgs}>
      {result?.map((image, index) => (<img
         key={index}
         src={getImageURL(image.url)}
         onClick={() => changeMainImg(index)}
      />))}
     </section>
   </div>
 );
};
```

_Trong Result thì đơn giản chỉ là hiện các ảnh đã gen_  
  

```tsx
//Form.tsx
const Form: FC<Props> = ({ generating, result, setResult, setGenerating }) => {
 const [input, setInput] = useState("");
    const handleSubmit = async () => {
      setGenerating(true);
      const data = await generateImage(input);
      setResult((prev) => prev.concat({ id: data.id, url: data.url }));
      setGenerating(false);
    };
    useEffect(() => {console.log(result)}, [imageCount]);
    return (
      <fieldset className={styles.form} disabled={generating}>
        <label className={styles.label} htmlFor="promptInput">Enter Animal</label>
        <Textarea value={input} onChange={(e) => setInput(e.target.value)} />
        <Button className={styles.submitButton} onClick={handleSubmit}>
          {generating ? <FcSynchronize /> : <FcServices />} Submit
        </Button>
      </fieldset>
    );
  };
```

_Form nhập tên con vật muốn generate_  
  

![result img](https://images.viblo.asia/eca86ac6-77ab-4e86-ab0f-eb1b98f103b5.png)

Đây là 1 ví dụ đơn giản về việc "lifting state up". State sẽ được khởi tạo trong component cha gần nhất chứa các component dùng state đó, sau đó sẽ truyền value và setter xuống các component con để chúng sử dụng. Trong các dự án thực tế rất có thể còn nhiều hơn nữa các component trung gian nằm giữa component Container và Result. Việc truyền state qua trung gian thực sự là một cơn ác mộng; hơn nữa, mỗi khi state được thay đổi, component khởi tạo state và tất cả component nằm dưới nó trong DOM đều sẽ phải re-render.

# 2. Giới thiệu về preact-signal

Vì những vấn đề trên, mình có thử tìm hiểu các thư viện thay thế, và mình tìm thấy preact-signal, nó giúp mình giải quyết các vấn đề trên. Cụ thể preact-signal là gì? Signal giúp đơn giản hóa quá trình quản lý state. Khác biệt mấu chốt ở đây là thay vì trả về value và setter, signal sẽ trả về getter và setter, getter sẽ giúp signal biết nơi nào đang sử dụng state, và khi giá trị thay đổi, những nơi gọi getter đó sẽ được tính toán lại mà không cần re-render lại cả component. Signal trả về 1 object với thuộc tính .value chứa giá trị của state, nó vừa có thể lấy giá trị ra (getter) và cũng có thể dùng để gán lại giá trị cho state (setter) (như 1 object thông thường).

## 2.1. Cài đặt và sử dụng

Tuỳ vào công nghệ dự án sử dụng mà cần cài package Signal phù hợp. Đối với dự án React, ta cần thêm package [@preact](https://viblo.asia/u/preact)/signals-react

```tsx
npm install @preact/signals-react
hoặc
yarn add @preact/signals-react
```

_Ta sẽ sử dụng signal và sửa lại component Form phía trên 1 chút:_

```tsx
 // const [input, setInput] = useState("");
 const inputSignal = useSignal("");
 console.log("check re-render", inputSignal);
```

_useSignal() dùng để khởi tạo state và “” là giá trị mặc định khi khởi tạo._

```
 // value={input}
 // onChange={(e) => setInput(e.target.value)}
 value={inputSignal}
 onChange={(e) => (inputSignal.value = e.target.value)}
```

_Mỗi khi nhập 1 ký tự, ta sẽ update lại giá trị cho state_

Và đây là kết quả

![](https://images.viblo.asia/fdf96c10-3c3f-49aa-8ccc-4f9682c58338.png)

_console.log("check re-render", inputSignal); không chạy mỗi khi nhập 1 ký tự do component không cần re-render._  
  
Tiếp theo là đến vấn đề truy cập cùng 1 state giữa các component ở các vị trí khác nhau. Signal cho phép chúng ta khai báo state ở cả bên trong hoặc bên ngoài component, do đó muốn các component khác truy cập tới thì ta chỉ cần đơn giản là khai báo state ở ngoài component rồi export nó ra như biến hoặc function thông thường thôi.  
Để khai báo state ngoài component, ta dùng method signal(),

```tsx
//Container.tsx
import { signal } from "@preact/signals-react";
export const generating = signal(false);
export const result = signal<Image[]>([]);
const Container: React.FC = () => {
 return (
   <div className={styles.container}><Form /><Result /></div>
 );
};
```

Ta cũng có thể đưa các khác báo signal ra các file riêng để quản lý chúng dễ dàng hơn.

_Form.tsx và Result.tsx ta chỉ cần import signal như biến thông thường_

`import { generating, result } from "../Container";`

Đơn giản đúng không nào? Việc này còn giúp các component không thực sự sử dụng state (Container) sẽ không phải re-render khi state đó thay đổi.

## 2.2. Một số ứng dụng khác

Ngoài ra, preact-signal còn cung cấp thêm một số method khác cũng hữu ích không kém:

### Computed

**computed()**: khởi tạo một signal mới được tính toán (computed) dựa trên giá trị của các signal khác. Computed signal cũng trả về 1 object nhưng ở dạng read-only và giá trị của nó sẽ được tự động cập nhật khi 1 trong các signal khác mà nói sử dụng được cập nhật (khá giống với useMemo() của React nhưng không cần truyền mảng dependencies vì computed() sẽ tự detect chúng). const count = signal(0); const addition = signal(2); const double = computed(() => count.value * 2 + addition.value);

Trong trường hợp ta không muốn double update khi addition thay đổi, ta có thể sử dụng addition.peek() để lấy giá trị mà không cần lắng nghe sự thay đổi của nó. Nhưng tất nhiên việc này rất hiếm khi xảy ra, vì hầu hết ta đều muốn state update khi phụ thuộc của nó thay đổi.

### Effect

**effect()**: thực hiện 1 function nào đó khi các signal được sử dụng bên trong function thay đổi (tương tự useEffect() và cũng không cần truyền mảng dependencies).

```tsx
const count = signal(0);
effect(() => console.log(`Count value has change to ${count.value}`));
```

Tương tự như computed(), chúng ta cũng có thể sử dụng .peek() để từ chối lắng nghe sự thay đổi của dependency signal. effect() sẽ không return signal, mà nó sẽ trả về 1 function tự huỷ chính nó (unsubscribe). Nghĩa là khi function tự huỷ được gọi đến thì effect() của n sẽ không tự động chạy khi có dependency signal thay đổi nữa.

```tsx
const count = signal(0);
const double = computed(() => count.value * 2);
const dispose = effect(() => {
 if (count.value === 3) {
   console.log("Count reached 3");
   dispose();
 }
 console.log("Count current", count.value);
});
const Test: React.FC = () => {
 console.log("Double current", double.value);
 return (
   <div>
     <button onClick={() => count.value++}>Increment</button>
     <div>Count: {double}</div>
   </div>
 );
};
```

Kết quả:

![](https://images.viblo.asia/3bd256cb-5af1-4554-83e6-5a201b54f1d4.png)

_Ta có thể thấy khi count = 3, function trong effect sẽ không được gọi nữa_

# Kết luận

Signal là một cách khác để lưu trữ state trong ứng dụng, thay vì trả về một giá trị và một hàm setter, signal trả về một hàm getter và một hàm setter. Từ hàm getter, signal có thể biết ngay được component nào đang sử dụng trạng thái và phản ứng lại cho chúng 1 cách nhanh chóng mà không cần phải để dev khai báo các dependencies.

Hy vọng sau bài viết này các bạn sẽ nhận thấy rằng việc sử dụng signal có thể giúp đơn giản hóa quá trình quản lý trạng thái trong ứng dụng và tạo ra một trải nghiệm phát triển (DX) tốt hơn. Nếu bạn đang tìm kiếm một cách tiếp cận mới để quản lý state trong ứng dụng của mình, thì preact-signal có thể là một lựa chọn hữu ích.

Hãy thử nghiệm và khám phá cách preact-signal có thể giúp tối ưu hóa quá trình phát triển ứng dụng của bạn nhé. Chúc bạn may mắn!

Nguồn:: [[Viblo]], [Đơn giản hoá quản lý state với preact-signal](https://viblo.asia/p/don-gian-hoa-quan-ly-state-voi-preact-signal-5OXLAPzvJGr)
yup, useState will always re-render everything starting from the component it was defined in, unless you manually opt out of that through memoization further down in a component. Signals will only update starting from the component they are accessed in. Passing them to attributes or text directly bypasses component rendering. So it has the chance of eliminating rendering

Nguồn:: [Discord](https://discord.com/channels/684898665143206084/991511118524715139/1238162003965775984)