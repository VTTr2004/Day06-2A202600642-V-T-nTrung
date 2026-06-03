# Synthesis & Decide — Travel & Hospitality

Dùng sau khi nhóm đã có evidence. Mục tiêu: chốt build slice đủ nhỏ cho Day 06.

---

## 1. Cụm evidence (gom theo pain/workflow)

| Cụm pain | Evidence (dự kiến / cần xác nhận) |
|---|---|
| **Không biết chi phí thực tế** | User đọc gói riêng lẻ, không tổng hợp được; review phàn nàn "đặt xong mới biết có chi phí phát sinh" |
| **Không biết gói nào phù hợp với nhóm của mình** | Không có bộ lọc theo số người / độ tuổi / nhu cầu tiện ích |
| **Lười/mất thời gian tìm kiếm và tổng hợp** | Phải xem nhiều trang, nhiều tab, không có chỗ so sánh nhanh |
| **Không chắc chắn trước khi cam kết đặt** | Thiếu "preview" lịch trình + chi phí tổng trước khi checkout |

> **Action cho nhóm:** Xác nhận từng cụm này bằng ít nhất 1 quote/screenshot thật trước M1 Day 06.

---

## 2. Insight

```text
User lần đầu đến Vinpearl / Sun World (hoặc gia đình đi cùng nhau)
không chỉ cần danh sách hoạt động / gói dịch vụ.

Họ thật ra cần hỗ trợ ra quyết định có cơ sở về tài chính và lịch trình,
vì họ không có công cụ tổng hợp nhanh "với điều kiện X của tôi thì đi thế nào, tốn bao nhiêu".
```

---

## 3. Opportunity

```text
Cơ hội là dùng AI để augment bước lập kế hoạch trước đặt:
hỏi 4-5 câu đầu vào có cấu trúc (số người, ngày, ngân sách, ưu tiên),
tổng hợp 2-3 lịch trình gợi ý kèm cost estimate breakdown,
giúp user tự tin hơn khi quyết định đặt — hoặc biết rõ cần điều chỉnh gì —
trong khi vẫn kiểm soát được failure: nếu input mơ hồ hoặc ngân sách không khả thi,
AI hỏi lại thay vì trả output sai.
```

---

## 4. Build slice — qua 5 câu hỏi kiểm tra

| Câu hỏi | Đánh giá |
|---|---|
| User cụ thể chưa? | ✅ Khách đến Vinpearl / VinWonders lần đầu, hoặc gia đình có trẻ em / người lớn tuổi, đang ở bước lập kế hoạch trước khi đặt |
| Task đủ hẹp chưa? | ✅ Chỉ làm bước: input (số người, ngày, ngân sách, ưu tiên) → AI tổng hợp → output 2-3 lịch trình + cost estimate |
| AI decision rõ chưa? | ✅ AI tổng hợp và gợi ý lịch trình + ước tính chi phí; user duyệt và điều chỉnh |
| Failure path rõ chưa? | ✅ Case: user nhập ngân sách quá thấp so với thực tế, hoặc input mơ hồ ("muốn vui") — AI hỏi lại thay vì bịa output |
| Có evidence không? | ⚠️ Cần bổ sung review thật trước M1 |

---

## 5. Quyết định: giữ, giảm scope, hay đổi hướng?

| Tình huống | Quyết định |
|---|---|
| Ý tưởng quá rộng | ✅ **Giữ domain, cắt xuống một flow** — chỉ làm bước "plan trước khi đặt", không làm booking thật |
| AI không cần thiết | ❌ AI cần thiết — tổng hợp nhiều biến (người, ngày, ngân sách, địa điểm) thành gợi ý cá nhân hóa là task AI fit |
| Không demo được trong 1 ngày | ✅ Flow này demo được: form input → API call → hiển thị 2-3 lịch trình + cost |

---

## 6. Câu chốt cuối

```text
Dựa trên evidence (user không có công cụ tổng hợp lịch trình + chi phí theo điều kiện cụ thể),
nhóm sẽ build prototype "AI Trip Planner" cho Vinpearl / VinWonders,
cho khách đang lập kế hoạch trước khi đặt (1-2 ngày, 2-5 người),
để giải quyết pain: không biết lịch trình nào phù hợp và tổng chi phí thực tế là bao nhiêu,
bằng cách AI hỏi 4-5 input → augment: gợi ý 2-3 lịch trình + cost estimate breakdown,
và sẽ test failure path: user nhập ngân sách thấp hơn thực tế hoặc input mơ hồ.
```

---

## 7. Backlog (không build trong Day 06)

- Tích hợp booking thật (đặt phòng / vé)
- Cá nhân hóa theo lịch sử chuyến đi trước
- So sánh nhiều điểm đến (Vinpearl vs Sun World vs cả hai)
- Gợi ý nhà hàng / ăn uống trong khu
- Multi-language support
