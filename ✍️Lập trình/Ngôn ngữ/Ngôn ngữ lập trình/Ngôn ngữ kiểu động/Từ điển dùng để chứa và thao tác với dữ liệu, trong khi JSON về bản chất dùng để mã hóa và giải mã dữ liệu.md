---
share: true
created: 2023-08-25T14:20
updated: 2025-03-03T18:48
---
JSON sẽ chuyển đổi dữ liệu thành một chuỗi byte có thể lưu trữ và truyền qua mạng, dùng để response cho API. Và ta dùng JSON khi muốn lưu dữ liệu ở phía server.
Nguồn:: [Tìm hiểu về JSON và sự khác nhau giữa JSON và Dictionary trong Python - Python - Magestore](https://stories.magestore.com/t/tim-hi-u-v-json-va-s-khac-nhau-gi-a-json-va-dictionary-trong-python/1247#:~:text=Dictionary%20trong%20Python%20được%20hiểu,dùng%20để%20response%20cho%20API%2e)

| JSON                                                                                 | Dictionary                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| The keys in JSON can be only strings.                                                | The keys in the dictionary can be any hashable object.                                                                                                                                           |
| In JSON, the keys are sequentially ordered and can be repeated.                      | In the dictionary, the keys cannot be repeated and must be distinct.                                                                                                                             |
| In JSON, the keys have a default value of undefined.                                 | Dictionaries do not have any default value set.                                                                                                                                                  |
| IN JSON file format, the values are accessed by using the “.”(dot) or “[]” operator. | In the dictionary, the values are mostly accessed by the subscript operator. For example, if 'dict' = {'A':'123R' ,'B':'678S'} then by simply calling dict['A'] we can access values associated. |
| We are required to use the double quotation for the string object                    | We can use either a single or double quote for the string objects                                                                                                                                |
| The return object type in JSON is a ‘string’ object type                             | The return object type in a dictionary is the ‘dict’ object type                                                                                                                                 |
Nguồn:: [Convert Dictionary to JSON Python - Scaler Topics](https://www.scaler.com/topics/convert-dictionary-to-json-python/#:~:text=Difference%20between%20dict%20and%20JSON&text=The%20keys%20in%20JSON%20can,repeated%20and%20must%20be%20distinct%2e)
[[Python tách bạch từ điển và vật thể ngay từ đầu, còn JS mãi về sau mới có từ điển]]
[[Những vật thể đơn giản dùng để tra cứu dữ liệu theo từ khoá gọi là từ điển]]
[[JSON là cách để biểu diễn vật thể ra chữ, chứ tự nó không phải là vật thể]]
