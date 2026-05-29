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

| # | Subsidiary | Lens                           | Mô tả ngắn bài toán                                                                                                                     |
| - | ---------- | ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | Vinhomes   | Tốn thời gian (Time-consuming) | Nhân viên CSKH mất 10–20 phút để đọc, tra lịch sử và soạn phản hồi cho các review 1-star của cư dân trên app/fanpage/email.             |
| 2 | VinFast    | Lặp lại (Repetitive)           | Kỹ thuật viên service center phải lặp đi lặp lại thao tác tra cứu manual kỹ thuật, mã lỗi DTC và lịch sử sửa chữa cho các lỗi phổ biến. |
| 3 | Xanh SM    | Stakeholder Pain               | Khách hàng bức xúc vì thời gian xử lý khiếu nại quên đồ/hoàn tiền chậm do tổng đài viên phải kiểm tra nhiều hệ thống thủ công.          |
| 4 | Vinmec     | AI-upgrade                     | Bác sĩ và điều dưỡng phải nhập lại ghi chú khám bệnh và tóm tắt hồ sơ bệnh án từ trao đổi trực tiếp với bệnh nhân vào hệ thống HIS/EMR. |
| 5 | Vinhomes   | Lặp lại (Repetitive)           | Ban quản lý phải tổng hợp phản ánh cư dân từ app, hotline, Zalo và email rồi phân loại/chuyển ticket thủ công cho từng bộ phận xử lý.   |


---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                      │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Nhân viên CSKH mất nhiều thời gian xử lý và phản hồi        │
│ review 1-star của cư dân Vinhomes.                          │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes │
│                     [ ] Vinmec   [ ] Khác _________________ │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ - Nhân viên CSKH                                            │
│ - Ban quản lý tòa nhà                                       │
│ - Supervisor vận hành                                       │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận review                                            │
│      ──> 2. Đọc & kiểm tra lịch sử ticket                   │
│      ──> 3. Tra policy/SLA                                  │
│      ──> 4. Soạn phản hồi & chờ duyệt                       │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ - Soạn phản hồi & tra lịch sử xử lý                         │
│ - ⏱ 10–20 phút/lượt                                         │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ - Auto summarize issue                                      │
│ - Retrieve policy liên quan                                 │
│ - Generate draft phản hồi                                   │
│ - Detect sentiment & mức độ nghiêm trọng                    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian phản hồi từ 10–20 phút ──> dưới 2 phút     │
│ - Giảm SLA trễ từ ~30% ──> dưới 5%                          │
│ - Tăng ticket xử lý/ngày từ 40 ──> >100                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM [x] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                      │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Kỹ thuật viên VinFast mất nhiều thời gian tra cứu manual    │
│ và chẩn đoán lỗi bảo hành cho khách hàng.                   │
│                                                             │
│ Công ty thành viên: [x] VinFast [ ] Xanh SM [ ] Vinhomes   │
│                     [ ] Vinmec   [ ] Khác _________________ │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ - Kỹ thuật viên service center                              │
│ - Service advisor                                           │
│ - Senior technical support                                  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận mô tả lỗi từ khách                                │
│      ──> 2. Đọc mã lỗi DTC                                  │
│      ──> 3. Tra manual PDF                                  │
│      ──> 4. Hỏi senior engineer & đề xuất sửa chữa          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ - Tra cứu tài liệu & xác định root-cause                    │
│ - ⏱ 20–60 phút/lượt                                         │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ - Retrieve SOP sửa chữa                                     │
│ - Gợi ý nguyên nhân lỗi                                     │
│ - Summarize lịch sử sửa chữa tương tự                       │
│ - Đề xuất checklist kiểm tra                                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian tra cứu từ 30 phút ──> dưới 2 phút         │
│ - Giảm escalation senior từ 35% ──> dưới 10%                │
│ - Tăng first-time fix rate từ 70% ──> >90%                  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                      │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Tổng đài Xanh SM xử lý khiếu nại quên đồ và hoàn tiền      │
│ chậm do phải thao tác nhiều hệ thống thủ công.              │
│                                                             │
│ Công ty thành viên: [ ] VinFast [x] Xanh SM [ ] Vinhomes   │
│                     [ ] Vinmec   [ ] Khác _________________ │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ - Tổng đài viên                                             │
│ - Customer support                                          │
│ - Khách hàng                                                │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận khiếu nại từ khách                                │
│      ──> 2. Kiểm tra lịch sử chuyến đi                      │
│      ──> 3. Tra thông tin tài xế & giao dịch                │
│      ──> 4. Soạn phản hồi & tạo ticket xử lý                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ - Kiểm tra nhiều hệ thống & tổng hợp thông tin              │
│ - ⏱ 15–30 phút/lượt                                         │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ - Auto summarize complaint                                  │
│ - Retrieve trip & policy liên quan                          │
│ - Generate phản hồi khách hàng                              │
│ - Auto routing ticket đúng bộ phận                          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian xử lý từ 30 phút ──> dưới 5 phút           │
│ - Giảm ticket routing sai từ 15% ──> dưới 3%                │
│ - Tăng CSAT thêm >20%                                       │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM [x] Agent │
└─────────────────────────────────────────────────────────────┘

```