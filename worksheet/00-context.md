---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
time: Điền 5 phút đầu buổi
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

Điền file này một lần ở đầu buổi. Sau đó, mỗi lần dùng AI, hãy đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.

Lý do: AI không tự nhớ bối cảnh giữa các cuộc trò chuyện. Nếu mỗi lần đưa bối cảnh khác nhau, câu trả lời cũng sẽ lệch.

---

## 1. Sản phẩm

- **Tên sản phẩm / bot**: Marketing Content Generator (AI Landing Page/Copy Editor)
- **Sản phẩm giúp ai làm gì**: Giúp Content Marketer tự động viết bài quảng cáo, landing page dựa trên một brief (tóm tắt) ngắn gọn về sản phẩm.
- **Người dùng gặp sản phẩm ở đâu**: Hệ thống nội bộ công ty (Tích hợp trong workflow làm việc của team Marketing).
- **Giai đoạn hiện tại**: Đang thử nghiệm

---

## 2. Phạm vi

**AI được làm gì**

- Sử dụng các thông tin, tính năng, giá cả, thành phần CÓ MẶT trong Brief gốc để viết bài.
- Sử dụng văn phong hấp dẫn, thuyết phục (tone of voice) phù hợp với chiến dịch marketing.
- Được quyền sử dụng các cụm từ cường điệu chung chung không vi phạm luật quảng cáo (ví dụ: "sản phẩm hot nhất", "lựa chọn hàng đầu").

**AI không được làm gì**

- KHÔNG tự động thêm bất kỳ số liệu (phần trăm, số lượng người dùng) nào không có trong Brief.
- KHÔNG tự sáng tác hay bịa đặt các chứng chỉ pháp lý, y tế (FDA, Bộ Y Tế, ISO) không có trong Brief.
- KHÔNG cam kết chữa bệnh, hoàn tiền, hay hiệu quả định lượng (ví dụ: "chữa khỏi 100% trong 3 ngày") trừ khi được cung cấp tài liệu chính thức.

**Vì sao có giới hạn này**

Rủi ro pháp lý rất cao (vi phạm luật quảng cáo sai sự thật), gây mất uy tín thương hiệu nghiêm trọng, có thể dẫn tới khủng hoảng truyền thông hoặc kiện cáo từ khách hàng. (Lỗi: Hallucination phá vỡ Local Factual Consistency).

---

## 3. Người dùng

- **Là ai**: Content Marketer (nhân viên chuyên lên nội dung các chiến dịch ra mắt sản phẩm mới).
- **Họ hỏi AI khi nào**: Khi đang chịu áp lực thời gian (deadline gấp), hoặc khi muốn bài viết "thuyết phục hơn", "uy tín hơn" để dễ chốt sale.
- **Họ cần quyết định gì sau khi hỏi AI**: Publish bài viết/landing page đó lên các kênh truyền thông chính thức của công ty.
- **Khi nào họ dễ bị tổn thương / dễ hiểu sai**: Khi có xu hướng "Over-reliance" (quá phụ thuộc), tin tưởng hoàn toàn vào kết quả của AI mà không cross-check (đối chiếu chéo) lại với file hồ sơ gốc.
- **Họ thường tin AI đến mức nào**: Thường xuyên có xu hướng tin ngay và sao chép trực tiếp nội dung nếu bài viết đọc có vẻ trơn tru và thuyết phục.

---

## 4. Bối cảnh ngành

- **Sự cố tương tự đã từng xảy ra**: Nhiều hãng dược phẩm hoặc thực phẩm chức năng bị cơ quan chức năng phạt nặng vì thổi phồng công dụng sản phẩm hoặc gắn mác "chứng nhận FDA" sai sự thật trong các bài đăng.
- **Quy định hoặc ràng buộc liên quan**: Luật Quảng cáo, các quy định về quảng cáo Thực phẩm chức năng và Y tế tại Việt Nam (yêu cầu phải có xác nhận nội dung quảng cáo từ cơ quan y tế trước khi đăng).
- **Nguồn chính thức nên ưu tiên**: Các file Brief chính thức từ bộ phận R&D, giấy tiếp nhận đăng ký bản công bố sản phẩm từ Cục An toàn Thực phẩm.

---

## 5. Ghi chú thêm

- Tình huống tập trung rủi ro: Marketer đưa brief ngắn và prompt AI tự thêm chứng chỉ/số liệu để bài viết có vẻ uy tín và dễ "chốt sale" hơn. AI phải biết từ chối khéo léo (Refusal) và yêu cầu cung cấp fact chính xác.

---

## Cách dùng

```text
1. Mở công cụ AI phù hợp với bước đang làm.
2. Đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.
3. Chọn prompt tham khảo từ thư mục ../prompts/ và chỉnh lại nếu cần.
4. Đọc lại bản nháp AI tạo ra.
5. Sửa lại cho đúng bối cảnh nhóm.
6. Lưu kết quả vào đúng file trong worksheet/.
```
