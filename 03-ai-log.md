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
* Card #4 (Vinmec - Phác đồ dinh dưỡng): Ngoài ra dữ liệu về dinh dưỡng của thức ăn và dị ứng cần được chuẩn bị

* Card #1 (VinFast - Dự đoán bảo trì Robot hàn): Bài toán Predictive Maintenance dùng dữ liệu Time-series/Sensor telemetry rất nhiễu. Thường đòi hỏi tốn rất nhiều thời gian làm sạch dữ liệu và huấn luyện mô hình Machine Learning truyền thống phức tạp hơn là dùng Agent/LLM.

*Nhóm tác động kinh doanh (Impact) thấp hơn hoặc quy mô hẹp hơn:

* Card #7 (Vinhomes CSKH) & Card 9 (Xanh SM CSKH): Tự động hóa CSKH bằng LLM rất dễ làm và chắc chắn thành công. Tuy nhiên, đây là bài toán dễ, tính đột phá chiến lược không cao bằng việc giải quyết lõi kỹ thuật của xe điện.

* Card #5 (Marketing - Social Listening): Hiện tại trên thị trường đã có rất nhiều SaaS chuyên dụng làm Social Listening rất tốt. Tự build lại một hệ thống Multimodal có thể tốn kém (compute cost cao cho video/audio) mà ROI không vượt trội so với mua tool.

*Nhóm lệch pha công nghệ:

* Card #6 (Xanh SM - Điều phối trạm sạc): Bài toán này giải quyết bằng thuật toán tối ưu (Operations Research) và Rule-based truyền thống, không có nhiều dư địa cho sự đột phá của LLM hay AI Agent.

* Card #2 (VinFast - QC ngoại quan): Đây là bài toán Computer Vision truyền thống (Vision Inspection), yêu cầu đầu tư lớn vào phần cứng (Camera, Edge Computing) và setup môi trường ánh sáng tại xưởng, chi phí Capex cao và triển khai khá cồng kềnh so với một giải pháp phần mềm thuần túy.
---

*   **AI giúp gì:** Bạn đã dùng AI để làm gì? Brainstorm ý tưởng, điền problem card nhanh, phân tích lựa chọn của nhóm, Vẽ nhanh trên draw.io, hỗ trọ code prototype.
*   **AI sai gì:** Chọn sai loại Architecture trên problem card, phân tích còn chưa đúng.
*   **Sửa đổi ra sao:** bổ sung, chỉnh sửa trực tiếp trên câu trả lời của AI.
