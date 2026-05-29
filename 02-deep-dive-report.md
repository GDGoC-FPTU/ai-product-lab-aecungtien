# Nhóm AEcungtien
Nguyễn Huy Bảo - 2A202600997
Tạ Duy Xuân - 2A202600970
Phạm Ngọc Vinh - 2A202600563
# 🗳️ Tổng hợp Ý tưởng:
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Dây chuyền robot welding thường chỉ được bảo trì sau khi   │
│ phát sinh lỗi, gây downtime và ảnh hưởng sản lượng.        │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ Maintenance Engineer, Production Supervisor                │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Robot phát sinh alarm                                 │
│      ──> 2. Technician kiểm tra log PLC/SCADA              │
│      ──> 3. Gọi maintenance lead phân tích nguyên nhân     │
│      ──> 4. Shutdown line để sửa chữa                      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Root-cause analysis & xác định thời điểm cần bảo trì       │
│ (⏱ 30–90 phút/lần incident)                                │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Phân tích sensor telemetry để dự đoán failure trước khi    │
│ line bị stop.                                              │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm unplanned downtime từ ~12h/tháng ──> dưới 5h/tháng │
│ - Giảm MTTR từ 75 phút ──> dưới 30 phút                    │
│ - Giảm emergency maintenance ticket ~40%                   │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ✓] Rule  [ ] LLM  [] Agent                    │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ QC viên kiểm tra ngoại quan xe/l linh kiện bằng mắt thường │
│ dễ fatigue và bỏ sót defect trong ca sản xuất lớn.         │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ QC Inspector, QA Manager                                   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Xe/l linh kiện đi qua checkpoint QC                   │
│      ──> 2. Inspector kiểm tra bằng mắt                    │
│      ──> 3. Ghi nhận defect thủ công                       │
│      ──> 4. Chuyển xe sang rework hoặc pass                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Kiểm tra ngoại quan thủ công                               │
│ (⏱ 3–7 phút/xe)                                            │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ Computer vision tự động detect scratch, lệch khe, lỗi sơn,│
│ weld defect theo thời gian thực.                           │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm defect escape rate từ 1.8% ──> dưới 0.5%            │
│ - Giảm inspection time từ 5 phút ──> dưới 1 phút/xe        │
│ - Tăng inspection coverage từ sampling ──> 100%            │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [✓] Rule  [ ] LLM  [ ] Agent                    │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Technician tại xưởng dịch vụ mất nhiều thời gian tra SOP   │
│ và đọc fault code khi chẩn đoán lỗi xe EV.                 │
│                                                             │
│ Công ty thành viên: [✓] VinFast                            │
│                     [ ] Xanh SM  [ ] Vinhomes              │
│                     [ ] Vinmec   [ ] Khác                  │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ Service Technician, Service Advisor                        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                     │
│   1. Xe vào xưởng với fault code                           │
│      ──> 2. Technician đọc DTC log                         │
│      ──> 3. Tra SOP/service manual                         │
│      ──> 4. Đề xuất sửa chữa & thay thế linh kiện          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ Tra cứu tài liệu & xác định root cause                     │
│ (⏱ 20–45 phút/case)                                        │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ LLM copilot gợi ý nguyên nhân khả dĩ, SOP liên quan và     │
│ repair sequence dựa trên fault code + lịch sử sửa chữa.    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm diagnosis time từ 45 phút ──> dưới 15 phút          │
│ - Tăng first-time-fix rate từ 72% ──> trên 88%             │
│ - Giảm repeated repair claim ~30%                          │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ] Rule  [✓] LLM  [ ] Agent                    │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #4                                       │
│                                                             │
│ Bài toán (1 câu): Khớp nối thủ công hàng trăm nguyên liệu   │
│ và bệnh án để lên phác đồ dinh dưỡng gây quá tải cho y bác sĩ.│
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị & Chuyên gia dinh dưỡng│
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Đọc hồ sơ/chỉ số sinh tồn ──> 2. Tra cứu tiền sử dị ứng│
│   ──> 3. Chọn nguyên liệu thực phẩm ──> 4. Lên thực đơn/phác đồ│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 15-20 phút/ca)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3 & 4. Xây dựng  │
│ hệ thống RAG kết hợp cơ sở dữ liệu vector (pgvector) để truy│
│ xuất nhanh hàng ngàn record thực đơn, tự động sinh phác đồ. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian thiết kế thực đơn từ 20 phút ──> dưới 2 phút,│
│   duy trì độ chính xác y khoa 100% qua phê duyệt cuối."     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #5                                       │
│                                                             │
│ Bài toán (1 câu): Lỗ hổng trong việc rà soát thủ công bình  │
│ luận đa phương tiện (text, âm thanh, video) khiến việc phát │
│ hiện khủng hoảng truyền thông bị chậm trễ.                  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác (Ghi rõ) Dùng     |
|                                      chung trong marketing  ││                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH & Đội ngũ Social Listening│
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Quét các hội nhóm/diễn đàn ──> 2. Nghe/Xem/Đọc thủ công│
│   ──> 3. Đánh giá sắc thái (Sentiment) ──> 4. Báo cáo rủi ro│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 10 phút/post) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Phân tích đầu vào. Đẩy│
│ pipeline dữ liệu qua các mô hình Multimodal LLM để xử lý    │
│ đồng thời văn bản, video và bóc băng âm thanh (Speech-to-Text).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Tăng tỷ lệ bao phủ dữ liệu MXH từ 30% ──> >95%, giảm lead │
│   time phát cảnh báo khủng hoảng từ 4 giờ ──> dưới 5 phút."  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #6                                       │
│                                                             │
│ Bài toán (1 câu): Tài xế bị "Range Anxiety", tập trung sạc  │
│ vào giờ cao điểm tại các trạm lớn gây ách tắc cục bộ.       │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế Xanh SM                         │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Check lượng pin lửng lơ ──> 2. Tự mở app tìm trạm lớn  │
│   ──> 3. Lái xe chạy rỗng tới trạm ──> 4. Xếp hàng chờ sạc  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 4 (⏱ 45-90 phút/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2. Cắt đứt thói  │
│ quen tự tìm trạm bằng hệ thống Smart Charging Dispatch, tự  │
│ động tính toán lộ trình và điều hướng tài xế đến trạm rảnh. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian chờ đợi tại trạm (Idle Time) từ 45 phút   │
│   ──> dưới 10 phút/lượt; giảm 15% tỷ lệ km chạy rỗng."       │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #7                                      │
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
│ Quick Architecture: [ ] No AI  [ ] Rule  [] LLM [x] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #8                                      │
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
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM [] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #9                                      │
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
│ Quick Architecture: [ ] No AI  [ ] Rule  [] LLM [x] Agent │
└─────────────────────────────────────────────────────────────┘
```
---

# 🗳️ Quyết định lựa chọn của nhóm:
Nhóm quyết định chọn bài toán **"Card #8 — Kỹ thuật viên VinFast mất nhiều thời gian tra cứu manual và chẩn đoán lỗi bảo hành cho khách hàng.   "** để thực hiện Deep-Dive.
---
## Lý do lựa chọn và loại bỏ các thẻ khác:
Lý do lựa chọn (Why it wins):

Độ khả thi về công nghệ (High Feasibility): Bài toán tra cứu tài liệu (SOP, Manual) và gợi ý chẩn đoán dựa trên mã lỗi DTC là mảnh đất hoàn hảo cho GenAI (cụ thể là kiến trúc RAG - Retrieval-Augmented Generation). Dữ liệu đầu vào (PDF manual, lịch sử sửa chữa) đã có sẵn dưới dạng text.

Giá trị chiến lược (High ROI & Strategic Impact): Nút thắt lớn nhất của xe điện (EV) hiện nay không chỉ là bán xe, mà là năng lực dịch vụ hậu mãi (After-sales). Việc giảm sự phụ thuộc vào các "Senior Engineer" và trao quyền cho KTV cấp thấp xử lý lỗi nhanh chóng sẽ giúp VinFast mở rộng quy mô xưởng dịch vụ dễ dàng hơn, trực tiếp tăng độ hài lòng của khách hàng (First-time fix rate >90%).

Rủi ro kiểm soát được (Human-in-the-loop): AI chỉ đóng vai trò "Copilot" (gợi ý SOP, checklist). Quyết định vặn ốc nào, thay linh kiện nào vẫn do KTV thực hiện. Điều này giúp hạn chế rủi ro "ảo giác" (hallucination) của AI gây hậu quả nghiêm trọng.
---
## Nhóm rủi ro chuyên môn/Phức tạp về dữ liệu (Rất khó làm chuẩn):
---
---
* Card #4 (Vinmec - Phác đồ dinh dưỡng): Dù RAG có thể làm tốt, nhưng y tế đòi hỏi độ chính xác tuyệt đối (100%) nên còn cần xác nhận tư nhân viên y tế. Ngoài ra dữ liệu về dinh dưỡng của thức ăn và dị ứng cần được chuẩn bị

* Card #1 (VinFast - Dự đoán bảo trì Robot hàn): Bài toán Predictive Maintenance dùng dữ liệu Time-series/Sensor telemetry rất nhiễu. Thường đòi hỏi tốn rất nhiều thời gian làm sạch dữ liệu và huấn luyện mô hình Machine Learning truyền thống phức tạp hơn là dùng Agent/LLM.

*Nhóm tác động kinh doanh (Impact) thấp hơn hoặc quy mô hẹp hơn:

* Card #7 (Vinhomes CSKH) & Card 9 (Xanh SM CSKH): Tự động hóa CSKH bằng LLM rất dễ làm và chắc chắn thành công. Tuy nhiên, đây là bài toán "nhà nhà đều làm", tính đột phá chiến lược không cao bằng việc giải quyết lõi kỹ thuật của xe điện.

* Card #5 (Marketing - Social Listening): Hiện tại trên thị trường đã có rất nhiều SaaS chuyên dụng làm Social Listening rất tốt. Tự build lại một hệ thống Multimodal có thể tốn kém (compute cost cao cho video/audio) mà ROI không vượt trội so với mua tool.

*Nhóm lệch pha công nghệ:

* Card #6 (Xanh SM - Điều phối trạm sạc): Bài toán này giải quyết bằng thuật toán tối ưu (Operations Research) và Rule-based truyền thống, không có nhiều dư địa cho sự đột phá của LLM hay AI Agent.

* Card #2 (VinFast - QC ngoại quan): Đây là bài toán Computer Vision truyền thống (Vision Inspection), yêu cầu đầu tư lớn vào phần cứng (Camera, Edge Computing) và setup môi trường ánh sáng tại xưởng, chi phí Capex cao và triển khai khá cồng kềnh so với một giải pháp phần mềm thuần túy.
---

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