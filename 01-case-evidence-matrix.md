# Case Evidence Matrix

## A. Case Evidence Matrix — Case 1: Starbucks Deep Brew

**Nguồn tham khảo:**
- [Starbucks Deep Brew: Personalisation at Scale — MetaLumna](https://metalumna.com/articles/starbucks-deep-brew-personalization-at-scale)
- [How Starbucks uses AI to make a 30% ROI — AI Tool Report](https://www.aitoolreport.com/articles/how-starbucks-uses-ai-to-make-a-30-roi)
- [Starbucks doubles down on baristas, not AI — Business Insider](https://businessinsider.com/starbucks-investing-humans-rivals-bet-ai-2025-5)
- [Starbucks Reboots Its AI Approach After Automation Stalls — CIO](https://www.cio.inc/starbucks-reboots-its-ai-approach-after-automation-stalls-a-29240)
- [Deep Brew: How Starbucks Turns Data Into Double-Digit Growth — All The Meta](https://allthemeta.substack.com/p/deep-brew-how-starbucks-turns-data)
- [Starbucks Deep Brew: AI-Powered Customer Experience — Ivey Business School / The Case Centre](https://www.thecasecentre.org/products/view?id=205759)

| Trường | Trả lời |
|---|---|
| Case | Starbucks Deep Brew — AI platform cho personalization, labor scheduling, inventory management |
| AI được dùng trong workflow nào? | (1) Personalized recommendations qua app/drive-thru; (2) Labor scheduling dựa trên demand forecasting; (3) Inventory forecasting để giảm spoilage; (4) Predictive equipment maintenance cho máy pha Mastrena |
| Người dùng chính là ai? | Barista, shift lead, store manager, khách hàng qua app/drive-thru |
| Họ đo metric gì? | Promo ROI (+30%), ticket size (+12%), same-store sales (+6%), spoilage reduction (15-20%), drive-thru wait time (-25s peak hour), Rewards member spend (3x non-member), food attach rate (+6%) |
| Metric đó thuộc layer nào? | Activation: personalized touch-points (400M/day); Productivity: wait time reduction, labor savings; Quality: spoilage reduction; Trust: barista override rate (không công bố); Value: promo ROI, ticket size, same-store sales |
| Metric đó chứng minh được gì? | AI tạo doanh thu rõ ràng (ROI promo, ticket size), vận hành tốt hơn (giảm waste, giảm wait time), và loyalty tăng (member spend 3x) |
| Metric đó chưa chứng minh được gì? | (1) Không tách được doanh thu từ AI vs. từ loyalty program vốn đã mạnh trước Deep Brew; (2) Không biết override rate của barista — nếu barista override nhiều thì AI không đáng tin; (3) Quality đồ uống có giảm không khi speed tăng; (4) Siren System tự động hóa pha chế đã gây hỗn loạn vận hành — metric productivity của 1 workflow có thể phá workflow khác |
| Thiếu metric nào? | Barista override rate, employee satisfaction/NPS trước và sau AI, cross-workflow conflict (mobile order volume tăng nhưng barista overload), customer complaint rate theo độ phức tạp order |
| Rủi ro lớn nhất | AI tối ưu 1 workflow (speed) có thể phá workflow khác (quality, employee wellbeing). Siren System là ví dụ: tự động hóa pha chế gây hỗn loạn, phải dừng năm 2025 |
| Bài học cho dashboard nhóm | (1) Metric productivity phải đi kèm quality và trust; (2) Cần đo cross-workflow impact; (3) Override rate là metric trust quan trọng; (4) AI hỗ trợ con người tốt hơn là thay thế |

---

## A. Case Evidence Matrix — Case 2: Zillow Zestimate / Zillow Offers

**Nguồn tham khảo:**
- [Flip Flop: Why Zillow's Algorithmic Home Buying Venture Imploded — Stanford GSB](https://www.gsb.stanford.edu/insights/flip-flop-why-zillows-algorithmic-home-buying-venture-imploded)
- [Zillow's home-buying debacle shows how hard it is to use AI to value real estate — CNN](https://www.cnn.com/2021/11/09/tech/zillow-ibuying-home-zestimate)
- [When Strength Turns Into Weakness: Exploring the Role of AI in the Closure of Zillow Offers — JISE](https://jise.org/Volume35/n1/JISE2024v35n1pp67-72.html)
- [Why Zillow Couldn't Make Algorithmic House Pricing Work — WIRED](https://www.wired.com/story/zillow-ibuyer-real-estate/)
- [Zillow Offers iBuying Zestimate algorithm — AIAAIC Incident Repository](https://www.aiaaic.org/aiaaic-repository/ai-algorithmic-and-automation-incidents/zillow-offers-ibuying-zestimate-algorithm)

| Trường | Trả lời |
|---|---|
| Case | Zillow Zestimate / Zillow Offers — iBuying dùng AI định giá nhà để mua bán trực tiếp |
| AI được dùng trong workflow nào? | (1) Zestimate ước giá nhà cho người dùng tham khảo; (2) Zillow Offers dùng Zestimate làm cơ sở đặt giá mua nhà; (3) Pricing algorithm ("Zprices") quyết định giá mua từng nhà; (4) Inventory management — mua bán hàng nghìn nhà cùng lúc |
| Người dùng chính là ai? | Người bán nhà chấp nhận giá AI, Zillow operations team, investors |
| Họ đo metric gì? | Số nhà mua (27,000 trong 3 năm), Zestimate median error rate (1.9% on-market, 6.9% off-market), thời gian xử lý offer, revenue target ($20B/năm) |
| Metric đó thuộc layer nào? | Activation: số nhà mua; Productivity: tốc độ xử lý offer; Quality: Zestimate error rate; Trust: số người chấp nhận giá AI; Value: revenue target |
| Metric đó chứng minh được gì? | AI xử lý được quy mô lớn (27,000 nhà), ước giá nhanh, có người dùng chấp nhận |
| Metric đó chưa chứng minh được gì? | (1) 27,000 nhà mua nhưng chỉ bán được ~17,000 → inventory imbalance; (2) Error rate 1.9% nghe nhỏ nhưng = ~$10K/nhà $500K × nghìn nhà = thiệt hại lớn; (3) Không đo adverse selection — ai là người chấp nhận giá AI? Người bán nhà chất lượng thấp chấp nhận nhiều hơn → portfolio lệch; (4) Không đo distribution shift — model huấn luyện trên data trước COVID không hoạt động khi thị trường thay đổi |
| Thiếu metric nào? | Adverse selection rate (chất lượng nhà chấp nhận vs. từ chối), error × volume (sai số nhân quy mô), inventory turnover rate, sell-through rate, distribution shift detection, human override rate (Zillow bid cao hơn chính model gợi ý) |
| Rủi ro lớn nhất | Dùng model tham khảo (Zestimate) làm decision engine (mua nhà tiền thật) — accuracy cho consumer estimate ≠ accuracy cho financial decision. Zillow còn bid cao hơn model gợi ý để giành thị phần, override chính AI của mình |
| Bài học cho dashboard nhóm | (1) Accuracy ≠ Decision-readiness — sai số nhỏ dùng tham khảo có thể thảm họa khi dùng ra quyết định; (2) Metric phải đo ai chấp nhận giá AI (adverse selection); (3) Cần metric error × volume; (4) Mục tiêu tăng trưởng không được override tín hiệu model |

---

## Tự kiểm tra

- [x] Không chỉ kể chuyện case.
- [x] Có nêu metric cụ thể.
- [x] Có nói metric chứng minh được gì và chưa chứng minh được gì.
- [x] Có ít nhất 1 bài học áp dụng vào dashboard nhóm.