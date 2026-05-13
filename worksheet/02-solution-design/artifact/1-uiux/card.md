---
artifact: 1 — Lớp giao diện
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp giao diện

**Tình huống xử lý**: T-01 (Bịa chứng chỉ y tế)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Giao diện soạn thảo sẽ làm nổi bật (highlight) các chứng chỉ y tế hoặc công dụng bằng các nhãn màu (Xanh: Đã kiểm chứng từ PIM DB; Vàng: Chưa xác minh). 
Khi AI từ chối sinh nội dung bịa đặt do Marketer ép buộc, giao diện sẽ hiển thị một Alert Box cảnh báo rủi ro pháp lý kèm nút "Gửi yêu cầu phê duyệt lên Phòng Pháp chế" (Escalation).

---

## 2. Vì sao sửa ở lớp giao diện?

- Người dùng dễ tin câu trả lời của AI quá mức (Marketer thấy AI viết mượt nên tin là có thật).
- Rủi ro xảy ra ở khoảnh khắc người dùng copy/paste bài viết đi publish.
- Giao diện cần làm rõ: chứng chỉ nào là thật (có trong DB), chứng chỉ nào là ảo.

**Hành động phòng vệ chính**:

- [x] Thông báo rõ giới hạn
- [x] Phát hiện dấu hiệu thiếu nguồn
- [x] Chuyển người thật khi cần
- [x] Giúp người dùng kiểm tra lại nguồn

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

**Định dạng demo**:

- [x] Phác thảo màn hình (ASCII UI)
- [ ] Luồng màn hình
- [ ] Bản HTML đơn giản
- [ ] Ảnh hoặc link prototype

**Thành phần cần có trong demo**:

- Trạng thái có nguồn xác minh
- Trạng thái chưa có nguồn xác minh
- Cách người dùng chuyển sang người thật
- Câu chữ cảnh báo ngắn, dễ hiểu

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

Làm giao diện soạn thảo (Editor) bị rối mắt bởi quá nhiều nhãn màu (badges). Marketer có thể cảm thấy phiền phức khi bị AI từ chối và cản trở luồng công việc (giảm tốc độ tạo content).

**Nhóm giảm vấn đề đó bằng cách nào?**

Chỉ highlight các thực thể nhạy cảm (Medical Claims, Certificates, Percentages). Thông báo từ chối được thiết kế ngắn gọn, không lên mặt dạy đời, và luôn cung cấp nút "Gửi Legal duyệt" để Marketer thấy họ vẫn có đường lui chứ không bị chặn đứng hoàn toàn.

---

## 5. Checklist trước khi nộp

- [x] Giải pháp gắn đúng với một rủi ro chính.
- [x] Demo nhìn vào là hiểu vấn đề được chặn ở đâu.
- [x] Có đủ trạng thái bình thường và trạng thái lỗi.
- [x] Có cách chuyển sang người thật khi AI không nên tự xử lý.
- [x] Câu chữ trong giao diện ngắn, không đổ hết trách nhiệm cho người dùng.

**Người phụ trách**: Chu Thị Ngọc Huyền
