# Thin SPEC — AI Trip Planner · Vinpearl / VinWonders

> Thin SPEC không phải PRD đầy đủ. Đây là bản cam kết đủ rõ để sáng Day 06 nhóm build ngay.

---

## 1. Track, product/app và user

**Track:** B · Travel & Hospitality
**Product/app thật:** Vinpearl Resort & Golf / VinWonders (Sun World là analog tham khảo)
**User cụ thể:** Khách lần đầu đến khu nghỉ dưỡng Vinpearl hoặc VinWonders (2-5 người, có thể có trẻ em), đang ở bước lập kế hoạch trước khi đặt — chưa biết lịch trình nào phù hợp và không rõ tổng chi phí thực tế.
**Nhóm có phải user thật không?** Một phần — sinh viên chưa có gia đình riêng, ngân sách khác, nhưng đã từng đi hoặc biết người đã đi. Khác ở chỗ: user thật thường lo ngân sách gia đình và phù hợp với trẻ em / người lớn tuổi hơn.

---

## 2. Evidence summary

| Evidence | Nguồn | User/pain nói lên điều gì? | SPEC phải đổi gì? |
|---|---|---|---|
| Web Vinpearl không có bộ lọc theo số người / ngân sách / ưu tiên | Self-use (cần chụp screenshot) | User phải đọc từng gói, không có gợi ý tổng hợp | Build slice phải bao gồm bước hỏi input có cấu trúc |
| User không biết tổng chi phí thực tế trước khi đặt | Self-use + review (cần xác nhận) | Pain là ra quyết định thiếu thông tin, không chỉ "không biết có gì" | Output phải là cost estimate rõ, không chỉ danh sách hoạt động |
| _(Review thật từ App Store / group du lịch — nhóm bổ sung trước M1)_ | _(nguồn)_ | _(insight)_ | _(thay đổi)_ |

---

## 3. Pain statement

```text
Khách lần đầu đến Vinpearl / VinWonders (đặc biệt gia đình 2-5 người)
đang gặp khó ở bước lập kế hoạch trước khi đặt,
vì không có công cụ tổng hợp lịch trình + ước tính chi phí theo điều kiện cụ thể của họ
(số người, ngày đi, ngân sách, ưu tiên hoạt động),
dẫn tới: mất thời gian tìm kiếm, không chắc có phù hợp không, dễ bị surprise về chi phí sau khi đặt.
Bằng chứng chính là: (1) web/app thiếu bộ lọc cá nhân hóa, (2) review phàn nàn chi phí phát sinh
[nhóm bổ sung quote thật trước M1].
```

---

## 4. Build slice

```text
Cho khách đang lập kế hoạch chuyến đi Vinpearl / VinWonders (chưa đặt),
prototype sẽ dùng AI để augment bước planning:
— Hỏi 4-5 input: số người lớn / trẻ em, số ngày, điểm đến (Phú Quốc / Nha Trang / Đà Nẵng),
  ngân sách tổng dự kiến, ưu tiên (thiên nhiên / vui chơi / nghỉ dưỡng / ẩm thực).
— AI tổng hợp → gợi ý 2-3 lịch trình theo ngày + cost estimate breakdown (vé vào, phòng ước tính, ăn uống).
— User xem, chỉnh, hoặc hỏi thêm.

Output: 2-3 lịch trình dạng ngày-theo-ngày + bảng ước tính chi phí.
Failure mode xử lý: nếu ngân sách nhập vào thấp hơn thực tế tối thiểu,
AI cảnh báo và hỏi lại thay vì trả output không khả thi.
```

---

## 5. Auto/Aug decision

- [x] **Augmentation:** AI gợi ý / draft lịch trình + cost estimate, user quyết định cuối (chỉnh, chọn, đặt thật thì ra ngoài scope).
- [ ] Conditional automation
- [ ] Automation

**Lý do chọn Augmentation:**
Quyết định đặt tour / nghỉ dưỡng liên quan đến tiền và kỳ vọng gia đình — sai khó undo. User cần xem và duyệt trước khi cam kết. Augmentation giúp thu dữ liệu correction thật (user chỉnh gợi ý gì) để cải thiện sau.

**Human role:** Decider — user xem gợi ý, tự điều chỉnh và quyết định có đặt không.

---

## 6. Four paths

| Path | Prototype phải thể hiện gì? |
|---|---|
| **Happy** | User nhập đủ input hợp lệ → AI trả 2-3 lịch trình rõ ràng + cost estimate breakdown → user đọc được, có thể hỏi thêm |
| **Low-confidence** | Input mơ hồ ("muốn vui", không có ngân sách, số người chưa chắc) → AI hỏi lại 1-2 câu làm rõ thay vì tự đoán |
| **Failure** | Ngân sách nhập quá thấp so với thực tế tối thiểu → AI cảnh báo rõ ("ngân sách X thấp hơn mức tối thiểu Y, bạn muốn điều chỉnh không?") thay vì trả kết quả không khả thi |
| **Correction** | User nói "tôi không muốn hoạt động nước" hoặc "thêm 1 ngày" → AI cập nhật lịch trình theo yêu cầu, không bắt nhập lại từ đầu |

---

## 7. Failure mode nguy hiểm nhất

```text
Nếu user nhập ngân sách thấp hơn chi phí thực tế tối thiểu (ví dụ: 2 người 2 ngày, ngân sách 2 triệu),
AI có thể trả lịch trình trông hợp lý nhưng không khả thi trên thực tế,
hậu quả là user lên kế hoạch sai, đến nơi mới biết thiếu tiền — mất tin tưởng vào app.

Prototype sẽ xử lý bằng:
— So sánh ngân sách nhập với cost floor ước tính (hardcode hoặc AI estimate).
— Nếu dưới ngưỡng: hiện cảnh báo rõ + hỏi lại ("Với X người, Y ngày tại Z,
  chi phí tối thiểu ước tính là [số], bạn muốn điều chỉnh ngân sách hoặc rút ngắn chuyến đi?").
— Không trả lịch trình giả nếu không khả thi.

Owner kiểm thử path này là: [tên thành viên phụ trách test].
```

---

## 8. Owner plan cho sáng Day 06

| Thành viên | Việc phụ trách | Bằng chứng cần có trong repo |
|---|---|---|
| Phan Võ Trọng Tiển| Research / evidence: đọc 20-30 review App Store + vào 1-2 group du lịch, lấy 3-5 quote thật | `evidence-pack.md` có quote + nguồn điền đầy đủ |
| Võ Tấn Trung | SPEC: cập nhật thin SPEC sau khi có evidence thật, đặc biệt pain statement và failure mode | `spec-final.md` |
| Đào Văn Tuân | Prototype: build flow input → AI → output (có thể dùng Claude API / ChatGPT API + simple UI) | `prototype-readme.md` + link demo hoặc video |
| Nguyễn Bá Thành | Test / failure path: kiểm thử ít nhất 3 case (happy, low-budget, mơ hồ), ghi log kết quả | `prompt-tests-or-failure-log.md` |