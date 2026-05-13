---
artifact: 3 — Lớp kiến trúc dữ liệu
bai-tap: 2 — Thiết kế giải pháp
card: ./card.md
---

# demo.md — Sơ đồ Kiến trúc Dữ liệu (RAG/API Layer)

Sơ đồ Mermaid dưới đây mô tả luồng dữ liệu của hệ thống, minh họa cách Lớp Kiến trúc chặn đứng nguy cơ AI bịa chứng chỉ (T-01) bằng cách cung cấp "Ground Truth" trước khi gọi LLM.

## Sơ đồ luồng xử lý (Data Flow)

```mermaid
sequenceDiagram
    autonumber
    actor Marketer
    participant UI as Giao diện (Content Editor)
    participant Backend as Hệ thống Backend
    participant DB as Legal & Compliance DB (PIM)
    participant LLM as LLM (AI Generator)
    
    Marketer->>UI: Nhập Prompt (VD: Viết bài FB Serum C, thêm chứng nhận FDA)
    UI->>Backend: Gửi Request (Product SKU: SERUM-C, Prompt)
    
    rect rgb(230, 240, 255)
        Note right of Backend: BƯỚC 1: CROSS-CHECK DỮ LIỆU
        Backend->>DB: Truy vấn thông tin pháp lý bằng SKU
        alt DB Phản hồi (Có dữ liệu)
            DB-->>Backend: Trả về <APPROVED_FACTS> (Thành phần, Chứng chỉ thật)
        else DB Lỗi / Đang bảo trì (Fallback)
            DB-->>Backend: Lỗi Timeout
            Backend-->>UI: Fallback Message: "Hệ thống kiểm chứng gián đoạn."
        end
    end
    
    rect rgb(255, 240, 230)
        Note right of Backend: BƯỚC 2: TẠO PROMPT & GỌI LLM
        Backend->>LLM: Gửi System Prompt + <APPROVED_FACTS> + User Prompt
        LLM-->>Backend: Trả về nội dung (Hoặc lời từ chối nếu User ép bịa)
    end
    
    rect rgb(230, 255, 230)
        Note right of Backend: BƯỚC 3: XỬ LÝ KẾT QUẢ
        alt AI Sinh nội dung thành công
            Backend->>Backend: Đánh dấu (Highlight xanh) các chứng chỉ khớp với DB
            Backend-->>UI: Hiển thị nội dung kèm nhãn "Verified"
        else AI Từ chối do vi phạm Guardrails
            Backend->>Backend: Ghi log lỗi vào hệ thống giám sát (Monitoring)
            Backend-->>UI: Hiển thị Alert Box đỏ & Nút "Gửi Legal duyệt"
        end
    end
```

### Giải thích các cơ chế phòng vệ trong Kiến trúc:
1. **Ngăn chặn từ đầu (Prevention)**: LLM không bao giờ phải "đoán" chứng chỉ vì nó được nạp sẵn `<APPROVED_FACTS>` ở Bước 2.
2. **Kiểm tra chéo (Detection)**: Backend kiểm tra lại nội dung LLM sinh ra ở Bước 3. Bất kỳ chứng chỉ nào không nằm trong tập hợp do DB trả về sẽ bị đánh dấu Vàng (Unverified) hoặc AI tự động chặn.
3. **Giám sát (Logging)**: Các trường hợp AI phải từ chối do Marketer ép buộc sẽ được ghi Log lại để phân tích hành vi "lách luật" của người dùng nội bộ, từ đó có kế hoạch training cho nhân viên Marketing.
