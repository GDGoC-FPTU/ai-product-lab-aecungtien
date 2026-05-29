# Nhóm AEcungtien
Nguyễn Huy Bảo - 2A202600997
Tạ Duy Xuân - 2A202600970
Phạm Ngọc Vinh - 2A202600563
# 🗳️ Quyết định lựa chọn của nhóm:
Nhóm quyết định chọn bài toán **"Card #8 — Kỹ thuật viên VinFast mất nhiều thời gian tra cứu manual và chẩn đoán lỗi bảo hành cho khách hàng.   "** để thực hiện Deep-Dive.
---
## 3.1. Current-State Workflow
Quy trình xử lý sự cố hết pin thực địa hiện tại của điều phối viên Xanh SM:

```text
┌────────────────┐     ┌────────────────┐     ┌────────────────┐     ┌────────────────┐
│ Bước 1         │     │ Bước 2         │     │ Bước 3         │     │ Bước 4         │
│ Nhận mô tả lỗi │     │ Trích xuất mã  │     │ Tra cứu manual │     │ Tham vấn Senior│
│ từ khách hàng  │ ──→ │ lỗi xe (DTC)   │ ──→ │ PDF và SOP     │ ──→ │ & chốt lệnh sửa│
│ Ai: KTV & CVDV │     │ Ai: KTV        │     │ Ai: KTV        │     │ Ai: KTV & S.Eng│
│ ⏱ 5 phút      │     │ ⏱ 10 phút     │     │ ⏱ 35 phút 🔴   │     │ ⏱ 15 phút 🔴   │
│ In: Lời khách  │     │ In: Cổng OBD   │     │ In: Mã lỗi DTC │     │ In: Phương án  │
│ Out: Tình trạng│     │ Out: Log DTC   │     │ Out: Cách xử lý│     │ Out: Lệnh sửa  │
└────────────────┘     └────────────────┘     └────────────────┘     └────────────────┘

🔴 = Bottlenecks (Nút thắt cổ chai gây chậm trễ)
⏱ Tổng thời gian xử lý thủ công: ~65 phút/ca chẩn đoán.
```

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Kỹ thuật viên Xưởng dịch vụ (Service Center Technician) và Cố vấn dịch vụ (Service Advisor) tại VinFast. |
| **2. Current Workflow** | Khi tiếp nhận xe bảo hành, kỹ thuật viên nghe mô tả từ khách hàng, cắm máy đọc mã lỗi (DTC), sau đó mở kho tài liệu nội bộ tra cứu thủ công qua hàng ngàn trang Manual PDF. Nếu không xác định được nguyên nhân (root-cause), kỹ thuật viên phải leo thang (escalate) hỏi ý kiến kỹ sư bậc cao (Senior Engineer) để chốt phương án. Quy trình 4 bước, mất từ 20 đến 60 phút/lượt. |
| **3. Bottleneck** | Bước 3 & 4 (mất 20-60 phút): Tra cứu thủ công mã lỗi DTC qua các file PDF rải rác để map với triệu chứng thực tế, và sự phụ thuộc quá lớn vào kinh nghiệm của Senior Engineer khi gặp các ca khó. |
| **4. Business Impact** | Tình trạng thắt cổ chai làm giảm công suất phục vụ tại xưởng dịch vụ, kéo dài thời gian chờ của khách hàng. Việc leo thang ca bệnh liên tục (35%) làm cạn kiệt băng thông của đội ngũ Senior, trong khi tỷ lệ sửa đúng ngay lần đầu (First-time fix rate) chỉ đạt 70% gây hao phí chi phí bảo hành và giảm CSAT nghiêm trọng. |
| **5. Success Metric** | 1. Giảm thời gian tra cứu tài liệu và chẩn đoán từ 30 phút xuống dưới 2 phút (Efficiency).
2. Giảm tỷ lệ leo thang lên Senior Engineer từ 35% xuống dưới 10% (Resource Optimization).
3. Tăng tỷ lệ sửa chữa thành công ngay lần đầu (First-time fix rate) từ 70% lên trên 90% (Quality). |
| **6. Operational Boundary** | AI được phép truy xuất kho dữ liệu SOP sửa chữa, sơ đồ mạch điện, lịch sử bệnh án xe để tổng hợp và đề xuất checklist kiểm tra/nguyên nhân lõi. CẤM: AI không được quyền tự động chốt phương án thay thế linh kiện đắt tiền hoặc đẩy lệnh sửa chữa vào hệ thống ERP mà không có xác nhận (Approve) của kỹ thuật viên (Bắt buộc HITL); tuyệt đối không hướng dẫn các thao tác bypass/can thiệp phần cứng sai tiêu chuẩn bảo hành. |

---
---
## 3.3. Future-State Flow & AI Fit

* **AI Fit:** Chọn **LLM (RAG Copilot)** (không dùng Agent tự trị hoàn toàn vì quy trình sửa chữa liên quan trực tiếp đến an toàn kỹ thuật và hệ thống điện áp cao của xe điện. Rủi ro khi AI tự động ra quyết định thay thế linh kiện sai có thể gây nguy hiểm hoặc thiệt hại lớn về chi phí). AI ở đây hoạt động như một trợ lý ảo, truy xuất thông tin và mớm lời, quyết định cuối cùng vẫn thuộc về Kỹ thuật viên (Human-in-the-loop).
* **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ KTV nhập mã  │     │ 🔵 Auto-pull │     │ 🔵 AI draft  │     │ 🟢 KTV duyệt │
│ DTC và mô tả │ ──→ │ SOP, Manual &│ ──→ │ nguyên nhân &│ ──→ │ checklist &  │
│ lỗi của khách│     │ Lịch sử xe   │     │ checklist test│    │ chốt lệnh sửa│
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Fallback:
                                                               Nếu AI không tìm ra 
                                                               hoặc gợi ý thiếu, KTV 
                                                               tự tra PDF hoặc hỏi 
                                                               Senior như cũ.

```

---
---
### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
* Nguyên liệu đầu vào lý tưởng: VinFast hiện đã có sẵn hệ thống tài liệu số hóa quy chuẩn (SOP, PDF Manuals, sơ đồ mạch điện) và kho dữ liệu lịch sử bảo hành/DTC codes. Dữ liệu này hoàn toàn đáp ứng điều kiện tiên quyết để xây dựng kiến trúc hệ thống RAG (Retrieval-Augmented Generation). 
* Kiểm soát rủi ro bằng HITL (Human-in-the-loop): Kiến trúc hệ thống tuân thủ chặt chẽ ranh giới vận hành: AI chỉ đóng vai trò "Co-pilot" (cố vấn kỹ thuật). Quyền thao tác vật lý lên xe và chốt lệnh xuất kho phụ tùng/đẩy lên ERP 100% phải qua con người phê duyệt. Điều này triệt tiêu hoàn toàn rủi ro AI ảo giác (hallucination) gây thiệt hại tài sản hoặc vi phạm an toàn.
* Động lực thay đổi cao: Đội ngũ Cố vấn dịch vụ và Kỹ thuật viên đang chịu áp lực lớn từ KPI thời gian xử lý và phàn nàn của khách hàng. Việc cung cấp một công cụ giúp họ "nhẹ gánh" và chẩn đoán nhanh sẽ gặp rất ít sự kháng cự khi chuyển đổi số (Change Management).
---