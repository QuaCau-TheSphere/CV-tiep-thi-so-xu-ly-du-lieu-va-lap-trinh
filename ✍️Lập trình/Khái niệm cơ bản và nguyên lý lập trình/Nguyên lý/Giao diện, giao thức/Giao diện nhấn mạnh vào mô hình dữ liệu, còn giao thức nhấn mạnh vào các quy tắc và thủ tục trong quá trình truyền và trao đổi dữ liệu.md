---
share: true
created: 2023-10-30T14:29
updated: 2025-05-02T14:59
title: Giao diện và giao thức đều là những thứ các bên cần tuân thủ để sự giao tiếp được diễn ra, nhưng giao diện nhấn mạnh vào mô hình dữ liệu, còn giao thức nhấn mạnh vào các quy tắc và thủ tục trong quá trình truyền và trao đổi dữ liệu
---
[[Giao diện là cách để sử dụng vật thể mà không cần biết bên trong nó có gì]]. Đây là một ví dụ về giao diện (interface):

```
interface Communicate
{
    string SendMessageAndGetResponse(string message);
}
```

[[Giao thức là cách để các bên nhận và gửi dữ liệu hiểu nhau]]. Đây là một ví dụ về giao thức (protocol):

> 1. Gửi "Hello"
> 2. Nếu bạn nhận được phản hồi "Hi" thì hãy gửi "How are you?" và phản hồi sẽ là trạng thái
> 3. Nếu bạn nhận được bất kỳ thông tin nào khác ngoài "Hi" từ tin nhắn ban đầu thì hệ thống không hoạt động bình thường và bạn phải gửi tin nhắn "Reboot" 
> 4. Sau đó bạn sẽ nhận được "Rebooted!" nếu thành công và bất kỳ thông tin nào khác nếu không thành công

You can explore the relationship between these concepts in [Six Degree of Wikipedia](https://www.sixdegreesofwikipedia.com/?source=Interface+(computing)&target=Communication+protocol):
- Interface to protocol: [![enter image description here](https://i.sstatic.net/pzNMapLf.png)](https://i.sstatic.net/pzNMapLf.png)
- Protocol to interface: [![enter image description here](https://i.sstatic.net/65pL4rSB.png)](https://i.sstatic.net/65pL4rSB.png)

Nguồn:: [What is the difference between a protocol and an interface in general? - Stack Overflow](https://stackoverflow.com/a/64219055)