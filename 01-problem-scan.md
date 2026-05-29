# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 |Predictive Maintenance cho dây chuyền hàn, sơn, robot assembly |Time-consuming |Downtime do nhiều lý do không chỉ máy hỏng, có thể line stop cascade, overtime recovery, bảo trì theo lịch và phụ thuộc kinh nghiệm kỹ thuật viên  |
| 2 |Manual Quality Inspection ở body, paint, battery, final assembly |Repetitive |QC viên phải kiểm tra ngoại quan hàng nghìn linh kiện/xe mỗi ngày bằng mắt thường, dễ fatigue và bỏ sót defect. |
| 3 |AI Production Scheduling & Material Planning |Time-consuming |Planner phải liên tục chỉnh schedule sản xuất và xử lý thiếu vật tư bằng Excel/email thủ công khi có biến động supply chain hoặc thay đổi sản lượng. |
| 4 |Warranty Claim & Service Diagnostics Copilot |Stakeholder Pain |Technician/service advisor mất nhiều thời gian tra cứu SOP, đọc fault code và chẩn đoán lỗi, dẫn đến sửa chữa chậm và repeated repair. |
| 5 |Supplier Quality & Incoming Inspection AI |Repetitive |QA team phải kiểm tra COA/chứng từ và sampling inspection thủ công cho số lượng lớn linh kiện từ supplier, dễ lọt batch lỗi vào production. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Dây chuyền robot welding thường chỉ được bảo trì sau khi   │
│ phát sinh lỗi, gây downtime và ảnh hưởng sản lượng.        │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ Maintenance Engineer, Production Supervisor                │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Robot phát sinh alarm                                 │
│      ──> 2. Technician kiểm tra log PLC/SCADA              │
│      ──> 3. Gọi maintenance lead phân tích nguyên nhân     │
│      ──> 4. Shutdown line để sửa chữa                      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Root-cause analysis & xác định thời điểm cần bảo trì       │
│ (⏱ 30–90 phút/lần incident)                                │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Phân tích sensor telemetry để dự đoán failure trước khi    │
│ line bị stop.                                              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm unplanned downtime từ ~12h/tháng ──> dưới 5h/tháng │
│ - Giảm MTTR từ 75 phút ──> dưới 30 phút                    │
│ - Giảm emergency maintenance ticket ~40%                   │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [✓] Rule  [ ] LLM  [] Agent                    │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ QC viên kiểm tra ngoại quan xe/l linh kiện bằng mắt thường │
│ dễ fatigue và bỏ sót defect trong ca sản xuất lớn.         │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ QC Inspector, QA Manager                                   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Xe/l linh kiện đi qua checkpoint QC                   │
│      ──> 2. Inspector kiểm tra bằng mắt                    │
│      ──> 3. Ghi nhận defect thủ công                       │
│      ──> 4. Chuyển xe sang rework hoặc pass                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Kiểm tra ngoại quan thủ công                               │
│ (⏱ 3–7 phút/xe)                                            │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Computer vision tự động detect scratch, lệch khe, lỗi sơn,│
│ weld defect theo thời gian thực.                           │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm defect escape rate từ 1.8% ──> dưới 0.5%            │
│ - Giảm inspection time từ 5 phút ──> dưới 1 phút/xe        │
│ - Tăng inspection coverage từ sampling ──> 100%            │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [✓] Rule  [ ] LLM  [ ] Agent                    │
└─────────────────────────────────────────────────────────────┘

```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Technician tại xưởng dịch vụ mất nhiều thời gian tra SOP   │
│ và đọc fault code khi chẩn đoán lỗi xe EV.                 │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ Service Technician, Service Advisor                        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Xe vào xưởng với fault code                           │
│      ──> 2. Technician đọc DTC log                         │
│      ──> 3. Tra SOP/service manual                         │
│      ──> 4. Đề xuất sửa chữa & thay thế linh kiện          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Tra cứu tài liệu & xác định root cause                     │
│ (⏱ 20–45 phút/case)                                        │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ LLM copilot gợi ý nguyên nhân khả dĩ, SOP liên quan và     │
│ repair sequence dựa trên fault code + lịch sử sửa chữa.    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm diagnosis time từ 45 phút ──> dưới 15 phút          │
│ - Tăng first-time-fix rate từ 72% ──> trên 88%             │
│ - Giảm repeated repair claim ~30%                          │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ] Rule  [✓] LLM  [ ] Agent                    │
└─────────────────────────────────────────────────────────────┘

```
> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*
