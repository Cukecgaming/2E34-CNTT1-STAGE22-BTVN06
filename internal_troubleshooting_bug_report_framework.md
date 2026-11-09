# 🛠️ Internal Troubleshooting & Bug Report Framework

Quy trình chuẩn hóa giúp nhóm giải quyết sự cố môi trường (*Docker, Git, Port Conflict, PATH*) nhanh chóng, an toàn và tránh trôi thông tin.

---

## 1. 🐛 Bug Report Template (Mẫu báo cáo lỗi chuẩn)

> **Bắt buộc:** Thành viên phải điền đủ **4 thành phần** dưới đây trước khi gửi yêu cầu hỗ trợ vào nhóm chat hoặc cho Mentor/Giảng viên.

### Structure Template

| Thành phần | Ý nghĩa | Nội dung cần điền | Ví dụ minh họa |
| :--- | :--- | :--- | :--- |
| **1. CONTEXT** | Ngữ cảnh môi trường | Hệ điều hành, Công cụ/Công nghệ, Nhánh Git | `HĐH: Windows 11` \| `Công cụ: VS Code, Git Bash` \| `Nhánh: main` |
| **2. EXPECTED** | Kết quả kỳ vọng | Hành vi mong muốn của ứng dụng/lệnh | Đẩy (push) mã nguồn thành công lên kho chứa GitHub. |
| **3. ACTUAL** | Kết quả thực tế | Sự cố xảy ra thực tế khi thực thi | Terminal bị chặn và từ chối quyền truy cập vào file cấu hình Git. |
| **4. LOG / ERROR** | Mã lỗi thô & Đã thử | Mã lỗi chính xác và các bước *Self-Troubleshooting* | `error: open(".git/FETCH_HEAD"): Permission denied`<br>*Đã thử: Run as Administrator nhưng chưa được.* |

---

## 2. 🔄 Quy trình 3 bước tự tra cứu (Self-Troubleshooting Workflow)

Thực hiện nghiêm túc **3 bước** theo thứ tự để tự xử lý **80% vấn đề** trước khi nhờ hỗ trợ:

```text
[Bước 1: Smart Googling] ➔ [Bước 2: Community Search] ➔ [Bước 3: AI Translation & Fact-Checking]
```

### 📋 Chi tiết quy trình tra cứu

| Bước | Tên bước | Thao tác kỹ thuật | Ví dụ cú pháp chuẩn |
| :---: | :--- | :--- | :--- |
| **1** | **Smart Googling** | Đặt mã lỗi thô trong dấu ngoặc kép `""` kèm theo tên HĐH để lọc nhiễu. | `"open(.git/FETCH_HEAD): Permission denied" Windows 11` |
| **2** | **Community Search** | Giới hạn tra cứu trên nguồn uy tín (*GitHub Issues*, *StackOverflow*) bằng toán tử `site:`. | `site:github.com "Permission denied" "FETCH_HEAD"`<br>`site:stackoverflow.com "Permission denied" Windows 11` |
| **3** | **AI & Fact-Checking** | Dùng Prompt 3 thành phần nhờ AI dịch lỗi và đưa ra hướng xử lý an toàn. | *(Xem mẫu Prompt tại Mục 3)* |

---

## 3. 🤖 Quy chuẩn sử dụng AI (Prompt 3 Thành phần)

Để AI giải thích nguyên nhân gốc rễ (Root Cause) bằng ngôn ngữ bình dân và gợi ý lệnh an toàn, áp dụng công thức **Role - Context - Task**:

```markdown
### 💡 MẪU PROMPT CHUẨN KHI HỎI AI

- [Role]: Bạn là một trợ lý AI kỹ thuật thông minh, giỏi giải thích các khái niệm IT phức tạp bằng ngôn ngữ bình dân, dễ hiểu.
- [Context]: Tôi đang dùng Windows 11 và VS Code. Khi thực hiện lệnh đẩy code lên GitHub thì Terminal báo lỗi: `error: open(".git/FETCH_HEAD"): Permission denied`. Tôi đã thử gõ lại lệnh nhiều lần nhưng không được.
- [Task]: 
  1. Giải thích nguyên nhân gây lỗi này một cách bình dân nhất.
  2. Đưa ra 2 cách khắc phục an toàn (kèm cảnh báo nếu có lệnh nguy hiểm ảnh hưởng hệ thống).
```

---

## 4. ✅ Tiêu chí đánh giá giải pháp từ Cộng đồng (Fact-Checking)

Khi tìm kiếm trên GitHub Issues hoặc StackOverflow, **không áp dụng mù quáng**. Hãy đối chiếu qua bảng tiêu chuẩn sau:

| Tiêu chí | Giải pháp ĐÁNG TIN CẬY (Nên dùng) | Giải pháp RỦI RO (Nên tránh) |
| :--- | :--- | :--- |
| **Độ tin cậy lịch sử** | Có chỉ số **Reactions (👍 / ❤️)** cao hoặc được đánh dấu **Accepted Answer (✓)**. | Không có lượt upvote, câu trả lời mơ hồ không ai xác nhận. |
| **Tính cập nhật (Recency)** | Đăng hoặc cập nhật trong **1–2 năm gần đây** (hoặc xác nhận tương thích bản mới). | Bài viết cũ từ 2014-2018 (dùng cú pháp/cơ chế cũ đã bị loại bỏ trên Windows 11). |
| **Môi trường & Cú pháp** | Đúng HĐH Windows (`PowerShell`, `setx`, `icacls`, đường dẫn `C:\...`). | Dùng cú pháp Linux/macOS (`sudo`, `chmod`, `chown`, `export PATH`) trên PowerShell. |

---

## 5. 📸 Mẹo chụp ảnh màn hình minh họa lỗi chuyên nghiệp

1. **Khoanh vùng trọng tâm:** Dùng khung màu đỏ/cam khoanh đúng vị trí báo lỗi trong Terminal hoặc hộp thoại hệ thống.
2. **Bảo mật thông tin (Privacy Masking):** Dùng công cụ Blur/Che đường dẫn thư mục chứa thông tin cá nhân (`C:\Users\Ten_Cua_Ban\...`), Token hoặc Key bảo mật.
3. **Cắt hình gọn gàng:** Sử dụng phím tắt `Windows + Shift + S` chỉ chụp đúng cửa sổ làm việc liên quan, không chụp toàn bộ màn hình Desktop.