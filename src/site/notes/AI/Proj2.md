---
{"dg-publish":true,"permalink":"/ai/proj2/","tags":["gardenEntry"]}
---

Đây là nội dung tài liệu được viết lại thành các ghi chú bài giảng có cấu trúc rõ ràng, giữ nguyên 100% thông tin và ý nghĩa của văn bản gốc, nhằm truyền tải mục đích giảng dạy của slide.

---

## Dự án 02: Hashiwokakero

Đây là tài liệu dành cho môn học **CSC14003 - Nhập môn Trí tuệ Nhân tạo (Introduction to Artificial Intelligence)**, được ban hành vào ngày 15 tháng 3 năm 2025.

### Mục lục

Tài liệu dự án này bao gồm các phần chính sau:

1. Tổng quan (Overview).
2. Mô tả Dự án (Project Description).
3. Yêu cầu (Requirements):
    - 3.1 Đầu vào (Inputs).
    - 3.2 Đầu ra (Outputs).
    - 3.3 Ngôn ngữ lập trình (Programming language).
    - 3.4 Báo cáo (Report).
    - 3.5 Video minh họa (Demonstration videos).
    - 3.6 Nộp bài (Submission).
4. Đánh giá (Assessment).
5. Thông báo (Notices).

---

### 1. Tổng quan

**Hashiwokakero** (còn được gọi là **Bridges** hoặc **Hashi**) là một trò chơi giải đố logic thách thức người chơi kết nối các hòn đảo được đánh số bằng một số lượng cầu cụ thể, đồng thời phải tuân thủ một bộ quy tắc đơn giản.

Trò chơi này được xuất bản bởi Nikoli và yêu cầu **tư duy chiến lược và lập kế hoạch cẩn thận** để đảm bảo tất cả các hòn đảo được kết nối với nhau mà không vượt quá số lượng cầu cho phép trên mỗi hòn đảo.

Trò chơi đã trở nên phổ biến trên toàn thế giới dưới nhiều tên khác nhau, ví dụ như **Ai-Ki-Ai** ở Pháp, Đan Mạch, Hà Lan và Bỉ. Với thiết kế thanh lịch và chiều sâu logic, Hashiwokakero mang đến một thử thách hấp dẫn cho những người đam mê giải đố ở mọi cấp độ.

### 2. Mô tả Dự án

Hashiwokakero được chơi trên một lưới hình chữ nhật không có kích thước tiêu chuẩn, mặc dù bản thân lưới thường không được vẽ.

Một số ô ban đầu chứa các số (thường được khoanh tròn) từ 1 đến 8; đây được gọi là **"các hòn đảo"**. Các ô còn lại là ô trống.

Trong dự án này, sinh viên sẽ phát triển một **bộ giải Hashiwokakero** sử dụng logic **Dạng Chuẩn Tắc Hội (Conjunctive Normal Form - CNF)**. Mục tiêu là kết nối tất cả các hòn đảo bằng cách vẽ một loạt các cây cầu giữa chúng.

Các cây cầu phải tuân theo các tiêu chí sau:

- Chúng phải bắt đầu và kết thúc tại **hai hòn đảo riêng biệt**, di chuyển theo một đường thẳng giữa chúng.
- Chúng **không được phép cắt ngang** bất kỳ cây cầu hoặc hòn đảo nào khác.
- Chúng chỉ được phép chạy **vuông góc** (theo chiều dọc hoặc chiều ngang).
- Chỉ được phép có **tối đa hai cây cầu** kết nối một cặp đảo.
- **Số lượng cầu** được kết nối với mỗi hòn đảo phải khớp với số được ghi trên hòn đảo đó.
- Các cây cầu phải kết nối các hòn đảo thành **một nhóm kết nối duy nhất**.

Để giải quyết vấn đề này, sinh viên có thể xem xét các bước sau:

1. **Xác định Biến Logic:** Gán một biến logic cho mỗi ô của ma trận.
2. **(Báo cáo) Xây dựng Ràng buộc CNF:** Viết các ràng buộc cho các ô chứa số để có được một tập hợp các mệnh đề ràng buộc ở dạng CNF (lưu ý rằng cần loại bỏ các mệnh đề trùng lặp).
3. **(Thực hiện) Tự động Tạo CNF:** Tự động hóa quá trình tạo các CNF.
4. **(Thực hiện) Giải bằng PySAT:** Sử dụng thư viện `pysat` để tìm giá trị cho mỗi biến và suy luận ra kết quả.
5. __(Thực hiện) Áp dụng Thuật toán Tìm kiếm A_:_* Áp dụng thuật toán A* để giải CNF.
6. **(Thực hiện) So sánh với các Phương pháp khác:** Lập trình thuật toán **Brute-force (vét cạn)** và **Backtracking (quay lui)** để so sánh tốc độ (bằng cách đo thời gian chạy — khoảng thời gian máy tính cần để thực hiện một tác vụ cụ thể) và hiệu suất của chúng với thuật toán A*.

### 3. Yêu cầu (Requirements)

#### 3.1 Đầu vào (Inputs)

Sinh viên được yêu cầu thiết kế **ít nhất 10 tệp đầu vào khác nhau**. Các tệp này phải được đặt tên theo cấu trúc: `input-01.txt`, `input-02.txt`, ..., `input-10.txt`.

Ví dụ về định dạng đầu vào:

```
0 , 2 , 0 , 5 , 0 , 0 , 2
0 , 0 , 0 , 0 , 0 , 0 , 0
4 , 0 , 2 , 0 , 2 , 0 , 4
0 , 0 , 0 , 0 , 0 , 0 , 0
0 , 1 , 0 , 5 , 0 , 2 , 0
0 , 0 , 0 , 0 , 0 , 0 , 0
4 , 0 , 0 , 0 , 0 , 0 , 3
```

Trong định dạng này, **số không (zeros)** đại diện cho các ô trống, và **các số khác** thể hiện các hòn đảo.

#### 3.2 Đầu ra (Outputs)

Đầu ra cho ví dụ trên sẽ có định dạng như sau:

```
[ ”0” , ”2” , ”=” , ”5” , ”−” , ”−” , ”2” ]
[ ”0” , ”0” , ”0” , ”$” , ”0” , ”0” , ” | ” ]
[ ”4” , ”=” , ”2” , ”$” , ”2” , ”=” , ”4” ]
[ ”$” , ”0” , ”0” , ”$” , ”0” , ”0” , ” | ” ]
[ ”$” , ”1” , ”−” , ”5” , ”=” , ”2” , ” | ” ]
[ ”$” , ”0” , ”0” , ”0” , ”0” , ”0” , ” | ” ]
[ ”4” , ”=” , ”=” , ”=” , ”=” , ”=” , ”3” ]
```

Các ký hiệu trong đầu ra được định nghĩa như sau:

- **`|`** có nghĩa là **một cầu dọc** (one vertical bridge).
- **`$`** có nghĩa là **hai cầu dọc** (two vertical bridges).
- **`-`** có nghĩa là **một cầu ngang** (one horizontal bridge).
- **`=`** có nghĩa là **hai cầu ngang** (two horizontal bridges).

#### 3.3 Ngôn ngữ lập trình (Programming language)

Mã nguồn phải được viết bằng **Python (phiên bản 3.7 trở lên)**. Sinh viên được phép sử dụng bất kỳ thư viện hỗ trợ nào; tuy nhiên, các **thuật toán chính liên quan trực tiếp đến quá trình tìm kiếm** phải được sinh viên tự triển khai (implemented by you).

#### 3.4 Báo cáo (Report)

Báo cáo cần phải bao gồm các nội dung sau:

- Thông tin thành viên (ID sinh viên, họ tên đầy đủ, v.v.).
- Bảng phân công công việc, bao gồm thông tin về từng nhiệm vụ được giao cho các thành viên trong nhóm, cùng với **tỷ lệ hoàn thành** của mỗi thành viên so với nhiệm vụ được giao.
- **Tự đánh giá** về các yêu cầu của dự án.
- **Giải thích chi tiết** về từng thuật toán (quá trình triển khai, hàm heuristic, v.v.).
    - Khuyến khích sử dụng hình ảnh minh họa và sơ đồ.
    - **TUYỆT ĐỐI KHÔNG ĐẶT QUÁ NHIỀU MÃ NGUỒN VÀO BÁO CÁO** (Please DO NOT PUT TOO MUCH SOURCE CODE INTO THE REPORT).
- Mô tả các trường hợp kiểm thử (test cases) và **kết quả thử nghiệm** (mức sử dụng bộ nhớ, độ phức tạp thời gian, v.v.).
- **Làm nổi bật các thách thức** và **so sánh hành vi tổng thể** của các thuật toán đã thực hiện.
- Báo cáo cần được định dạng tốt (well-formatted) và **xuất sang định dạng PDF**. Điểm sẽ bị trừ nếu có hình ảnh bị cắt bởi ngắt trang, v.v..
- Tài liệu tham khảo (nếu có).

#### 3.5 Video minh họa (Demonstration videos)

- Các video minh họa (ghi lại quá trình chạy chương trình của sinh viên với một số trường hợp kiểm thử) nên được tải lên **YouTube hoặc Google Drive**, và **các URL công khai** phải được đưa vào báo cáo.
- Trong video, sinh viên nên bắt đầu từ việc biên dịch hoặc chạy mã của mình, sau đó **đi qua các bước chính** của quá trình thực thi chương trình để người xem dễ theo dõi.

#### 3.6 Nộp bài (Submission)

- Báo cáo, mã nguồn và các trường hợp kiểm thử phải được nộp dưới dạng một tệp nén (`.zip`, `.rar`, `.7z`) và được đặt tên theo định dạng: `StudentID1 StudentID2 . . .`.
- Nếu tệp nén lớn hơn **25MB**, ưu tiên nén báo cáo và mã nguồn. Các trường hợp kiểm thử có thể được tải lên **Google Drive** và chia sẻ qua một liên kết.
- Sinh viên cần tuân thủ tổ chức thư mục sau:

```
StudentID1 StudentID2
|-- Docs
|   |-- Report.pdf
|   |-- References 01.pdf
|   |-- References 02.pdf . . .
|-- Source
|   |-- Inputs
|   |   |-- input-01.txt
|   |   |-- input-02.txt . . .
|   |-- Outputs
|   |-- helper 01.py
|   |-- helper 02.py
|   |-- main.py
|   |-- requirements.txt (các thư viện cần cài đặt)
|   |-- README.txt (cách chạy mã nguồn) . . .
```

---

### 4. Đánh giá (Assessment)

Dự án sẽ được đánh giá dựa trên các tiêu chí sau:

|No|Tiêu chí|Điểm số|
|:--|:--|:--|
|1|**Mô tả Giải pháp:** Mô tả các nguyên tắc logic chính xác để tạo CNFs.|**30%**|
|2|**Tự động tạo CNFs.**|**10%**|
|3|**Sử dụng thư viện PySAT** để giải CNFs một cách chính xác.|**10%**|
|4|**Triển khai A*** để giải CNFs mà **không sử dụng thư viện.**|**10%**|
|5|**Triển khai các thuật toán bổ sung để so sánh:** 1) Thuật toán Brute-force để so sánh với A* (tốc độ); 2) Thuật toán Backtracking để so sánh với A* (tốc độ).|**10%**|
|6|**Tài liệu và Phân tích:** 1) Viết báo cáo chi tiết (chiếm 30% điểm của tiêu chí này); 2) Phân tích và thử nghiệm kỹ lưỡng; 3) Cung cấp **ít nhất 10 trường hợp kiểm thử** với **các kích thước khác nhau** (7 × 7, 9 × 9, 11 × 11, 13 × 13, 17 × 17, 20 × 20) để xác minh giải pháp; 4) So sánh kết quả và hiệu suất.|**30%**|

### 5. Thông báo (Notices)

Xin lưu ý những thông báo sau:

1. Đây là **BÀI TẬP NHÓM**. Mỗi nhóm có **4 thành viên**.
2. Thời gian thực hiện: **khoảng 3 tuần**.
3. Bất kỳ hành vi đạo văn (plagiarism), thủ thuật (tricks), hoặc gian dối nào sẽ bị **0 điểm** cho điểm khóa học.
4. Nội dung được tạo bởi AI (AI-Generated Content) phải **thấp hơn 30%** trong báo cáo.