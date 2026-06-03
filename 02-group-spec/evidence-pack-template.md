# Evidence Pack — Nhóm Travel & Hospitality

Nộp kèm thin SPEC cuối Day 05.

## 1. Nhóm và track

**Tên nhóm:** 4AE
**Track:** B · Travel & Hospitality
**Product/app đã chọn:** Vinpearl + Sun World / SunGroup
**Build slice đang nghĩ:** AI gợi ý lịch trình + ước tính chi phí cá nhân hóa theo số người, ngày đi, nhu cầu tiện ích

---

## 2. Self-use evidence

Nhóm tự dùng app/workflow và ghi lại điểm gãy.

| Observation | Screenshot/link | Path liên quan | Điều học được |
|---|---|---|---|
| Vào web Vinpearl, không có chỗ nhập "tôi đi 2 người lớn + 1 trẻ em, 2 ngày, ngân sách X" để lấy gợi ý phù hợp | _(chụp màn hình trang chủ/trang gói dịch vụ)_ | Failure | User phải tự đọc từng gói, không có bộ lọc theo nhu cầu cụ thể |
| Thử tìm "combo gia đình 2 ngày Vinpearl Nha Trang giá bao nhiêu" — kết quả trả về danh sách gói riêng lẻ, không tổng hợp được chi phí thực tế | _(screenshot trang kết quả tìm kiếm)_ | Low-confidence | User không biết tổng chi phí thực tế là bao nhiêu cho cả chuyến |
| _(Thêm observation của nhóm sau khi self-use thật)_ | | Happy / Low-confidence / Failure / Correction | |

> **Lưu ý:** Nhóm cần thực sự mở app/web Vinpearl và Sun World, thử ít nhất 3 query thật, chụp ảnh điểm gãy cụ thể trước khi nộp.

---

## 3. User / review / social evidence

| Quote / review / observation | Nguồn | User là ai? | Pain/failure mode |
|---|---|---|---|
| _(Ví dụ: "Đặt combo xong mới phát hiện không bao gồm vé tàu/cáp treo, phải mua thêm rất nhiều")_ | App Store review / Google Maps / group du lịch | Gia đình đi lần đầu | Chi phí thực tế cao hơn dự kiến, cảm giác bị lừa |
| _(Ví dụ: "Không biết trẻ bao nhiêu tuổi thì được miễn vé, hỏi chatbot không ra")_ | Review Play Store / Facebook group | Phụ huynh có con nhỏ | Thiếu thông tin chính sách giá rõ ràng theo độ tuổi |
| _(Thêm review thật từ App Store / Play Store / group du lịch VN)_ | | | |

```text
Phần này là GIẢ ĐỊNH minh họa. Nhóm sẽ kiểm bằng cách:
- Đọc 20-30 review App Store/Play Store của app Vinpearl / VinWonders
- Vào group "Du lịch Phú Quốc / Nha Trang / Đà Nẵng" tìm complaint liên quan đến lịch trình và chi phí
- Hỏi nhanh 1-2 người đã từng đi Vinpearl hoặc Sun World
Trước checkpoint M1 Day 06.
```

---

## 4. Competitor / analog evidence

| App / mô hình tham khảo | Họ xử lý task này thế nào? | Pattern học được | Có áp dụng trong 1 ngày không? |
|---|---|---|---|
| Airbnb | Bộ lọc: số người, ngày, loại không gian, tiện ích; hiện giá ngay khi chọn | Filtering theo nhu cầu + hiển thị giá realtime | Có — chỉ lấy pattern hỏi input + gợi ý kết quả |
| Klook / GetYourGuide | Gợi ý combo tour theo số người, thời gian, loại hoạt động; hiện tổng giá trước khi đặt | Transparency về chi phí tổng + breakdown | Có — pattern "estimate before commit" |
| Google Travel | AI tóm tắt lịch trình gợi ý cho điểm đến cụ thể | AI augment: gợi ý, user tự điều chỉnh | Có — đây đúng là mô hình Augmentation |

---

## 5. Evidence → Insight

```text
Evidence nổi bật nhất:
User đến Vinpearl / Sun World thường không biết trước tổng chi phí thực tế,
và không có công cụ nào hỏi rõ nhu cầu (số người, ngày đi, ưu tiên tiện ích)
để lọc và tổng hợp gợi ý phù hợp.

Insight:
User không chỉ gặp vấn đề "không biết chọn gói nào".
Thật ra họ cần được hỗ trợ ra quyết định an toàn về tài chính và lịch trình
trước khi cam kết đặt — đặc biệt với gia đình hoặc nhóm đông người.

Opportunity:
AI có thể giúp bằng cách hỏi 3-5 câu đầu vào (số người, ngày, ngân sách, ưu tiên),
sau đó augment: tổng hợp 2-3 lịch trình gợi ý kèm ước tính chi phí breakdown,
để user duyệt và chỉnh trước khi đặt chính thức.
```

---

## 6. Evidence đổi SPEC như thế nào?

- [ ] Đổi user chính.
- [x] Đổi pain statement — từ "không biết chọn lịch trình" → "không biết chi phí thực tế và gói nào phù hợp với điều kiện cụ thể của mình".
- [x] Đổi build slice — thu hẹp từ "gợi ý lịch trình" → "hỏi input → gợi ý 2-3 option kèm cost estimate".
- [x] Đổi Auto/Aug decision — xác nhận Augmentation là đúng.
- [ ] Đổi 4 paths.
- [ ] Đổi failure mode.
- [ ] Đổi owner/test plan.

```text
Trước evidence, nhóm định: build AI gợi ý lịch trình chung chung.
Sau evidence, nhóm đổi thành: AI hỏi input có cấu trúc (số người, ngày, ngân sách, ưu tiên)
→ trả về 2-3 lịch trình + ước tính chi phí tổng + breakdown.
Lý do: pain thật không phải "không biết có gì" mà là "không biết chi phí thực tế
và có phù hợp với điều kiện của mình không".
```
