# Product ROI Dashboard — Starbucks Deep Brew AI

---

## Part A — Adoption Context

### A.1 Thách Thức Nhóm Chọn

| Trường | Trả lời |
|---|---|
| Thách thức áp dụng AI | Barista và store manager không tin hoặc không dùng đúng khuyến nghị AI từ Deep Brew |
| Tình huống xuất phát từ ai / ở đâu? | Store manager thấy AI scheduling không phù hợp thực tế cửa hàng; barista bị overload bởi mobile order volume mà AI tạo ra |
| Dấu hiệu bị kẹt | Barista override AI scheduling thường xuyên; Siren System tự động hóa pha chế gây hỗn loạn vận hành, phải dừng; Promo ROI cao nhưng quality ticket và customer complaint tăng theo |
| Vì sao thách thức này đáng giải quyết? | Deep Brew có tín hiệu mạnh (ROI +30%, waste -15-20%) nhưng nếu nhân viên không tin và không dùng đúng thì giá trị không bền vững. Starbucks đã phải dừng Siren System — bài học rằng AI không được nhân viên chấp nhận sẽ thất bại |

### A.2 Sản Phẩm / Công Cụ AI

| Trường | Trả lời |
|---|---|
| Tên sản phẩm / công cụ AI | Starbucks Deep Brew — AI platform cho personalization, scheduling, inventory, maintenance |
| Người dùng chính | Barista, shift lead, store manager, khách hàng qua app và drive-thru |
| Bối cảnh sử dụng | Cửa hàng Starbucks Mỹ — 16,000+ locations, 75M Rewards members, 90M weekly transactions |
| Mục tiêu kinh doanh / học tập / vận hành | Tăng doanh thu (ticket size, promo ROI), giảm lãng phí (spoilage), tối ưu nhân sự (labor scheduling), cải thiện trải nghiệm khách hàng |
| Không nằm trong phạm vi | Siren System (đã dừng), chatbot khách hàng, backend IT operations |

### A.3 2-4 Quy Trình Chính

| # | Tên quy trình | Vai trò AI | Điểm người kiểm tra | Khi AI sai thì xử lý thế nào? |
|---|---|---|---|---|
| 1 | Personalized recommendations (app + drive-thru) | Recommend | Barista / khách hàng review recommendation trước khi chấp nhận | Override recommendation, chọn món khác, ghi nhận feedback |
| 2 | Labor scheduling | Classify / Recommend | Store manager review và adjust schedule trước khi publish | Manager override schedule, minimum hours guarantee, barista feedback |
| 3 | Inventory forecasting | Forecast | Shift lead kiểm tra dự báo vs. thực tế mỗi ca | Điều chỉnh order thủ công, báo cáo sai lệch, model retrain weekly |
| 4 | Predictive equipment maintenance | Classify | Technician xác nhận anomaly trước khi sửa | False positive → technician check và dismiss; false negative → breakdown → sửa khẩn cấp |

### A.4 Chẩn Đoán Nhanh ADKAR

| Stage | Câu hỏi | Nhận định nhóm |
|---|---|---|
| Awareness | Người dùng có biết AI này giúp gì không? | Có — Deep Brew đã tích hợp vào workflow, barista thấy recommendation trên POS và drive-thru screen |
| Desire | Người dùng có muốn dùng không? | Hạn chế — barista thấy mobile order volume tăng (do AI personalization) gây overload; một số thấy AI scheduling cứng nhắc |
| Knowledge | Người dùng có biết dùng đúng không? | Có — training cơ bản, nhưng barista có thể không biết khi nào nên override vs. khi nào nên theo AI |
| Ability | Người dùng có đủ access, thời gian, kỹ năng không? | Có — AI built-in vào POS và app, nhưng thời gian phản ứng trong ca đông đúc bị hạn chế |
| Reinforcement | Có cơ chế khiến họ quay lại dùng không? | Yếu — không có incentive rõ ràng cho barista dùng đúng AI; frequency cap chống spam nhưng không khuyến khích dùng đúng |

**Barrier chính: Desire + Reinforcement** — barista cảm thấy AI thêm workload (mobile order volume) thay vì giảm, và không có cơ chế khuyến khích dùng đúng.

### A.5 3 Tactic Áp Dụng

| Tactic | Nhắm vào barrier nào? | Áp dụng cho quy trình nào? | Người phụ trách | Khi nào hoàn thành? |
|---|---|---|---|---|
| 1. Human-in-loop checklist — barista confirm AI recommendation trước khi thực hiện, với UI hiện "AI suggest X, customer ordered Y, why?" | Desire | Personalized recommendations | Store Ops Lead | Tuần 2-4 |
| 2. QA sample hằng tuần — random 5% AI recommendation được review bởi shift lead, đo override rate và lý do override | Reinforcement | Labor scheduling + Personalized recommendations | CX QA Lead | Tuần 1-8 |
| 3. Dashboard cảnh báo — khi override rate > 30% hoặc repeat complaint tăng, tự động flag cho store manager | Reinforcement | Tất cả 4 workflow | District Manager | Tuần 2-6 |

### Tự kiểm tra Part A

- [x] Có 1 sản phẩm cụ thể.
- [x] Có 4 workflow chính, không chỉ 1.
- [x] Mỗi workflow có vai trò AI, điểm người kiểm tra, cách xử lý khi AI sai.
- [x] Có 1 barrier ADKAR chính (Desire + Reinforcement).
- [x] Tactic có người phụ trách và liên kết với barrier.

---

## Part B — ROI Dashboard

### B.1 Chỉ Số Toàn Sản Phẩm

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % eligible orders có AI recommendation | 60% (Deep Brew markets) | 80% | POS log + app analytics | Product Lead | Activation cao không nghĩa là người dùng theo recommendation — có thể ignore | Thêm "% AI recommendations accepted by barista" |
| Retention / Value | Weekly same-store sales growth | +6% (FY24) | Duy trì ≥5% | Finance P&L | Finance BP | Sales tăng có thể do loyalty program vốn mạnh, không phải AI | Tách AI-attributed revenue (orders with AI recommendation) vs. non-AI |
| Trust / Quality | Barista override rate trên AI recommendation | Chưa đo (v1 thiếu) | <30% | POS log | Store Ops Lead | Không đo override thì không biết barista có tin AI không | **Thêm ở v2** — đo override rate + lý do override |

### B.2 Chỉ Số Theo Từng Quy Trình

#### Quy trình 1 — Personalized recommendations

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % customers nhận personalized offer/tuần | 400M touch-points/day | Duy trì | App analytics | Product Lead | Touch-point count không nói customers unique | Đổi thành "% active members nhận ≥1 personalized offer/tuần" |
| Engagement | Click-through rate trên personalized app card | +18% lift | Duy trì | App analytics | Product Lead | CTR cao nhưng conversion? | Ghép CTR với conversion rate |
| Productivity | Median drive-thru wait time reduction | -25s ở 8AM peak | Duy trì hoặc giảm thêm | POS timestamps | Store Ops Lead | Nhanh hơn nhưng đồ uống đúng không? | Ghép với drink quality score |
| Quality | Repeat complaint rate sau AI recommendation | Chưa đo | ≤ human baseline | Customer service log | CX QA Lead | Không đo thì không biết khách có quay lại phàn nàn không | **Thêm ở v2** — theo dõi repeat complaint trong 7 ngày |
| Trust | Barista override rate trên recommendation | Chưa đo | <30% | POS log | Store Ops Lead | Override cao → AI không đáng tin; override thấp → barista có đang accept bừa? | **Thêm ở v2** — đo override rate + phân loại lý do |
| Value | Promo ROI | +30% | Duy trì ≥25% | Marketing analytics | Marketing Lead | ROI cao nhưng có thể do loyalty program, không phải AI recommendation | Tách AI-attributed promo revenue |

#### Quy trình 2 — Labor scheduling

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % stores dùng AI-generated schedule | ~70% (estimate) | ≥85% | Scheduling system | Store Ops Lead | "Dùng" schedule không nghĩa là không override hàng loạt | Đo % shifts unchanged after manager review |
| Productivity | Labor-hour savings vs. manual schedule | 5-10% | Duy trì ≥5% | Workforce management system | HR Ops Lead | Tiết kiệm giờ nhưng có thể ảnh hưởng chất lượng phục vụ | Ghép với customer satisfaction theo ca |
| Quality | Schedule override rate | Chưa đo | <20% | Scheduling system | Store Ops Lead | Manager override nhiều → model không phản ánh đúng nhu cầu | **Thêm ở v2** — đo override rate + lý do |
| Trust | Barista satisfaction score trên AI schedule | Chưa đo | ≥3.5/5 | Pulse survey | HR Ops Lead | Survey response rate thấp thì data không đáng tin | Đo qua anonymous shift feedback app |
| Value | Overtime cost reduction | Chưa public | Giảm ≥15% vs. baseline | Finance P&L | Finance BP | Giảm overtime nhưng có thể tăng turnover nếu schedule cứng nhắc | Ghép với turnover rate |

#### Quy trình 3 — Inventory forecasting

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % stores dùng AI-driven order | ~80% (estimate) | ≥90% | Inventory system | Supply Chain Lead | Dùng AI order nhưng vẫn adjust thủ công | Đo % orders unchanged after shift lead review |
| Productivity | Spoilage / waste reduction | 15-20% | Duy trì ≥15% | Inventory system | Supply Chain Lead | Waste giảm nhưng có thể do bán hết (stockout) chứ không phải dự báo tốt | Ghép với stockout rate |
| Quality | Forecast accuracy (MAPE) | Chưa public | <10% error | Inventory system | Data Science Lead | MAPE trung bình che giọt sai lẻ ở item quan trọng | **Thêm ở v2** — đo MAPE theo item category, không chỉ trung bình |
| Trust | Shift lead manual adjustment rate | Chưa đo | <25% | Inventory system | Store Ops Lead | Adjust nhiều → model không đáng tin | **Thêm ở v2** — phân loại lý do adjust |
| Value | Cost per item served | Chưa public | Giảm ≥10% vs. baseline | Finance P&L | Finance BP | Cost giảm nhưng có thể do giảm portion, không phải giảm waste | Ghép với customer satisfaction |

### Checklist Part B

- [x] Có 3 chỉ số toàn sản phẩm.
- [x] Mỗi quy trình có ít nhất 4 lớp đo.
- [x] Có nguồn dữ liệu và người phụ trách.
- [x] Có ít nhất 1 chỉ số Quality và Trust.
- [x] Sau phản biện, có cột rủi ro và cột sửa ở v2.

---

## Part C — Dashboard Mock

```text
┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ PRODUCT HEALTH                     │ │ WORKFLOW 1: PERSONALIZATION         │
│ Metric: AI-attributed revenue %    │ │ Metric: Barista override rate       │
│ Current: 6% same-store growth      │ │ Current: Not measured (v1 gap)     │
│ Target: ≥5% sustained              │ │ Target: <30%                        │
│ Status: GREEN                      │ │ Status: AMBER (need data)           │
│ Action if red: Segment AI vs.      │ │ Action if red: Investigate override │
│ non-AI revenue attribution         │ │ reasons, retrain recommendation    │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ WORKFLOW 2: LABOR SCHEDULING       │ │ QUALITY / TRUST                     │
│ Metric: Schedule override rate     │ │ Metric: Repeat complaint rate       │
│ Current: Not measured (v1 gap)    │ │ Current: Not measured (v1 gap)      │
│ Target: <20%                       │ │ Target: ≤ human baseline            │
│ Status: AMBER (need data)          │ │ Status: AMBER (need data)           │
│ Action if red: Manager feedback    │ │ Action if red: QA sample increase,  │
│ loop, adjust forecast inputs       │ │ add human review step               │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ VALUE / COST                       │ │ DECISION                            │
│ Metric: Promo ROI + Waste          │ │ Continue with guardrails            │
│ reduction combined                 │ │                                     │
│ Current: ROI +30%, waste -15-20%   │ │ Metric mạnh nhất: Barista override  │
│ Target: ROI ≥25%, waste ≥15% saved │ │ rate + repeat complaint rate        │
│ Status: GREEN                      │ │ Before scale: (1) Add override rate │
│ Action if red: Re-segment AI vs.   │ │ tracking; (2) QA sample weekly;     │
│ non-AI attribution in P&L          │ │ (3) Dashboard alert when >30%       │
└────────────────────────────────────┘ └────────────────────────────────────┘
```

### Tự kiểm tra Part C

- [x] Có 6 ô.
- [x] Ô đầu là toàn sản phẩm.
- [x] Có ít nhất 1 ô Quality và Trust.
- [x] Có ô Decision.
- [x] Mỗi ô có action nếu đỏ.

---

## Part D — Decision Memo

```markdown
# Memo Quyết Định Cuối — Starbucks Deep Brew

1. Nhóm khuyến nghị: **continue with guardrails**.
   Tiếp tục dùng Deep Brew cho personalization và inventory forecasting, nhưng cần thêm metric trust và quality trước khi mở rộng sang workflow mới. Siren System đã cho thấy AI tối ưu 1 workflow có thể phá workflow khác — cần đo cross-workflow impact trước khi scale.

2. Chỉ số mạnh nhất để bảo vệ quyết định là:
   **Barista override rate** trên AI recommendation. Nếu barista override <30% và lý do override không phải "AI gợi ý sai" mà là "khách yêu cầu khác" → AI đáng tin và tạo giá trị. Nếu override >50% → AI không phù hợp workflow và cần pivot. Override rate là chỉ số trust trực tiếp nhất vì nó đo hành vi thực tế (accept vs. reject) chứ không phải ý kiến.

3. Chỉ số hoặc giả định nhóm đã sửa sau phản biện là:
   **V1** dùng "promo ROI +30%" và "ticket size +12%" làm chỉ số Value chính. Nhóm CFO phản biện rằng những chỉ số này có thể đến từ loyalty program vốn mạnh, không phải từ AI recommendation. Không tách được AI-attributed revenue. **V2** đổi thành "AI-attributed revenue %" (doanh thu từ orders có AI recommendation / tổng doanh thu) và thêm "barista override rate" làm chỉ số Trust chính. V2 tốt hơn vì đo trực tiếp AI contribution và niềm tin của người dùng vào AI, thay vì đo chỉ số mà AI chỉ là 1 trong nhiều yếu tố đóng góp.

4. Trước khi scale, nhóm phải:
   1. Triển khai override rate tracking trên POS cho recommendation và scheduling — Store Ops Lead — cuối Q2
   2. Thiết lập QA sample hằng tuần (5% random recommendations) — CX QA Lead — tuần 1-8
   3. Dashboard cảnh báo tự động khi override rate >30% hoặc repeat complaint tăng — District Manager — tuần 2-6
```

### Tự kiểm tra Part D

- [x] Có quyết định rõ (continue with guardrails).
- [x] Có một chỉ số mạnh nhất (barista override rate).
- [x] Có V1 → V2 cụ thể (promo ROI → AI-attributed revenue % + override rate).
- [x] Có 3 việc cần làm trước khi scale, mỗi việc có người phụ trách và deadline.

---

## Red-team và sửa v2

### Nhóm mình đi red-team nhóm khác

| Vai nhóm được giao | Nhóm bị phản biện | 3 câu hỏi / rủi ro nhóm mình nêu |
|---|---|---|
| CFO | [Tên nhóm] | 1. Chỉ số Value của nhóm chứng minh tiền/thành tiền ở đâu? 2. Baseline từ đâu? Có tách được AI contribution không? 3. Nếu Value không tăng sau 8 tuần thì continue hay dừng? |

### Nhóm mình bị red-team

| Red-team risk | Metric / giả định bị chất vấn | Sửa ở v2 |
|---|---|---|
| Promo ROI +30% có thể đến từ loyalty program, không phải AI | Value metric (promo ROI, ticket size) | Đổi thành AI-attributed revenue % + thêm override rate làm metric Trust |
| Không đo override rate → không biết barista có tin AI không | Trust metric thiếu ở v1 | Thêm barista override rate + lý do override ở v2 |
| Repeat complaint chưa đo → AI recommendation có thể gây trải nghiệm tồi | Quality metric thiếu ở v1 | Thêm repeat complaint rate trong 7 ngày sau AI recommendation |

### Ít nhất 2 thay đổi cụ thể từ v1 sang v2

| # | V1 có vấn đề gì? | V2 sửa thành gì? | Vì sao sửa này tốt hơn? |
|---|---|---|---|
| 1 | Value metric chỉ đo promo ROI (+30%) và ticket size (+12%) — không tách được AI contribution từ loyalty program vốn mạnh | Đổi thành AI-attributed revenue % (doanh thu từ orders có AI recommendation / tổng doanh thu) | Đo trực tiếp AI contribution thay vì chỉ số mà AI chỉ là 1 trong nhiều yếu tố |
| 2 | Không có metric Trust — không biết barista có tin AI recommendation không, override bao nhiêu | Thêm barista override rate (<30% target) + lý do override + repeat complaint rate | Override rate đo hành vi thực tế (accept vs. reject), không phải ý kiến; repeat complaint đo chất lượng output AI |

---

## Checklist trước khi nộp

- [x] Có 1 product cụ thể (Starbucks Deep Brew), không chọn "AI cho cả công ty".
- [x] Có 4 workflow chính.
- [x] Mỗi workflow có vai trò AI, human review và failure path.
- [x] Có rào cản ADKAR chính (Desire + Reinforcement).
- [x] Dashboard có metric toàn product và metric theo workflow.
- [x] Không chỉ đo usage: login, prompt count, DAU/MAU.
- [x] Có baseline, target, data source và owner cho các metric chính.
- [x] Có ít nhất 1 metric Quality, Trust và Value.
- [x] Có Red-team risk và Fix.
- [x] Có ít nhất 2 thay đổi rõ từ v1 sang v2.
- [x] Decision Memo có continue with guardrails.