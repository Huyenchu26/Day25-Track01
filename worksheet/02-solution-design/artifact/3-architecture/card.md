---
artifact: 3 — Lớp kiến trúc dữ liệu
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp kiến trúc dữ liệu

**Tình huống xử lý**: T-01 (Bịa chứng chỉ y tế)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Xây dựng luồng RAG kết nối trực tiếp vào Legal & Compliance DB (hoặc hệ thống PIM) của doanh nghiệp. Hệ thống sẽ trích xuất mã sản phẩm (SKU) từ Brief, gọi API lấy danh sách chứng chỉ thật rồi nạp vào LLM trước khi sinh nội dung. Nếu DB không có chứng chỉ đó, AI không được phép viết.

---

## 2. Vì sao sửa ở lớp kiến trúc dữ liệu?

- Nguyên nhân chính là thiếu nguồn đúng (Ground Truth) khiến AI phải tự đoán thông tin y tế dựa trên dữ liệu mạng.
- AI đang phải tự nhớ thông tin thay vì đọc từ nguồn đáng tin cậy.
- Cần kiểm tra chéo (Cross-check) dữ liệu đầu vào trước khi LLM thực sự sinh nội dung.

**Hành động phòng vệ chính**:

- [x] Ngăn lỗi bằng nguồn dữ liệu đúng
- [x] Phát hiện khi nguồn thiếu hoặc lỗi
- [x] Khắc phục bằng cách chuyển sang người thật
- [x] Ghi lại lỗi để cải thiện sau

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo cần có:

- Sơ đồ cách dữ liệu đi qua hệ thống
- Nguồn dữ liệu chính thức
- Bước kiểm tra trước khi AI trả lời
- Cách xử lý khi nguồn thiếu, lỗi hoặc quá cũ
- Cách ghi lại hoặc theo dõi lỗi

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**

**Có thể gây vấn đề gì?**

Quá trình gọi API nội bộ làm tăng độ trễ (Latency) của hệ thống. Nếu Legal DB bảo trì, Content Pipeline sẽ bị đình trệ hoàn toàn. Việc cập nhật chứng chỉ mới phụ thuộc vào tốc độ nhập liệu của Phòng Pháp chế.

**Nhóm giảm vấn đề đó bằng cách nào?**

Sử dụng cơ chế Caching (Redis) để lưu tạm dữ liệu của các sản phẩm đang chạy chiến dịch Marketing hiện tại. Cung cấp Fallback Message khi DB lỗi ("Hệ thống kiểm chứng đang gián đoạn, vui lòng duyệt nội dung cẩn thận").

---

## 5. Checklist trước khi nộp

- [x] Sơ đồ cho thấy dữ liệu đi từ đâu đến đâu.
- [x] Có bước kiểm tra nguồn trước khi AI trả lời.
- [x] Có cách xử lý khi không có dữ liệu.
- [x] Có cách chuyển sang người thật với tình huống rủi ro cao.
- [x] Có cách biết lỗi này có đang lặp lại không.

**Người phụ trách**: Hứa Quang Linh
