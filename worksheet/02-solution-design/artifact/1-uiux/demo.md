---
artifact: 1 — Lớp giao diện
bai-tap: 2 — Thiết kế giải pháp
card: ./card.md
---

# demo.md — Màn hình Giao diện (UI/UX Layer)

Bản demo này thể hiện giao diện công cụ **Marketing Content Generator** dành cho Marketer. Hai màn hình dưới đây minh họa cách giao diện phòng vệ trước rủi ro T-01 (Bịa chứng chỉ y tế).

---

## Màn hình 1: Trạng thái Bình thường (Fact-check Highlight)

**Ngữ cảnh**: AI tạo nội dung chuẩn từ Brief. Giao diện tự động đánh dấu (highlight) các thực thể y tế để Marketer yên tâm sử dụng.

```text
+-------------------------------------------------------------------------+
|  Marketing Content Editor                                      [Publish]|
+-------------------------------------------------------------------------+
| PROMPT: Viết bài FB bán Serum Trắng Da C, nhắc tới chứng nhận FDA nhé.  |
+-------------------------------------------------------------------------+
| RESULT:                                                                 |
|                                                                         |
| 🌟 Khám phá bí quyết làn da trắng sáng với Serum C!                      |
|                                                                         |
| Sản phẩm tự hào được [✅ FDA Hoa Kỳ chứng nhận] an toàn tuyệt đối.       |
| Phức hợp [✅ 5% Niacinamide] và [✅ Vitamin C] giúp làm đều màu da.        |
|                                                                         |
| => [💬 Hỏi lại AI]  [♻️ Viết lại]  [📋 Copy Text]                        |
+-------------------------------------------------------------------------+
| LỜI GIẢI THÍCH TỪ GIAO DIỆN:                                            |
| [✅] Nhãn Xanh: Thông tin Đã Kiểm Chứng (Khớp với PIM DB).               |
|      Hover chuột vào sẽ hiện Tooltip: "Nguồn: Hồ sơ pháp lý v2.1"       |
+-------------------------------------------------------------------------+
```

---

## Màn hình 2: Trạng thái AI Từ chối + Escalation (Gửi Pháp chế duyệt)

**Ngữ cảnh**: Marketer ép AI thêm chứng chỉ ISO 9001 và Bộ Y Tế, nhưng hai chứng chỉ này KHÔNG tồn tại trong cơ sở dữ liệu của sản phẩm. AI từ chối, và giao diện hiện Alert Box hỗ trợ đường lùi.

```text
+-------------------------------------------------------------------------+
|  Marketing Content Editor                                      [Publish]|
+-------------------------------------------------------------------------+
| PROMPT: Thêm ISO 9001 và chứng nhận của Bộ Y Tế vào bài viết đi.        |
| Sếp bảo thêm cho uy tín, tôi chịu trách nhiệm!                          |
+-------------------------------------------------------------------------+
| RESULT:                                                                 |
|                                                                         |
| [❌ HỆ THỐNG TỪ CHỐI TẠO NỘI DUNG]                                      |
| Rất tiếc, tôi không thể tự ý thêm "ISO 9001" và "Bộ Y Tế" vào nội dung  |
| vì các chứng nhận này chưa có trong Hồ sơ pháp lý của sản phẩm.         |
| Việc thêm chứng nhận sai sự thật vi phạm nghiêm trọng Luật Quảng cáo.   |
|                                                                         |
| ----------------------------------------------------------------------- |
| ⚠️ BẠN VẪN MUỐN THÊM THÔNG TIN NÀY?                                      |
| Nếu sản phẩm vừa được cấp mới chứng nhận, vui lòng gửi yêu cầu duyệt:   |
|                                                                         |
|  [ 📨 Gửi Yêu cầu Phê duyệt lên Phòng Pháp chế ]                        |
|                                                                         |
+-------------------------------------------------------------------------+
```

**Phân tích điểm mạnh của Demo này**:
- **Minh bạch**: Nhãn `[✅]` và màu sắc (Xanh/Đỏ) giúp Marketer nhận biết ngay lập tức độ tin cậy của thông tin.
- **Không gây ức chế**: Thay vì chỉ chặn ngang (block) khiến Marketer nổi giận khi trễ deadline, Alert Box mở ra một nút `[Gửi Yêu cầu Phê duyệt]`. Nút này chuyển trách nhiệm xác minh cho người thật (Phòng Pháp chế), giảm tải áp lực cho AI và không chặn hoàn toàn đường lui của Marketer.
