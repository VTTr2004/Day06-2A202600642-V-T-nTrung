# Workshop — Mổ App AI Thật

- Họ và tên: Võ Tấn Trung.
- MSSV: 2A202600642.

## Case Study:  — Moni

## 1. Product được chọn

* Product: MoMo — Moni
* AI Feature: chatbot/trợ lý tài chính
* Task thử nghiệm: hỏi khả năng của AI assistant

---

# 2. Promise vs Reality

## User Input

```text id="h6m5s0"
"bạn có khả năng gì"
```

## Observed Behavior

Moni không trả lời được mà bắt đầu trả lời theo form mặc định:

```text id="9mz9a7"
"Tôi là chatbot chỉ có khả năng trả lời trong phạm vi ..."
```

Muốn bot trả lời được thì phải ghi đúng Moni có khả năng gì.

## User Expectation

Vì Moni được giới thiệu như AI assistant nên user kỳ vọng:

* có thể hỏi tự nhiên,
* bot hiểu mình đang hỏi về capability của chính nó.

## Actual Experience

* Bot không hiểu câu trên đang nói với Moni.
* User phải tự đổi cách hỏi để đúng keyword/capability mà bot hỗ trợ.
* Cảm giác giống chatbot FAQ cứng hơn là AI assistant.

## Emotional Reaction

```text id="zx3u1r"
"Cảm giác đang code với một con bot khô khan, mất hứng."
```

Sau đó user mất hứng và bỏ luôn.

---

# 3. Four Paths

| Path           | Observation                                                                  |
| -------------- | ---------------------------------------------------------------------------- |
| Happy          | Nếu user ghi đúng capability Moni hỗ trợ thì bot trả lời được.               |
| Low-confidence | Không có hỏi lại hoặc gợi ý user nên hỏi gì.                                 |
| Failure        | User hỏi tự nhiên: "bạn có khả năng gì" → bot fallback sang form mặc định.   |
| Correction     | User phải tự học cách phrasing đúng với bot. Không có recovery flow rõ ràng. |

---

# 4. Finding → Product Decision

## Finding

Khi user hỏi:

```text id="w3a5ic"
"bạn có khả năng gì"
```

AI không hiểu đây là câu hỏi capability discovery, mà fallback sang form mặc định giới hạn phạm vi.

Hậu quả là:

* user cảm giác AI bị giả,
* conversation bị khô,
* mất hứng tiếp tục dùng.

Lỗi thuộc layer:

* Intent Understanding
* Persona / Promise mismatch
* UX Recovery

## Product Decision

Nên thêm low-confidence path cho các câu capability discovery như:

* "bạn có khả năng gì"
* "bạn giúp được gì"
* "mình nên hỏi gì"

Thay vì fallback cứng, bot nên:

* trả lời tự nhiên hơn,
* gợi ý 3–5 việc Moni làm được,
* hoặc show quick actions để user tiếp tục conversation.

---

# 5. Sketch — As-is / To-be

## AS-IS

```text id="6n3n4m"
User:
"bạn có khả năng gì"

        ↓

Moni:
"Tôi là chatbot chỉ có khả năng..."

        ↓

User:
mất hứng / confused

        ↓

Thoát conversation
```

### Điểm gãy

* Không hiểu intent discovery
* Response quá cứng
* Không có recovery path

---

## TO-BE

```text id="z8s4tl"
User:
"bạn có khả năng gì"

        ↓

AI detect:
user đang hỏi capability

        ↓

Moni:
"Mình có thể giúp:
- xem chi tiêu,
- tìm giao dịch,
- nhắc thanh toán,
- gợi ý tiết kiệm"

[Quick actions]
- "Chi tiêu tháng này"
- "Tôi tiêu nhiều nhất vào gì?"
- "Gợi ý tiết kiệm"

        ↓

Conversation tiếp tục
```

---

# 6. SPEC Impact

* [x] Có ít nhất 1 screenshot hoặc observation cụ thể.
* [x] Có đủ 4 paths hoặc nói rõ path nào chưa có trong product.
* [x] Finding được viết thành product decision, không chỉ là nhận xét.
* [x] Sketch có as-is và to-be.
* [x] Finding này sẽ thay đổi fallback response, low-confidence handling và onboarding flow trong SPEC của Moni.