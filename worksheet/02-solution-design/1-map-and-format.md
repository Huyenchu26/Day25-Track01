---
artifact: 1 — FINAL kế hoạch giải pháp
bai-tap: 2 — Thiết kế giải pháp
phase: Chọn rủi ro + chọn tầng + chọn demo + chốt 3 lớp giải pháp
time: 11:00-11:55
input: 00-context.md + 01-test-set-review/3-FINAL-test-set-eval-plan.md
nop-cuoi: Có — file cuối Bài 2
---

# 1 — FINAL: Kế hoạch giải pháp

File này ghi lại quyết định chính của Bài 2:

- Rủi ro nào được chọn.
- Vì sao rủi ro đó quan trọng.
- Nguyên nhân gốc là gì.
- Nhóm sẽ xây 3 lớp giải pháp nào.
- Mỗi lớp dùng demo gì.

Lý do cần 3 lớp: một giải pháp đơn lẻ dễ lọt lỗi. Với rủi ro nặng, nhóm cần nhiều lớp cùng đỡ: lớp này ngăn, lớp kia phát hiện, lớp khác khắc phục hoặc thông báo cho người dùng.

Ba lớp giải pháp nằm trong thư mục `artifact/`:

| Lớp | Thư mục | Vai trò |
|---|---|---|
| Giao diện | `artifact/1-uiux/` | Cảnh báo, dẫn nguồn, nút chuyển sang người thật |
| Chỉ dẫn AI | `artifact/2-prompt/` | Hỏi lại, từ chối, bắt buộc dẫn nguồn |
| Kiến trúc dữ liệu | `artifact/3-architecture/` | Tra cứu nguồn đúng, lưu tạm dữ liệu, xử lý khi thiếu nguồn, giám sát |

Ba lớp này bổ sung cho nhau. Nếu một lớp lọt lỗi, lớp khác vẫn có thể chặn hoặc giảm hại.

## Thông tin nhóm

- **Chủ đề**: Marketing Content Generator
- **Thành viên**: Huyền, Tuyết, Linh
- **Ngày**: 2026-05-13

---

## Phần A — Chọn rủi ro và tầng giải pháp

### Rủi ro chính được chọn

- **ID tình huống**: T-01
- **Mô tả ngắn**: Khi bị áp lực KPI hoặc thiếu nội dung, AI có xu hướng bịa thông tin chứng chỉ y tế ảo (như FDA, Bộ Y Tế), gây rủi ro vi phạm Luật Dược và Luật Quảng cáo cho doanh nghiệp.
- **Mức độ**: Nặng
- **Điểm rủi ro**: 25
- **Vì sao chọn tình huống này**: Bịa chứng chỉ y tế là lỗi nghiêm trọng nhất, dẫn đến phạt tiền và tước giấy phép. Rủi ro này cực kỳ dễ xảy ra khi Marketer ép AI tạo nội dung "nghe uy tín hơn" để chốt sale.

### Tìm nguyên nhân gốc

Đừng chỉ mô tả lỗi. Hãy trả lời: vì sao lỗi xảy ra?

- [x] Thiếu nguồn dữ liệu đúng. (AI không có DB các chứng chỉ thật của sản phẩm).
- [ ] AI đoán khi không biết.
- [x] Giao diện khiến người dùng tin quá mức. (Marketer lầm tưởng nội dung AI sinh ra đã được verify).
- [x] Quy trình thiếu người duyệt hoặc thiếu bước chuyển sang người thật.
- [ ] Không có theo dõi sau khi ra mắt.
- [x] Khác: AI bị Sycophancy (có xu hướng chiều lòng Marketer) khi Marketer cố ép.

### Bảng nối nguyên nhân với tầng sửa

| Nguyên nhân gốc | Tầng ưu tiên sửa | Lớp giải pháp liên quan |
|---|---|---|
| Thiếu nguồn đúng | Dữ liệu / tra cứu nguồn (RAG) / chính sách nguồn | `3-architecture` là chính |
| AI đoán bừa | Chỉ dẫn hệ thống / quy tắc từ chối / dẫn nguồn | `2-prompt` là chính |
| Người dùng tin quá mức | Giao diện cảnh báo / cách viết mức tin cậy | `1-uiux` là chính |
| Tình huống nhạy cảm | Người duyệt / chuyển sang người thật | `1-uiux` + `2-prompt` + `3-architecture` |
| Lỗi lặp lại sau khi ra mắt | Theo dõi / vòng phản hồi | `3-architecture` là chính |

Nguyên tắc: lỗi ở tầng nào, ưu tiên sửa ở tầng đó. Đừng chỉ thêm cảnh báo giao diện nếu nguyên nhân gốc là thiếu nguồn dữ liệu hoặc AI đoán khi không biết.

### 10 tầng giải pháp tham khảo

Không bắt buộc dùng đủ 10 tầng. Bảng này giúp nhóm chọn đúng hướng sửa.

| Tầng | Khi nào dùng |
|---|---|
| Giao diện | Người dùng tin AI quá mức, thiếu cảnh báo, thiếu nguồn, thiếu nút chuyển sang người thật |
| Chỉ dẫn AI | AI đoán khi không biết, không hỏi lại, không từ chối |
| Quy trình xử lý | Cần phân loại ý định, chuyển đúng nơi xử lý, có cách xử lý khi AI không nên trả lời |
| Dữ liệu / tra cứu nguồn (RAG) | Thiếu nguồn đúng, nguồn cũ, AI không dựa vào nguồn đáng tin cậy |
| Theo dõi | Lỗi lặp lại sau khi ra mắt nhưng không ai thấy |
| Chính sách / thông báo giới hạn | Người dùng không biết giới hạn của AI |
| Người duyệt / phê duyệt | Tình huống pháp lý, y tế, tài chính, tuyển dụng, hoặc tác động lớn |
| Vai trò trách nhiệm | Có cảnh báo nhưng không ai chịu trách nhiệm xử lý |
| Vòng phản hồi | Cần người dùng / người rà báo lỗi để cập nhật hệ thống |
| Kiến trúc lai | LLM một mình không đủ, cần rule, classifier, hoặc nhiều bước kiểm tra |

### 4 hành động phòng vệ

Mỗi lớp nên làm ít nhất một việc:

- **Ngăn**: giảm khả năng lỗi xảy ra từ đầu.
- **Phát hiện**: nhận ra lỗi hoặc tín hiệu nguy hiểm.
- **Khắc phục**: chuyển sang người thật, dùng câu trả lời dự phòng, hoặc dừng trả lời.
- **Thông báo**: giúp người dùng hiểu mức tin cậy và rủi ro.

Gợi ý theo mức rủi ro:

| Mức rủi ro | Nên có |
|---|---|
| Nhẹ | Ít nhất 1 hành động |
| Vừa | Ít nhất 2 hành động |
| Nặng | Ít nhất 3 hành động |
| Rất nặng / không đảo ngược được | Cố gắng đủ 4 hành động + có người chịu trách nhiệm |

### Kết luận Phần A

**Nguyên nhân gốc**: (1) AI không có cơ sở dữ liệu thật (Ground Truth) về chứng chỉ của sản phẩm; (2) AI cố gắng chiều lòng người dùng; (3) Giao diện không cảnh báo thông tin chưa được kiểm chứng.

**Tầng chính cần sửa**: Dữ liệu / tra cứu nguồn (RAG) để chặn từ gốc.

**Vì sao cần 3 lớp giải pháp**:

- Lớp giao diện: Giúp minh bạch nguồn gốc thông tin (Fact-check) và cung cấp cơ chế xin duyệt (Escalation) khi AI từ chối.
- Lớp chỉ dẫn AI: Rào cản (Guardrails) ở mức ngôn ngữ, cấm AI tự sáng tác và cung cấp kịch bản từ chối khéo léo.
- Lớp kiến trúc dữ liệu: Ngăn chặn triệt để AI lấy thông tin sai bằng cách chỉ cung cấp ngữ cảnh từ hệ thống PIM/Compliance nội bộ.

---

## Phần B — Chọn định dạng demo

Mỗi lớp cần một bản demo. Demo giúp biến ý tưởng thành thứ trực quan để nhóm khác xem, kiểm tra và phản biện.

| Lớp | Thư mục | Định dạng demo chọn | Thời gian dự kiến |
|---|---|---|---|
| Giao diện | `1-uiux` | HTML / ASCII UI | 20 phút |
| Chỉ dẫn AI | `2-prompt` | bản prompt trong Markdown + ví dụ | 15 phút |
| Kiến trúc dữ liệu | `3-architecture` | Sơ đồ Mermaid (hộp-mũi tên) | 20 phút |

**Lý do chọn demo**

- Giao diện: Cần chứng minh người dùng sẽ nhìn thấy cảnh báo và nhãn kiểm chứng như thế nào trên màn hình.
- Chỉ dẫn AI: Cần cho thấy cấu trúc prompt, đặc biệt là cách nhúng <APPROVED_FACTS> và quy tắc từ chối.
- Kiến trúc dữ liệu: Cần làm rõ luồng đi của dữ liệu từ khi nhập SKU đến khi gọi API Legal DB và nạp vào RAG.

Gợi ý: có thể dùng AI để dựng nhanh bản nháp demo, nhưng nhóm phải đọc lại và sửa.

### Chọn demo theo điều cần chứng minh

| Nếu cần chứng minh... | Demo phù hợp |
|---|---|
| Người dùng nhìn thấy gì | Sketch, Figma, HTML, ASCII UI |
| AI được chỉ dẫn thế nào | Bản prompt trong Markdown, ví dụ trả lời |
| Dữ liệu đi qua đâu | Sơ đồ hộp-mũi tên, ASCII, Mermaid |
| Quy trình chuyển sang người thật | Sơ đồ quy trình |

---

## Phần C — Ba lớp giải pháp

Ghi tóm tắt ở đây. Chi tiết nằm trong `card.md` và `demo.*` của từng thư mục.

### Lớp 1 — Giao diện (`artifact/1-uiux/`)

- **Cách tiếp cận**: UI Fact-check, highlight các claim y tế/chứng chỉ (xanh/vàng) và hiển thị Alert Box yêu cầu phê duyệt từ Pháp chế khi AI từ chối.
- **Hành động phòng vệ bao phủ**: Thông báo / Phát hiện / Khắc phục
- **Demo**: Giao diện dạng Wireframe ASCII.
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/1-uiux/card.md`
- `artifact/1-uiux/demo.md`

### Lớp 2 — Chỉ dẫn AI (`artifact/2-prompt/`)

- **Cách tiếp cận**: System Prompt Guardrails, yêu cầu tuyệt đối chỉ dùng chứng chỉ trong <APPROVED_FACTS> và hướng dẫn cách từ chối khéo léo.
- **Hành động phòng vệ bao phủ**: Ngăn / Từ chối
- **Demo**: Markdown bản prompt + 2 ví dụ (Pass/Refusal).
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/2-prompt/card.md`
- `artifact/2-prompt/demo.md`

### Lớp 3 — Kiến trúc dữ liệu (`artifact/3-architecture/`)

- **Cách tiếp cận**: Cơ chế RAG gọi API đến Legal & Compliance DB dựa trên Product SKU để lấy danh sách chứng nhận hợp lệ.
- **Hành động phòng vệ bao phủ**: Ngăn / Phát hiện
- **Demo**: Sơ đồ luồng xử lý Mermaid.
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/3-architecture/card.md`
- `artifact/3-architecture/demo.md`

---

## Tổng kiểm tra

| Câu hỏi | Trả lời |
|---|---|
| Rủi ro chính đã chọn là gì? | T-01 (Bịa chứng chỉ y tế) |
| Nguyên nhân gốc là gì? | Thiếu DB thật, AI có xu hướng chiều lòng, UI thiếu minh bạch. |
| 3 lớp giải pháp đã đủ chưa? | Giao diện: Đủ / Chỉ dẫn AI: Đủ / Kiến trúc: Đủ |
| 4 hành động đã bao phủ chưa? | Ngăn: Có / Phát hiện: Có / Khắc phục: Có / Thông báo: Có |
| Nhóm khác đã góp ý chưa? | Chưa |
| Nhóm đã sửa gì sau phản biện? | N/A |

## Phản biện chéo: 4 câu phải trả lời

Khi nhóm khác góp ý, hoặc khi nhóm tự rà lại, dùng 4 câu này:

| Góc phản biện | Câu hỏi |
|---|---|
| Đúng tầng | Giải pháp có sửa đúng nguyên nhân gốc không? |
| Cụ thể | Demo có đủ rõ để hiểu cách vận hành không? |
| Đủ lớp | 3 lớp có bổ sung cho nhau không, hay đang lặp cùng một ý? |
| Tác dụng phụ | Giải pháp có làm chậm, tốn kém, rối giao diện, hoặc gây hiểu nhầm mới không? |

Ghi góp ý cụ thể vào `card.md` hoặc phần tổng kiểm tra. Không ghi chung chung "ổn" hoặc "chưa ổn".

## Gợi ý chia việc

Nhóm 3 người:

- Thành viên A: `artifact/1-uiux/`
- Thành viên B: `artifact/2-prompt/`
- Thành viên C: `artifact/3-architecture/`

Nhóm 2 người:

- Một người phụ trách 2 lớp.
- Người còn lại phụ trách 1 lớp và rà lại 2 lớp kia.

5 phút cuối: cả nhóm đọc chéo 3 lớp, sửa lại bảng tổng kiểm tra, rồi chuẩn bị phản biện chéo.
