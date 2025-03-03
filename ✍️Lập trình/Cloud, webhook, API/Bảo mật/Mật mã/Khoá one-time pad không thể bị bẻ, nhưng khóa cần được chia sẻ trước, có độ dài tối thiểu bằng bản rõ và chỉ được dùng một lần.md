---
share: true
created: 2023-10-30T14:29
updated: 2025-03-03T18:48
description: One time pad (OTP) là một phương pháp mã hóa dữ liệu an toàn tuyệt đối. Tuy nhiên nó lại không mấy hữu ích trong thực tế. Nguyên nhân do đâu?
---
### One time pad, phương pháp mã hóa hoàn hảo

One time pad (OTP) là một phương pháp mã hóa đơn giản, các bước của nó như sau.

- Chuyển dữ liệu sang dạng nhị phân (ta gọi đây là plaintext).
- Sinh ngẫu nhiên một mảng dữ liệu nhị phân với chiều dài bằng chiều dài của plaintext (ta gọi đây là pad). Chú ý pad ở đây phải là `truly random`.
- XOR từng bit trong plaintext với bit ở vị trí tương ứng trong pad để được dữ liệu mã hóa (ta gọi đây là cipher).
- Để lấy plaintext từ cipher, ta chỉ cần thực hiện XOR cipher với pad.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_example.png)

OTP là phương pháp mã hóa duy nhất được chứng minh là bảo mật tuyệt đối. Nếu sử dụng đúng cách, cipher của OTP không làm lộ thêm bất kỳ thông tin gì về plaintext mà ta chưa biết từ trước. Trong ví dụ ở trên, từ cipher là `0011 1010 1101 1101` ta biết plaintext không lớn hơn 2 bytes. Tuy nhiên với mỗi dữ liệu có kích thước 2 byte trong khoảng `0000 0000 0000 0000` tới `1111 1111 1111 1111`, ta đều có thể tìm được một pad tương ứng mà khi XOR với cipher ta thu lại được dữ liệu đó. Và vì pad là `truly random` nên nếu không biết pad, ta không có cách nào giải mã được cipher ngoài cách đoán mò.

### One time pad, phương pháp mã hóa không mấy hữu ích

Nếu OTP vừa đơn giản là vừa bảo mật thì tại sao ta lại cần tới những phương pháp mã hóa khác như AES hay RSA? Đó là vì để đạt được độ bảo mật hoàn hảo, OTP cần được sử dụng đúng cách. Ta cần đáp ứng được các điều kiện sau.

- Pad phải là `truly random` và phải có độ dài ít nhất bằng với plaintext.
- Phía gửi và phía nhận đều phải biết nội dung của pad và phải giữ kín không để lộ cho bên thứ ba.
- Không được tái sử dụng pad.

Ta sẽ phân tích từng điều kiện này.

#### Pad phải là `truly random` và phải có độ dài ít nhất bằng với plaintext

Việc tạo ra dữ liệu ngẫu nhiên một cách `truly random` không dễ như ta tưởng, nhất là khi ta cần lượng dữ liệu lớn. Trong phần lớn các trường hợp, máy tính sử dụng các giải thuật để tạo dữ liệu có vẻ là ngẫu nhiên, nhưng thực ra các dữ liệu đó phụ thuộc vào một dữ liệu mồi (seed). Dữ liệu mồi đó có thể được người dùng thiết lập trước, hoặc được lấy từ những nguồn khó đoán như thời gian hệ thống hiện tại.

Một số giải thuật sinh dữ liệu giả ngẫu nhiên như [CryptGenRandom](https://en.wikipedia.org/wiki/CryptGenRandom), [Yarrow](https://en.wikipedia.org/wiki/Yarrow_algorithm) hay [Fortuna](https://en.wikipedia.org/wiki/Fortuna_\(PRNG\)) được gọi là `cryptographically-secure`. Tức là dữ liệu do chúng sinh ra hầu như không khác gì dữ liệu thực sự ngẫu nhiên, và ta có thể dùng chúng cho mục đích bảo mật.

Vậy ta có thể dùng giải thuật có tính chất `cryptographically-secure` để sinh pad cho OTP không? Rất tiếc là không, vì một sợi xích dù chắc đến đâu cũng có thể bị gãy chỉ vì một mắt xích yếu. Trong trường hợp này mã hóa của ta chỉ đạt được mức độ bảo mật là `cryptographically-secure`. Mức bảo mật này đủ để sử dụng trong thực tế, nhưng ta chưa thể gọi đó là hoàn hảo.

Ta cũng có một vài phương pháp để sinh dữ liệu thực sự ngẫu nhiên. Ta có thể đo một nguồn dữ liệu ngẫu nhiên như áp suất khí quyển, nhiệt độ môi trường hay các hiện tượng lượng tử rồi chuyển đổi nó thành dạng số. Tuy nhiên phương pháp này chậm và phức tạp. Mỗi khi cần sinh dữ liệu, ta cần đợi để thu thập đủ lượng dữ liệu ngẫu nhiên từ môi trường, và ta phải có phương án để loại trừ những sai số mang tính hệ thống trong quá trình đo đạc.

#### Phía gửi và phía nhận đều phải biết nội dung của pad và phải giữ kín không để lộ cho bên thứ ba

Điều kiện này nghe có vẻ đơn giản nhưng lại không hề dễ thực hiện. Nếu như ta có cách để chuyển một pad dài bằng plaintext cho người nhận mà không sợ bị lộ thì sao ta không dùng cách đó để chuyển luôn plaintext, sao còn phải dùng OTP? Đây chính là nhược điểm lớn nhất và nó làm hạn chế đáng kể tính ứng dụng của OTP.

Vậy ta có thể áp dụng các giải thuật trao đổi khóa (key exchange) vào OTP được không? Đúng là việc trao đổi dữ liệu một cách bảo mật trên kênh thông tin không an toàn không phải là một vấn đề mới. Những giải thuật mã hóa dùng public key như RSA đã xử lý vấn đề này tương đối ổn bằng các giải thuật như Diffie–Hellman hay ECDH. Tuy nhiên khi áp dụng chúng vào OTP, ta gặp phải hai trở ngại lớn. Trở ngại thứ nhất là các giải thuật trao đổi khóa được thiết kế cho lượng dữ liệu nhỏ, chúng không hiệu quả khi áp dụng với dữ liệu lớn như pad (nhớ là pad cần dài ít nhất bằng plaintext). Trở ngại thứ hai là không giải thuật trao đổi khóa nào là hoàn hảo, nên nếu dùng chúng thì OTP cũng không còn hoàn hảo nữa.

#### Không được tái sử dụng pad

Ta sẽ thực hiện một thử nghiệm nhỏ để thấy vì sao không được tái sử dụng pad. Đây là file ảnh thứ nhất.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_csharp.bmp)

Ta thực hiện XOR nó với một pad ngẫu nhiên. Kết quả trông khá là bảo mật.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_csharp_encrypted.bmp)

Rồi ta thử tiếp với ảnh số hai.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_java.bmp)

Ta XOR nó với cùng pad lúc trước, kết quả cũng vẫn khá bảo mật.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_java_encrypted.bmp)

Tuy nhiên khi ta XOR hai cipher ở trên với nhau, ta thu được file ảnh dưới đây.

![](https://duongnt.com/wp-content/uploads/2021/06/otp_overview_mix_encrypted.bmp)

Tuy từ từng cipher riêng lẻ ta không biết được plaintext là gì, sau khi XOR hai cipher với nhau ta lại biết được tương đối nhiều điều về cả hai plaintext. Các bạn có thể tự mình thực hiện thử nghiệm này bằng script dưới đây. Tôi dùng `urandom` để sinh pad nên đây không đúng 100% là OTP, nhưng như thế là đủ cho thử nghiệm này.

[https://gist.github.com/duongntbk/12b5bca15b7b297dbba4f9502ad46ebe](https://gist.github.com/duongntbk/12b5bca15b7b297dbba4f9502ad46ebe)

### OTP có ứng dụng nào trong thực tế?

Thật tiếc là một phương pháp mã hóa đơn giản mà an toàn như OTP lại không mấy hữu ích trong thực tế. Liệu có trường hợp nào mà OTP là phù hợp không? Thực ra là có, trong thực tế lúc ta có kênh bảo mật thì chưa chắc đã có dữ liệu để trao đổi, mà lúc có dữ liệu để trao đổi thì có khi kênh bảo mật đó đã không còn tồn tại. Nếu ta gặp trực tiếp đối tác và đưa cho họ một USB chứa sẵn dữ liệu thực sự ngẫu nhiên thì sau này ta có thể dùng dữ liệu ngẫu nhiên đó làm pad để trao đổi thông tin mà hoàn toàn không sợ bị nghe trộm. Có lẽ các bạn đã đoán được rằng OTP rất hữu ích cho hoạt động gián điệp :).

Theo tôi, ứng dụng nổi tiếng nhất của OTP là trong đường dây nóng Moscow–Washington. Đoạn trích dưới đây được lấy từ [Crypto Museum](https://www.cryptomuseum.com/crypto/hotline/index.htm).

> Rather than using American or Russian cipher machines for the encryption of the messages, the ETCRRM machines were built in Norway by STK 1, who was considered neutral and impartial.

> As the ETCRRM is a One-Time Tape machine (OTT), it uses the principle of the One-Time Pad (OTP). When used in combination with truely random key tapes, an OTT machine is absolutely safe and unbreakable. As the Russians insisted on producing their own keys, it was decided that each side would create their own key tapes.

> These key tapes were then delivered by special couriers to the embassy at the other end, who then delivered it at the other party’s terminal \[9\]. So, the American Embassy in Moscow delivered their key tapes at the Moscow hotline terminal.

Tạm dịch.

> Máy ETCRRM do Na Uy sản xuất được sử dụng để mã hóa các bản tin thay cho máy của Liên Xô hay Mỹ. Nguyên nhân là do Na Uy được coi là bên trung lập, không bên nào sợ bị thiệt.

> ETCRRM sử dụng nguyên lý One-Time Pad (OTP). Nếu sử dụng pad thực sự ngẫu nhiên, cỗ máy này có độ an toàn tuyệt đối và không sợ bị giải mã. Do Liên Xô yêu cầu họ được tự sinh pad cho mình nên cuối cùng Liên Xô và Mỹ nhất trí cả bên sẽ đều tự sinh pad.

> Pad đó được các nước chuyển tới đại sứ quán của mình bằng kiện hàng ngoại giao đặc biệt. Sau đó pad được đưa tới nơi đặt máy mã hóa. Ví dụ: đại sứ quán Mỹ ở Moscow đưa pad do Mỹ sinh cho đầu máy đặt tại Liên Xô.

### Kết thúc

Ngày nay các thiết bị lưu trữ rất rẻ mà lại có dung lượng lên tới hàng terabyte. Và mặc dù việc sinh dữ liệu thực sự ngẫu nhiên không phải là đơn giản, ta vẫn một số phương án khả thi, nhất là khi ta có đủ thời gian để chuẩn bị trước. Những điều đó cho phép bất kỳ ai cũng có thể sử dụng OTP, miễn là họ hiểu được tất cả điểm mạnh lẫn hạn chế của nó. Còn bạn thì sao, có khi nào bạn cần đến một phương pháp mã hóa an toàn tuyệt đối không?

Nguồn:: [One time pad, phương pháp mã hóa hoàn hảo nhưng lại không mấy hữu ích - Duong's Blog](https://duongnt.com/one-time-pad-vie/)

Hàm mã hoá:
```
E(m, k) = m XOR k = c
```
Hàm giải mã:
```
D(c, k) = c XOR k = (m XOR k) XOR k = m
```