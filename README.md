# Day 06 — AI Trip Planner SPEC

Repo này là phần nộp cá nhân cho bài Day 06, tập trung vào việc chuẩn bị SPEC và evidence để build prototype AI Product trong track **B · Travel & Hospitality**.

Ý tưởng nhóm đang chốt là **AI Trip Planner cho Vinpearl / VinWonders**: AI hỗ trợ khách đang lập kế hoạch chuyến đi bằng cách hỏi thông tin đầu vào, gợi ý 2-3 lịch trình phù hợp và ước tính chi phí trước khi user quyết định đặt thật.

---

## Tổng quan dự án

| Mục | Nội dung |
|---|---|
| Nhóm | 4AE |
| Track | B · Travel & Hospitality |
| Product/app chính | Vinpearl Resort & Golf / VinWonders |
| Analog tham khảo | Sun World, Airbnb, Klook, GetYourGuide, Google Travel |
| User chính | Khách lần đầu đến Vinpearl / VinWonders, thường đi nhóm 2-5 người hoặc gia đình có trẻ em |
| Workflow tập trung | Lập kế hoạch trước khi đặt |
| Pain chính | Không biết lịch trình nào phù hợp và tổng chi phí thực tế là bao nhiêu |
| Hướng AI | Augmentation: AI gợi ý, user xem/chỉnh/quyết định cuối |

---

## Cấu trúc repo

```text
Day06-2A202600642-V-T-nTrung/
├── 01-invidual-workshop/
│   └── app-teardown.md
├── 02-group-spec/
│   ├── evidence-pack-template.md
│   ├── synthesis-decide-toolkit.md
│   └── thin-spec-template.md
└── README.md
```

| Folder / File | Vai trò |
|---|---|
| `01-invidual-workshop/app-teardown.md` | Bài làm cá nhân: mổ một app/workflow AI thật, tìm điểm yếu và rút ra quyết định product |
| `02-group-spec/evidence-pack-template.md` | Gom evidence từ self-use, review/social source và competitor analog |
| `02-group-spec/synthesis-decide-toolkit.md` | Tổng hợp evidence thành insight, opportunity và quyết định build slice |
| `02-group-spec/thin-spec-template.md` | Thin SPEC cho prototype AI Trip Planner, gồm user, pain, build slice, paths, failure mode và owner plan |

---

## Nội dung chính trong `02-group-spec`

Thứ tự đọc khuyến nghị:

1. `evidence-pack-template.md`
2. `synthesis-decide-toolkit.md`
3. `thin-spec-template.md`

Ba file này đi theo cùng một mạch:

- Bắt đầu từ evidence: web/app thiếu bộ lọc cá nhân hóa theo số người, ngày đi, ngân sách và ưu tiên.
- Chuyển thành insight: user không chỉ thiếu danh sách hoạt động, mà thiếu cơ sở để ra quyết định an toàn về lịch trình và chi phí.
- Chốt opportunity: dùng AI để augment bước lập kế hoạch trước khi đặt.
- Thu hẹp build slice: chỉ demo flow input → AI gợi ý → lịch trình + cost estimate, không làm booking thật.

---

## SPEC đang chốt

Prototype tập trung vào một flow hẹp:

```text
User nhập thông tin chuyến đi
→ AI tổng hợp nhu cầu
→ AI trả 2-3 lịch trình theo ngày
→ AI hiển thị ước tính chi phí breakdown
→ User xem, chỉnh hoặc hỏi thêm
```

Input chính:

- Số người lớn / trẻ em
- Số ngày đi
- Điểm đến: Phú Quốc / Nha Trang / Đà Nẵng
- Ngân sách tổng dự kiến
- Ưu tiên hoạt động: thiên nhiên, vui chơi, nghỉ dưỡng, ẩm thực

Output cần có:

- 2-3 lịch trình dạng ngày-theo-ngày
- Ước tính chi phí tổng
- Breakdown chi phí: vé vào, phòng ước tính, ăn uống
- Cảnh báo nếu ngân sách không khả thi

---

## Pain statement

Khách lần đầu đến Vinpearl / VinWonders, đặc biệt là gia đình hoặc nhóm 2-5 người, gặp khó ở bước lập kế hoạch trước khi đặt vì không có công cụ tổng hợp lịch trình và ước tính chi phí theo điều kiện cụ thể của họ.

Hệ quả:

- Mất thời gian đọc nhiều trang hoặc gói dịch vụ riêng lẻ.
- Không biết gói/lịch trình nào phù hợp với nhóm của mình.
- Không rõ tổng chi phí thực tế trước khi cam kết.
- Dễ gặp chi phí phát sinh hoặc kỳ vọng sai sau khi đặt.

---

## Auto/Aug decision

Nhóm chọn **Augmentation**.

AI chỉ đóng vai trò gợi ý lịch trình và ước tính chi phí. User vẫn là người xem, chỉnh, chọn và quyết định cuối cùng. Đây là lựa chọn phù hợp vì quyết định du lịch/nghỉ dưỡng liên quan đến tiền, thời gian và kỳ vọng của cả nhóm hoặc gia đình.

Booking thật nằm ngoài scope Day 06.

---

## Four paths cần test

| Path | Prototype cần thể hiện |
|---|---|
| Happy | User nhập đủ input hợp lệ, AI trả 2-3 lịch trình rõ ràng kèm cost estimate |
| Low-confidence | Input mơ hồ hoặc thiếu dữ liệu, AI hỏi lại 1-2 câu thay vì tự đoán |
| Failure | Ngân sách quá thấp, AI cảnh báo và không tạo lịch trình giả |
| Correction | User muốn chỉnh lịch trình, AI cập nhật theo yêu cầu mà không bắt nhập lại từ đầu |

Failure mode nguy hiểm nhất: AI trả lịch trình trông hợp lý nhưng không khả thi về chi phí. Prototype cần có cost floor hoặc ngưỡng tối thiểu để cảnh báo khi ngân sách thấp hơn thực tế dự kiến.

---

## Phân công hiện tại

| Thành viên | Phụ trách | Artifact cần có |
|---|---|---|
| Phan Võ Trọng Tiển | Research / evidence: đọc review, lấy quote thật, ghi nguồn | `evidence-pack.md` |
| Võ Tấn Trung | SPEC final: cập nhật pain statement, build slice, failure mode | `spec-final.md` |
| Đào Văn Tuân | Prototype: build flow input → AI → output | `prototype-readme.md` và link demo/video |
| Nguyễn Bá Thành | Test: happy, low-budget, input mơ hồ | `prompt-tests-or-failure-log.md` |

---

## Checklist cần bổ sung

- [ ] Chụp screenshot self-use thật trên web/app Vinpearl, VinWonders hoặc Sun World.
- [ ] Thử ít nhất 3 query thật liên quan đến lịch trình, combo, ngân sách hoặc chi phí gia đình.
- [ ] Đọc 20-30 review App Store / Play Store / Google Maps / group du lịch.
- [ ] Bổ sung 3-5 quote thật vào evidence pack.
- [ ] Điền nguồn, user type và pain/failure mode cho từng quote.
- [ ] Cập nhật thin SPEC thành bản final sau khi evidence thật đã được thêm.
- [ ] Ghi rõ owner kiểm thử failure path.

---

## Scope không build trong Day 06

- Booking thật: đặt phòng, vé, tour.
- Cá nhân hóa theo lịch sử chuyến đi.
- So sánh nhiều điểm đến hoặc nhiều brand cùng lúc.
- Gợi ý nhà hàng chi tiết trong khu.
- Multi-language support.
