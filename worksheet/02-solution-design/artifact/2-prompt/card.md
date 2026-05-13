---
artifact: 2 — Lớp chỉ dẫn AI
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp chỉ dẫn AI

**Tình huống xử lý**: T-01 (Bịa chứng chỉ y tế)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Nhóm sẽ thiết kế một System Prompt cứng rắn (Guardrails). AI được chỉ thị rõ chỉ được dùng các chứng nhận y tế có sẵn trong khối `<APPROVED_FACTS>` (được truyền vào từ hệ thống). Nếu Marketer ép thêm chứng chỉ bên ngoài, AI phải kiên quyết từ chối bằng một kịch bản từ chối mẫu.

---

## 2. Vì sao sửa ở lớp chỉ dẫn AI?

- AI đang chiều theo giả định sai của người dùng (Sycophancy) khi bị Marketer gây áp lực KPI hoặc lấy cớ "tôi chịu mọi trách nhiệm".
- AI cần luật rõ: Tuyệt đối không được hallucinate các thực thể thuộc nhóm "Medical Claims" & "Certificates".

**Hành động phòng vệ chính**:

- [x] Ngăn câu trả lời sai ngay từ đầu
- [ ] Bắt buộc nêu nguồn khi nói về thông tin quan trọng
- [x] Từ chối trả lời khi thiếu căn cứ
- [ ] Chuyển người thật khi vượt phạm vi

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo cần có:

- Luật chính cho AI
- Mẫu câu khi thiếu nguồn
- Mẫu câu khi cần chuyển sang người thật
- 2-3 ví dụ hỏi đáp để kiểm tra luật
- Kết quả thử lại với vài tình huống từ Bài 1

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

**Có thể gây vấn đề gì?**

AI có thể trở nên quá cứng nhắc (False Positive) và từ chối luôn cả những prompt vô hại, khiến trải nghiệm sử dụng chatbot Content bị giảm đi.

**Nhóm giảm vấn đề đó bằng cách nào?**

Chỉ áp dụng Guardrail nghiêm ngặt cho 2 loại thực thể: "Chứng chỉ" và "Cam kết chữa bệnh". Với các yêu cầu khác như đổi văn phong (Vui nhộn, Trang trọng), đổi đối tượng mục tiêu, AI vẫn được quyền sáng tạo tự do 100%.

---

## 5. Checklist trước khi nộp

- [x] Luật viết đủ cụ thể để AI làm theo.
- [x] Có mẫu câu khi AI không có đủ thông tin.
- [x] Có ví dụ cho tình huống dễ sai.
- [x] Có thử lại bằng tình huống trong Bài 1.
- [x] Không dùng prompt như cách duy nhất nếu lỗi nằm ở dữ liệu hoặc quy trình.

**Người phụ trách**: Nguyễn Thị Tuyết
