# Product ROI Dashboard — AI Math Tutor (K-12 Vietnamese Math Education)

---

## Part A — Adoption Context

### A.1 Thách Thức Nhóm Chọn

| Trường | Trả lời |
|---|---|
| Thách thức áp dụng AI | Học sinh dùng AI để "xin đáp án ăn liền" thay vì học theo phương pháp Socratic; giáo viên chưa tin tưởng chấm điểm AI; phụ huynh lo ngại con phụ thuộc AI |
| Tình huống xuất phát từ ai / ở đâu? | HS lớp 6–9 thấy Socratic hỏi ngược "chậm", tắt chế độ scaffolding để xin đáp án trực tiếp; GV thấy AI chấm bài tự luận sai với lời giải biến thể hợp lệ; phụ huynh không thấy bằng chứng con tự nghĩ |
| Dấu hiệu bị kẹt | Tỷ lệ HS bấm "Hiện đáp án ngay" cao ở mode deep_solve; GV vẫn chấm thủ công 80% bài tự luận; phụ huynh không mở dashboard vì không hiểu metric |
| Vì sao thách thức này đáng giải quyết? | Nếu HS chỉ copy đáp án thì platform trở thành công cụ gian lận thay vì tutor. Nếu GV không tin chấm điểm AI thì không scale được khối lượng bài tập. Nếu phụ huynh rút lui thì mất nguồn trả phí chính |

### A.2 Sản Phẩm / Công Cụ AI

| Trường | Trả lời |
|---|---|
| Tên sản phẩm / công cụ AI | AI Math Tutor — Multi-agent platform giảng dạy Toán lớp 6–9 (SGK Việt Nam) với 2-agent pipeline (Reasoning + Socratic) |
| Người dùng chính | Học sinh lớp 6–9, giáo viên Toán THCS, phụ huynh |
| Bối cảnh sử dụng | Trường THCS Việt Nam, học thêm tại nhà, luyện tập SGK + SBT, chuẩn bị kiểm tra định kỳ |
| Mục tiêu kinh doanh / học tập / vận hành | Tăng mastery toán học (learning gain), giảm thời gian chuẩn bị bài của GV, tăng retention HS, tạo doanh thu từ gói premium |
| Không nằm trong phạm vi | Học sinh tiểu học hoặc THPT, môn không phải Toán, nội dung ngoài chương trình SGK, tính năng social/forum |

### A.3 2-4 Quy Trình Chính

| # | Tên quy trình | Vai trò AI | Điểm người kiểm tra | Khi AI sai thì xử lý thế nào? |
|---|---|---|---|---|
| 1 | Notebook Giải Toán AI (Socratic + 2-agent) | Recommend / Generate | HS xem lời giải từng bước, tự đánh giá hiểu hay chưa; phụ huynh review lịch sử hội thoại | HS report "giải sai"; GV override lời giải trong teacher dashboard; SymPy verify catch lỗi số học |
| 2 | Practice Session — Luyện tập & chấm điểm | Classify / Grade | GV review bài tự luận được AI chấm; HS xem rubric và phản hồi | GV override điểm + ghi nhận lý do; SymPy symbolic verify fallback; LLM re-grade khi HS appeal |
| 3 | Chat Workspace — Trò chuyện đa chế độ | Generate / Recommend | HS chọn mode (chat/deep_solve/quiz...); Safety guardrail kiểm tra nội dung trước khi gửi | HS report off-topic; Safety middleware block nội dung không phù hợp; Teacher flag conversation |
| 4 | Teacher Dashboard — Giao bài & theo dõi tiến độ | Forecast / Recommend | GV review AI-generated homework và progress forecast trước khi publish | GV override bài giao hoặc điều chỉnh độ khó; manual reassignment nếu forecast sai |

### A.4 Chẩn Đoán Nhanh ADKAR

| Stage | Câu hỏi | Nhận định nhóm |
|---|---|---|
| Awareness | Người dùng có biết AI này giúp gì không? | Có — HS/GV biết app có AI giải toán và chấm điểm; phụ huynh biết có dashboard theo dõi |
| Desire | Người dùng có muốn dùng đúng cách không? | Hạn chế — HS thấy Socratic "chậm" hơn xin đáp án ngay; GV thấy AI chấm chưa chuẩn với lời giải biến thể; phụ huynh chưa thấy giá trị để mở dashboard thường xuyên |
| Knowledge | Người dùng có biết dùng đúng không? | Có — HS biết các mode; GV biết cách giao bài; nhưng GV có thể không biết khi nào nên override vs. khi nào AI đúng |
| Ability | Người dùng có đủ access, thời gian, kỹ năng không? | Có — app chạy trên browser/mobile, nhưng thời gian mỗi buổi học giới hạn; TTS giúp HS kém đọc |
| Reinforcement | Có cơ chế khiến họ quay lại dùng đúng không? | Yếu — chưa có incentive rõ ràng cho HS kiên nhẫn theo Socratic; chưa có cơ chế khuyến khích GV tin tưởng chấm AI; phụ huynh không được cảnh báo proactive |

**Barrier chính: Desire + Reinforcement** — HS không muốn đợi Socratic; GV không được khuyến khích để AI chấm; phụ huynh không được nhắc nhở khi con phụ thuộc AI.

### A.5 3 Tactic Áp Dụng

| Tactic | Nhắm vào barrier nào? | Áp dụng cho quy trình nào? | Người phụ trách | Khi nào hoàn thành? |
|---|---|---|---|---|
| 1. Socratic gating — HS phải thử ≥ 2 lần hoặc trả lời 1 câu hỏi gợi mở trước khi AI hiện đáp án đầy đủ; track "attempt_before_answer" | Desire | Notebook Giải Toán AI | Product Lead | Tuần 2-4 |
| 2. GV QA sample hằng tuần — random 5% bài tự luận được AI chấm sẽ được GV review lại; đo GV override rate và lý do | Reinforcement | Practice Session | CX QA Lead | Tuần 1-8 |
| 3. Parent alert dashboard — khi tỷ lệ "xin đáp án trực tiếp" của HS > 60% hoặc GV override rate > 30%, tự động gửi email cảnh báo phụ huynh + hiện badge trên dashboard | Reinforcement | Tất cả 4 workflow | District Manager / Parent Success | Tuần 2-6 |

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
| Activation | % eligible exercises có AI tutoring | 55% (bài tập có dùng AI hint/giải) | 80% | Notebook + Practice logs | Product Lead | Activation cao không nghĩa là HS học được — có thể chỉ xin đáp án | Thêm "% AI interactions với ≥ 1 attempt trước khi nhận đáp án" |
| Retention / Value | 7-day student retention rate | Chưa đo chính xác (v1 thiếu) | ≥ 60% | Auth + Activity logs | Growth Lead | Retention cao có thể do bắt buộc dùng (GV giao bài), không phải AI giúp ích | Thêm "voluntary return rate" (HS tự mở app ngoài giờ giao bài) |
| Trust / Quality | Tỷ lệ HS "bypass Socratic" để xin đáp án trực tiếp | Chưa đo (v1 thiếu) | < 30% | Notebook mode-switch logs | Product Lead | Không đo bypass rate thì không biết HS có đang học hay copy | **Thêm ở v2** — đo bypass rate + lý do (dễ quá/khó quá/mệt) |

### B.2 Chỉ Số Theo Từng Quy Trình

#### Quy trình 1 — Notebook Giải Toán AI (Socratic + 2-agent)

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % bài toán có AI suggestion được dùng | 60% | ≥ 85% | Notebook logs | Product Lead | Dùng suggestion không nghĩa là HS hiểu bài | Đo "% HS trả lời đúng câu hỏi Socratic tiếp theo" |
| Engagement | Avg session length (phút) | 12 phút | Duy trì ≥ 15 | Session analytics | Growth Lead | Dài hơn nhưng có thể do treo tab | Đo "active interaction time" (có keystroke/mouse) |
| Productivity | Time-to-solution (median) | 8 phút | Giảm xuống 6 (vì scaffolding tốt hơn) | Notebook timestamps | Product Lead | Nhanh hơn nhưng có phải do copy không? | Ghép với "attempt count before solution" |
| Quality | Solver accuracy so với SymPy ground truth | 92% | ≥ 95% | Grading engine logs | Data Science Lead | Accuracy trung bình che giọt sai lẻ ở dạng toán khó | **Thêm ở v2** — đo accuracy theo topic, không chỉ trung bình |
| Trust | HS bypass Socratic rate | Chưa đo | < 30% | Mode switch logs | Product Lead | Bypass cao → AI không tạo giá trị học tập; bypass thấp nhưng HS bỏ cuộc → cũng xấu | **Thêm ở v2** — đo bypass rate + drop-off rate sau khi bị gating |
| Value | Learning gain (Δmastery sau 4 tuần) | Chưa đo | ≥ +0.15 mastery | TopicMastery diff | Data Science Lead | Không đo thì không biết AI có giúp HS học tốt hơn không | **Thêm ở v2** — pre/post test mỗi 4 tuần |

#### Quy trình 2 — Practice Session (Luyện tập & chấm điểm)

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % HS dùng practice / tuần | ~40% (estimate) | ≥ 70% | Practice logs | Product Lead | "Dùng" không nghĩa là "làm đến cùng" | Đo % sessions hoàn thành ≥ 3 bài |
| Productivity | Problems solved per session | 4.2 | ≥ 6 | Practice logs | Product Lead | Số lượng cao nhưng sai nhiều? | Ghép với accuracy per session |
| Quality | AI grading accuracy so với GV chấm thủ công | Chưa đo (chưa có GV benchmark) | ≥ 90% agreement | Spot-check sample | CX QA Lead | Không có GV benchmark thì không tin AI grading | **Thêm ở v2** — weekly 5% spot-check GV vs AI |
| Trust | GV override rate trên AI grading | Chưa đo | < 20% | Teacher dashboard logs | Education Lead | Override nhiều → AI chấm không đáng tin | **Thêm ở v2** — đo override rate + phân loại lý do (AI sai / HS biến thể hợp lệ / GV khắt khe hơn rubric) |
| Value | Pre/post-test improvement sau 1 tháng luyện tập | Chưa đo | ≥ 10 điểm so với baseline | Diagnostic test | Data Science Lead | Cải thiện có thể do luyện nhiều, không phải do AI chấm | Tách nhóm "dùng AI grading" vs "GV chấm thủ công" |

#### Quy trình 3 — Chat Workspace (Trò chuyện đa chế độ)

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % active HS dùng workspace / tuần | ~35% (estimate) | ≥ 60% | Workspace logs | Product Lead | Dùng workspace nhiều nhưng toàn chat linh tinh? | Đo "% workspace sessions có ≥ 1 math-related intent" |
| Productivity | Avg turns per conversation | 6.5 | ≥ 8 | Workspace SSE logs | Product Lead | Nhiều turn nhưng toàn smalltalk? | Phân loại turn theo intent (solve / concept / smalltalk) |
| Quality | Hint helpfulness (% HS giải đúng sau khi nhận hint) | Chưa đo | ≥ 70% | ExerciseProgress + HintEvent | Data Science Lead | Không đo thì không biết hint có giúp không | **Thêm ở v2** — track HintEvent.resolved |
| Trust | % HS dùng deep_solve vs chat mode cho bài toán | Chưa đo | ≥ 50% deep_solve cho bài tập | Mode selection logs | Product Lead | Ít dùng deep_solve → HS không tin AI giải sâu | **Thêm ở v2** — đo mode preference theo topic độ khó |
| Value | Topic mastery improvement từ workspace usage | Chưa đo | ≥ +0.10 mastery / tháng | TopicMastery + Workspace join | Data Science Lead | Không đo thì không biết workspace có tạo giá trị học tập không | **Thêm ở v2** — correlation giữa workspace usage và mastery delta |

#### Quy trình 4 — Teacher Dashboard (Giao bài & theo dõi)

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---|---|---|---|---|---|
| Activation | % GV dùng dashboard để giao bài / tuần | ~50% (estimate) | ≥ 80% | Teacher dashboard logs | Education Lead | "Dùng" để giao bài nhưng không xem progress? | Đo "% GV xem progress report sau khi giao bài" |
| Productivity | Time to assign homework (so với thủ công) | Chưa đo | Giảm ≥ 50% | Teacher survey + logs | Education Lead | Nhanh hơn nhưng chất lượng bài giao kém? | Ghép với student accuracy trên AI-assigned vs manually-assigned exercises |
| Quality | Student progress forecast accuracy | Chưa đo | MAPE < 20% | TopicMastery vs actual test | Data Science Lead | Forecast sai → GV mất tin tưởng | **Thêm ở v2** — đo forecast accuracy theo class size |
| Trust | GV override rate trên AI recommendations (bài tập + dự báo) | Chưa đo | < 25% | Teacher dashboard logs | Education Lead | Override nhiều → AI không phản ánh đúng nhu cầu lớp | **Thêm ở v2** — phân loại lý do override (quá khó / quá dễ / ngoài chương trình) |
| Value | Class average improvement (điểm kiểm tra lớp) | Chưa đo | Tăng ≥ 8 điểm so với lớp không dùng AI | School records | Education Lead | Cải thiện có thể do GV giỏi, không phải AI | Tách lớp "dùng AI đầy đủ" vs "dùng cơ bản" |

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
│ PRODUCT HEALTH                     │ │ WORKFLOW 1: NOTEBOOK AI TUTOR       │
│ Metric: Learning gain (Δmastery)   │ │ Metric: HS bypass Socratic rate     │
│ Current: Not measured (v1 gap)     │ │ Current: Not measured (v1 gap)      │
│ Target: ≥ +0.15 after 4 weeks      │ │ Target: < 30%                       │
│ Status: AMBER (need data)          │ │ Status: AMBER (need data)           │
│ Action if red: Add pre/post test;  │ │ Action if red: Tighten gating rules,│
│ segment by topic difficulty        │ │ investigate why HS skip Socratic    │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ WORKFLOW 2: PRACTICE & GRADING     │ │ QUALITY / TRUST                     │
│ Metric: GV override rate on AI     │ │ Metric: Solver accuracy + Hint      │
│ grading                            │ │ helpfulness                         │
│ Current: Not measured (v1 gap)     │ │ Current: Solver 92%; Hint N/A       │
│ Target: < 20%                      │ │ Target: Solver ≥ 95%; Hint ≥ 70%    │
│ Status: AMBER (need data)          │ │ Status: AMBER (need data)           │
│ Action if red: Weekly 5% spot-check  │ │ Action if red: Increase GV sample   │
│ GV vs AI; expand rubric coverage   │ │ review; add SymPy verify on ALL     │
│                                    │ │ numeric answers                     │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ VALUE / COST                       │ │ DECISION                            │
│ Metric: AI cost per student /      │ │                                     │
│ month + Learning efficiency        │ │                                     │
│ Current: Cost unknown; Time-to-    │ │ Metric mạnh nhất: Bypass rate +     │
│ solution 8 min                     │ │ GV override rate                    │
│ Target: Cost ≤ $5/student/month;  │ │ Before scale: (1) Add bypass rate   │
│ Time-to-solution ≤ 6 min           │ │ tracking; (2) Weekly GV QA sample;  │
│ Status: GREEN (cost) / AMBER       │ │ (3) Parent alert when bypass > 60%  │
│ (learning proof)                   │ │                                     │
│ Action if red: Switch to cheaper   │ │                                     │
│ LLM tier for hints; cache common   │ │                                     │
│ questions                          │ │                                     │
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
# Memo Quyết Định Cuối — AI Math Tutor (K-12 Vietnamese Math)

1. Nhóm khuyến nghị: **continue with guardrails**.
   Tiếp tục phát triển và triển khai AI Math Tutor cho 4 workflow chính, nhưng cần thêm metric trust và quality trước khi mở rộng sang trường mới hoặc lớp 10–12. 
   Đặc biệt, cần đảm bảo Socratic gating hoạt động để tránh tình trạng HS phụ thuộc AI (xin đáp án ăn liền) — nếu không, sản phẩm sẽ bị phụ huynh và GV phản đối vì trở thành công cụ gian lận thay vì tutor.

2. Chỉ số mạnh nhất để bảo vệ quyết định là:
   **HS bypass Socratic rate** + **GV override rate trên AI grading**.
   Nếu bypass rate < 30% và GV override rate < 20% → HS đang học đúng cách và GV tin tưởng chấm điểm AI. 
   Nếu bypass rate > 50% → cần siết chặt gating hoặc pivot sang chế độ "guided discovery" khác.
   Nếu GV override rate > 40% → AI grading chưa đủ chuẩn, cần mở rộng rubric và symbolic verify trước khi scale.

3. Chỉ số hoặc giả định nhóm đã sửa sau phản biện là:
   **V1** dùng "DAU/MAU" và "số bài giải/tuần" làm chỉ số Activation và Value chính. 
   Nhóm red-team (đóng vai CFO + Hiệu trưởng) phản biện rằng: DAU cao không nghĩa là HS học được gì; số bài giải cao có thể là do copy đáp án. 
   Không tách được AI contribution từ việc HS tự luyện hoặc GV dạy thêm.
   **V2** đổi thành:
   - "Learning gain (Δmastery sau 4 tuần)" làm metric Value chính — đo trực tiếp AI contribution vào việc HS hiểu bài.
   - "HS bypass Socratic rate" làm metric Trust chính — đo hành vi thực tế (có chịu khó tư duy hay không) thay vì chỉ đo lượt dùng.
   - "GV override rate" làm metric Trust thứ hai — đo niềm tin của GV vào AI grading.
   V2 tốt hơn vì đo trực tiếp giá trị học tập và niềm tin của 2 stakeholder quan trọng nhất (HS và GV), thay vì đo chỉ số mà AI chỉ là 1 trong nhiều yếu tố đóng góp.

4. Trước khi scale, nhóm phải:
   1. Triển khai bypass rate tracking trên Notebook và Workspace — log mỗi lần HS chuyển từ Socratic sang "xin đáp án ngay" — Product Lead — cuối Q2.
   2. Thiết lập GV QA sample hằng tuần (5% random bài tự luận được AI chấm sẽ có GV review lại) — CX QA Lead — tuần 1-8.
   3. Dashboard cảnh báo tự động khi bypass rate > 30% hoặc GV override rate > 30% — gửi email phụ huynh + hiện badge trên dashboard — Parent Success Lead — tuần 2-6.
```

### Tự kiểm tra Part D

- [x] Có quyết định rõ (continue with guardrails).
- [x] Có một chỉ số mạnh nhất (bypass rate + GV override rate).
- [x] Có V1 → V2 cụ thể (DAU/MAU + số bài giải → Δmastery + bypass rate + GV override rate).
- [x] Có 3 việc cần làm trước khi scale, mỗi việc có người phụ trách và deadline.

---

## Red-team và sửa v2

### Nhóm mình đi red-team nhóm khác

| Vai nhóm được giao | Nhóm bị phản biện | 3 câu hỏi / rủi ro nhóm mình nêu |
|---|---|---|
| CFO / Hiệu trưởng | [Tên nhóm] | 1. Chỉ số Value chứng minh tiền/thành tiền ở đâu? Có baseline từ đâu? 2. Có tách được AI contribution khỏi việc HS tự học hoặc GV dạy thêm không? 3. Nếu learning gain không tăng sau 8 tuần thì continue hay dừng? |

### Nhóm mình bị red-team

| Red-team risk | Metric / giả định bị chất vấn | Sửa ở v2 |
|---|---|---|
| DAU/MAU cao không nghĩa là HS học được gì — có thể chỉ treo tab hoặc copy đáp án | Activation metric (DAU, số bài giải/tuần) | Đổi thành Learning gain (Δmastery) + bypass rate + GV override rate |
| Không đo bypass rate → không biết HS có đang học hay chỉ xin đáp án | Trust metric thiếu ở v1 | Thêm bypass rate + lý do bypass (dễ/khó/mệt) ở v2 |
| AI grading chưa có GV benchmark → có thể chấm sai lời giải biến thể hợp lệ | Quality metric thiếu ở v1 | Thêm GV spot-check 5%/tuần + GV override rate + inter-rater agreement |

### Ít nhất 2 thay đổi cụ thể từ v1 sang v2

| # | V1 có vấn đề gì? | V2 sửa thành gì? | Vì sao sửa này tốt hơn? |
|---|---|---|---|
| 1 | Value metric chỉ đo DAU/MAU và số bài giải/tuần — không tách được AI contribution từ việc HS tự học hoặc GV dạy thêm | Đổi thành Learning gain (Δmastery sau 4 tuần, đo bằng pre/post test) + tách nhóm "dùng AI đầy đủ" vs "dùng cơ bản" | Đo trực tiếp AI contribution vào việc HS hiểu bài, thay vì chỉ số mà AI chỉ là 1 trong nhiều yếu tố |
| 2 | Không có metric Trust — không biết HS có đang học đúng cách (Socratic) hay copy đáp án; không biết GV có tin AI grading không | Thêm HS bypass Socratic rate (< 30% target) + GV override rate trên AI grading (< 20% target) + lý do override | Bypass rate đo hành vi thực tế (tự tư duy vs xin đáp án), không phải ý kiến; GV override rate đo niềm tin của người dùng chuyên môn vào AI |

---

## Checklist trước khi nộp

- [x] Có 1 product cụ thể (AI Math Tutor K-12 Việt Nam), không chọn "AI cho cả công ty".
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
