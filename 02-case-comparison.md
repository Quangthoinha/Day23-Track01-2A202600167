# Case Comparison — Starbucks Deep Brew vs. Zillow Offers

## Nguồn tham khảo

**Starbucks Deep Brew:**
- [Starbucks Deep Brew: Personalisation at Scale — MetaLumna](https://metalumna.com/articles/starbucks-deep-brew-personalization-at-scale)
- [How Starbucks uses AI to make a 30% ROI — AI Tool Report](https://www.aitoolreport.com/articles/how-starbucks-uses-ai-to-make-a-30-roi)
- [Starbucks doubles down on baristas, not AI — Business Insider](https://businessinsider.com/starbucks-investing-humans-rivals-bet-ai-2025-5)
- [Starbucks Reboots Its AI Approach After Automation Stalls — CIO](https://www.cio.inc/starbucks-reboots-its-ai-approach-after-automation-stalls-a-29240)
- [Deep Brew: How Starbucks Turns Data Into Double-Digit Growth — All The Meta](https://allthemeta.substack.com/p/deep-brew-how-starbucks-turns-data)
- [Starbucks Deep Brew: AI-Powered Customer Experience — Ivey Business School / The Case Centre](https://www.thecasecentre.org/products/view?id=205759)

**Zillow Zestimate / Zillow Offers:**
- [Flip Flop: Why Zillow's Algorithmic Home Buying Venture Imploded — Stanford GSB](https://www.gsb.stanford.edu/insights/flip-flop-why-zillows-algorithmic-home-buying-venture-imploded)
- [Zillow's home-buying debacle shows how hard it is to use AI to value real estate — CNN](https://www.cnn.com/2021/11/09/tech/zillow-ibuying-home-zestimate)
- [When Strength Turns Into Weakness: Exploring the Role of AI in the Closure of Zillow Offers — JISE](https://jise.org/Volume35/n1/JISE2024v35n1pp67-72.html)
- [Why Zillow Couldn't Make Algorithmic House Pricing Work — WIRED](https://www.wired.com/story/zillow-ibuyer-real-estate/)
- [Zillow Offers iBuying Zestimate algorithm — AIAAIC Incident Repository](https://www.aiaaic.org/aiaaic-repository/ai-algorithmic-and-automation-incidents/zillow-offers-ibuying-zestimate-algorithm)

---

## Bảng so sánh

| Trường | Case thành công / tín hiệu tốt: Starbucks Deep Brew | Case cảnh báo / thất bại: Zillow Offers |
|---|---|---|
| Case | Starbucks Deep Brew — AI platform cho personalization, scheduling, inventory, maintenance | Zillow Offers — iBuying dùng AI định giá nhà để mua bán trực tiếp |
| Workflow có AI | (1) Personalized recommendations qua app/drive-thru; (2) Labor scheduling; (3) Inventory forecasting; (4) Predictive equipment maintenance | (1) Zestimate ước giá nhà cho người dùng; (2) AI pricing cho Zillow Offers mua nhà; (3) Inventory management mua bán hàng nghìn nhà |
| Metric chính | Promo ROI +30%, ticket size +12%, spoilage -15-20%, drive-thru wait -25s, member spend 3x | 27,000 nhà mua, Zestimate error 1.9% (on-market), $881M total loss, $569M write-down |
| Metric đó chứng minh được gì? | AI tạo doanh thu (ROI, ticket size), giảm lãng phí (spoilage), tăng loyalty (member spend) | AI xử lý quy mô lớn, ước giá nhanh, có người chấp nhận giá |
| Metric đó chưa chứng minh được gì? | Không tách AI impact từ loyalty program vốn mạnh; không biết override rate; quality đồ uống có giảm khi speed tăng; Siren System cho thấy AI tối ưu 1 workflow có thể phá workflow khác | 27,000 mua nhưng chỉ ~17,000 bán; 1.9% error × nghìn nhà = thiệt hại lớn; không đo adverse selection; model không hoạt động khi thị trường thay đổi (COVID) |
| Thiếu metric nào? | Barista override rate, employee satisfaction, cross-workflow conflict, complaint rate theo độ phức tạp | Adverse selection rate, error × volume, inventory turnover, distribution shift detection, human override rate (Zillow bid cao hơn model) |
| Bài học cho dashboard nhóm | (1) Productivity phải đi kèm quality và trust; (2) Cần đo cross-workflow impact; (3) Override rate = metric trust quan trọng; (4) AI hỗ trợ con người tốt hơn thay thế | (1) Accuracy ≠ decision-readiness; (2) Metric phải đo adverse selection; (3) Cần error × volume; (4) Mục tiêu tăng trưởng không được override model |

---

## Câu chốt

```markdown
Case thành công dạy nhóm tôi rằng:
AI tạo giá trị bền vững khi hỗ trợ con người thay vì thay thế, và khi metric productivity đi kèm quality, trust và cross-workflow impact. Starbucks Deep Brew hoạt động vì barista có thể override AI, và metric không chỉ đo speed mà còn đo waste reduction và member spend. Tuy nhiên, Siren System cảnh báo rằng AI tối ưu 1 workflow (pha chế nhanh hơn) có thể phá workflow khác (chất lượng đồ uống, trải nghiệm khách hàng).

Case cảnh báo / thất bại dạy nhóm tôi rằng:
Model tham khảo không tự động thành decision engine. Zestimate sai số 1.9% chấp nhận được khi người dùng tra giá nhà, nhưng khi dùng số đó để mua nhà thật × nghìn giao dịch = thiệt hại $881 triệu. Zillow còn override chính model của mình (bid cao hơn AI gợi ý) để giành thị phần, và không đo adverse selection — chỉ người bán nhà chất lượng thấp mới chấp nhận giá AI. Thiếu metric error × volume, inventory turnover và distribution shift khiến dashboard báo "tốt" trong khi thực tế đang lỗ.

Vì vậy dashboard nhóm tôi phải:
1. Phân biệt rõ metric cho tham khảo vs. metric cho ra quyết định — cùng 1 con số có ý nghĩa khác nhau tùy ngữ cảnh.
2. Đo adverse selection: ai là người dùng AI nhiều nhất, và họ dùng đúng cách hay vì AI dễ/tiễn lợi?
3. Đo cross-workflow impact: khi 1 workflow tăng productivity, workflow khác có bị ảnh hưởng không?
4. Bắt buộc có metric quality, trust hoặc value — không chỉ đo usage và speed.
5. Có human-in-loop checkpoint và override rate — AI sai thì ai xử lý, override bao nhiêu là bình thường?
```

---

## Tự kiểm tra

- [x] Không chỉ kể chuyện case.
- [x] Có nêu metric cụ thể.
- [x] Có nói metric chứng minh được gì và chưa chứng minh được gì.
- [x] Có ít nhất 1 bài học áp dụng vào dashboard nhóm.