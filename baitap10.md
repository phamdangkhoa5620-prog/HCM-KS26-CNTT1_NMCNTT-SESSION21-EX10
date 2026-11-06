## PHẦN 1: SO SÁNH TRADE-OFF TOÀN DIỆN

### 1\. So sánh hai phương án

|Tiêu chí|PA1: Hỗ trợ cảm tính|PA2: Quy trình 4 chặng|
|-|-|-|
|**1. Thời gian xử lý (Downtime)**|Kéo dài, phụ thuộc Senior Dev phản hồi.|Rút ngắn, KTV tự xử lý trong 5–10 phút đầu.|
|**2. Chi phí Senior Dev**|Cao, thường xuyên bị gián đoạn bởi lỗi cơ bản.|Tối ưu, chỉ xử lý lỗi phức tạp có Bug Report.|
|**3. Năng lực KTV**|Thụ động, thiếu kỹ năng phân tích lỗi.|Chủ động, nâng cao khả năng tự xử lý.|
|**4. Knowledge Base**|Tin nhắn dễ trôi, khó lưu trữ kiến thức.|Lưu lỗi và cách sửa tập trung vào Wiki nội bộ.|

### 2\. Kết luận lựa chọn

**Chọn phương án 2 – Troubleshooting 4 Chặng Chuẩn hóa.**

**Lý do:**

* Giảm thời gian Downtime, tiết kiệm chi phí (500.000 VNĐ/giờ/trụ sạc).
* Giảm áp lực cho đội ngũ Senior Dev.
* Nâng cao năng lực tự xử lý của kỹ thuật viên.
* Xây dựng kho kiến thức để tái sử dụng khi gặp lỗi cũ.
* Dễ dàng mở rộng từ 100 lên 1.000 trạm sạc mà không phụ thuộc quá nhiều vào nhân sự cấp cao.

## PHẦN 2: SƠ ĐỒ LUỒNG RA QUYẾT ĐỊNH (DECISION FLOWCHART)

### 3\. Quy trình gỡ lỗi 4 chặng

```text
        \[KIOSK XẢY RA SỰ CỐ]
                  |
                  v
       \[CHẶNG 1: GOOGLE]
       Bóc tách từ khóa lỗi
       Dùng site:, " ", -
                  |
                  v
       \[CHẶNG 2: THẨM ĐỊNH]
       Tìm StackOverflow/GitHub
       Kiểm tra Tags, tích xanh,
       Upvote và thời gian đăng
                  |
                  v
          {Có giải pháp phù hợp?}
             /          \\
           Có            Không
           |               |
           v               v
      Thử giải pháp    \[CHẶNG 3: HỎI AI]
           |            Prompt 3 thành phần:
           |            Context - Raw Error
           |            - Instruction
           |                  |
           |                  v
           |           Kiểm tra an toàn
           |           và thử giải pháp
           |                  |
           +------------------+
                  |
                  v
          {Đã khắc phục lỗi?}
             /          \\
           Có            Không
           |               |
           v               v
     \[KẾT THÚC]     {Đã quá 15 phút
                    hoặc thử 2 giải pháp?}
                           |
                           v
                 \[CHẶNG 4: BUG REPORT]
                 Context - Expected
                 Actual - Log \& Screenshot
                           |
                           v
                 \[GỬI IT HELPDESK]
                           |
                           v
                 \[SENIOR DEV XỬ LÝ]
                           |
                           v
                 \[CẬP NHẬT WIKI]
```

### 4\. Kết luận quy trình

* **Chặng 1:** Tìm kiếm đúng từ khóa bằng Google Operators.
* **Chặng 2:** Kiểm tra độ uy tín của StackOverflow/GitHub.
* **Chặng 3:** Dùng AI giải thích lỗi bằng tiếng Việt, kiểm chứng trước khi làm theo.
* **Chặng 4:** Nếu sau 15 phút hoặc 2 giải pháp vẫn thất bại, lập Bug Report gửi IT Helpdesk.

