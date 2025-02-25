# Tìm hiểu về Markdown 

## **1. Markdown là gì?**  

Markdown là một dạng ngôn ngữ đánh dấu đơn giản và dễ sử dụng, nó được tạo ra bởi John Gruber vào năm 2004. Hiện nay, markdown là một trong những ngôn ngữ đánh dấu phổ biến nhất thế giới. Nó thường được sử dụng để tạo tài liệu, README trên GitHub, ghi chú, blog và thậm chí cả email.

## **2. Cách sử dụng Markdown**

### **2.1. Tiêu đề**  

Có thể viết các lớp tiêu đề h1, h2, h3 cho đến h6 bằng cách thêm số lượng ký tự # tương ứng vào đầu dòng. Một ký tự # tương đương với h1, 2 ký tự # tương đương với h2...  

Ví dụ: `# h1` `## h2` `### h3` 

Output:
# h1
## h2
### h3  

### **2.2. Bôi đậm, in nghiêng**  

* **Bôi đậm:** Sử dụng 2 ký tự `**` ở đầu và cuối từ (câu) để bôi đậm từ (câu) đó.  

Ví dụ: `**Markdown**`  

Output: **Markdown**  
* **In nghiêng:** Sử dụng ký tự `*` hoặc `_` ở đầu và cuối từ (câu) để in nghiêng từ (câu) đó. 

Ví dụ: `*Markdown*`  `_Markdown_` 

Output: *Mardown*  _Markdown_  
* **Bôi đậm và in nghiêng:** Sử dụng 3 ký tự `***` hoặc `**_` và `_**` ở cuối ở đầu và cuối từ (câu) để bôi đậm và in nghiêng từ (câu) đó.  

Ví dụ: `***Markdown***` `**_Markdown_**`  

Output: ***Markdown*** **_Markdown_** 

### **2.3. Chèn link** 

Sử dụng cú pháp []() để chèn link trong bài viết, với nội dung trong [] sẽ là thẻ alt text và nội dung trong () sẽ là đường link muốn điều hướng đến.  
Ví dụ:`[Markdown](https://vi.wikipedia.org/wiki/Markdown)`  
Output: [Markdown](https://vi.wikipedia.org/wiki/Markdown)

### **2.4 Chèn ảnh**

Sử dụng cú pháp ![]() để chèn ảnh trong bài viết, với nội dung trong [] sẽ là thẻ alt text và nội dung trong () sẽ là địa chỉ ảnh.

Ví dụ: `![Ảnh 1](/QuyenNV/Markdown/images/anh1.png)`

Output: ![Ảnh 1](/QuyenNV/Markdown/images/anh1.png)

### **2.5 Danh sách**

Sử dụng - hoặc * hoặc + nếu muốn định dạng câu đó ở dạng list. Trong trường hợp muốn tạo thêm lớp level thấp hơn thì thêm 2 khoảng trắng vào nữa.

Ví dụ: `- dòng 1 - dòng 2`

Output: 
- dòng 1
  - dòng 2 

### **2.6 Blockquote**

Sử dụng > nếu muốn định dạng câu đó ở dạng quote.

Ví dụ: `> Xin chào`

Output: 
> Xin chào

### **2.7 Tạo bảng**

Để tạo bảng sử dụng cú pháp:
- Ký tự `|` tách các cột riêng lẻ trong bảng.
- Dấu `-` hoạt động như một hàng phân cách để tách header khỏi phần body.
- Dấu `:` căn chỉnh nội dung ô.

Ví dụ:  
| Cột 1  | Cột 2 | Cột 3 | Cột 4 |
|--------|-------|-------|-------|
| Hàng 2 | A     | C     | E     |
| Hàng 3 | B     | D     | F     |

### **2.8 Chèn code**

* **Code theo từ hoặc cụm từ:** Sử dụng ` hoặc ``` ở đầu và cuối câu nếu muốn định dạng câu đó ở dạng code.

Ví dụ: \`print("Hello world!")\`

Output: `print("Hello world!")`

* **Code theo đoạn/khối:** Sử dụng ba dấu ``` để bọc đoạn code nếu muốn định dạng cả đoạn đó ở dạng code.

Ví dụ: 
```
def hello():
    print("Hello world!")
```

### 2.9 Gạch ngang chữ

Sử dụng cặp dấu ~~ ở đầu và cuối câu nếu muốn gạch ngang giữa chữ của câu đó.

Ví dụ: `~~Xin chào~~`

Output: ~~Xin chào~~
