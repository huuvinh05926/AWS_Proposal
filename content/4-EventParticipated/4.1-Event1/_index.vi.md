---
title: "Event 1"
date: "2025-10-03"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# 03/10/2025

# AWS GenAI Builder

**Diễn giả:** Toàn Huỳnh - Senior Specialist Solutions Architect

## AI-Driven Development Lifecycle (AI-DLC)

### Giới thiệu về AI-DLC

- AI-DLC không chỉ là một công cụ đơn thuần
- Sự phát triển của AI trong phát triển phần mềm:
  - **2023:** Hỗ trợ developer viết code nhanh hơn
  - **2024:** Tạo ra các đoạn code lớn hơn và trả lời nhanh hơn
  - **2025:** Hoàn thành các task phát triển end-to-end với human in the loop
- AI phải được sử dụng theo mô hình pair-programming thay vì làm việc đơn lẻ
- Developer vẫn là người kiểm tra, validate và là owner của code

### AI Disruption to Development

**Những thách thức khi sử dụng AI:**

- Cần hiểu rõ lý do tại sao cần AI
- AI đang trở thành công cụ không thể thiếu trong phát triển phần mềm
- Vấn đề chất lượng phần mềm vẫn do developer kiểm tra và đảm bảo
- Khi dùng AI để scale dự án lớn có thể gặp nhiều vấn đề:
  - Sinh ra nhiều code nhưng không kiểm soát được chất lượng
  - Có thể phải làm lại từ đầu nếu không kiểm soát tốt
  - Khó theo dõi những gì AI đang làm
- Không nên "single-shot" cho tất cả các trường hợp
- Khi xem AI là bạn đồng hành cùng giải quyết vấn đề, đa số vấn đề sẽ được giải quyết tốt hơn

### Cách làm việc với AI-DLC

**Nguyên tắc quan trọng:**

- Developer phải là người đưa ra quyết định cuối cùng, không để AI tự quyết định
- Developer cần tổng hợp thông tin, lên ý tưởng và trao đổi với AI
- AI sẽ giúp define tasks, tránh mất kiểm soát
- Phải cung cấp đủ thông tin và ý tưởng cho AI
- Phát triển dựa trên phân tích và hiểu vấn đề với sự hỗ trợ của AI

**Quy trình làm việc:**

![How does AI-DLC work?](/images/4-EventParticipated/BC23F17A-C590-4D04-9560-B9CBF09A0B87.jpeg)

![AI-Driven Development Lifecycle](/images/4-EventParticipated/0B608674-73F3-4495-A0F4-4DD70F17C3B8.jpeg)

**Các bước thực hiện:**

1. Đưa vấn đề vào AI để generate user stories
2. Scope down và đặt câu hỏi về app muốn làm
3. Nhờ AI group những unit quan trọng cho end user
4. Implement từng unit, chia nhỏ thành các project nhỏ

### Mob Elaboration & Construction

**Mob Elaboration:** Nhiều người làm chung trên một máy tính và chia sẻ output với nhau

![Construction: Mob Construction](/images/4-EventParticipated/C96E172C-D36A-451B-A402-8EB2DF5B8486.jpeg)

**Lưu ý:** Đi từ một yêu cầu đơn giản qua từng unit và đi tới kết quả cuối cùng. Nếu Backend và Frontend muốn làm việc chung theo mô hình này thì cần có ít nhất một track chung để tương tác với nhau.

### Workflow with AI

**Standard Development Workflow:**

![AI-DLC Standard Development Workflow](/images/4-EventParticipated/67A368F8-5389-4E7E-AFE1-329DEE2B1255.jpeg)

- Hiện tại chúng ta dùng AI để compile code
- Mô hình này không thể chia nhỏ ra, nên với dự án lớn nên dùng Amazon Q

**Prompt Template:**

![Prompt Template](/images/4-EventParticipated/96F29C72-912C-4427-9774-F1381D6A8FA4.jpeg)

**Cách viết prompt hiệu quả:**

- Phải chỉ rõ AI làm gì, Product Manager làm gì
- Phải chỉ ra được role để giải quyết vấn đề
- Khi muốn làm dự án, yêu cầu AI plan ra trước
- Có thể chia ra nhiều options và làm từ từ để tránh quá tải

**Best Practices:**

- Lưu trữ kết quả trên file Markdown và dựa vào đó để làm những việc tiếp theo
- Phải compile lại nhiều lần, upload lên MD và define rõ ràng
- Đưa file MD vào project để AI có thể đọc và thêm ý tưởng
- Có các dấu check trong file plan để note lại những thứ đã làm

![Each Stage](/images/4-EventParticipated/C651E529-5F58-47C4-8FF8-1A068DAAB023.jpeg)

![Key Workflow Features](/images/4-EventParticipated/A432E852-C014-4130-B437-9BEE50B1296C.jpeg)

![Steps in AI-DLC](/images/4-EventParticipated/4A1C23B0-123E-47AB-A5AE-A71CBE94A764.jpeg)

### Nguyên tắc quan trọng

**Never Single-shot a Multi-step Problem:**

![Never Single-shot](/images/4-EventParticipated/2B3CD950-C4EF-4601-B9C7-3B69F28F104E.jpeg)

- Tận dụng AI cho những công việc chuẩn chỉnh
- Những công việc cần suy nghĩ thì tự làm
- Phải review thường xuyên, không giao nhiệm vụ hoàn toàn cho AI

**Maximize Semantics per Token:**

![Maximize Semantics per Token](/images/4-EventParticipated/6CAE446D-4245-4D9D-9807-D12D4FDD74F9.jpeg)

- Code dễ over context, nên phải build thành Markdown file để tránh tỉ lệ đi sai

![Code Ownership](/images/4-EventParticipated/BA4CF1EE-98AA-466F-B3F7-C8E87EF7E32C.jpeg)

**Kết luận:** Bạn vẫn là người chịu trách nhiệm về code cuối cùng.

---

## Kiro - The AI IDE for Prototype to Production

**Diễn giả:** My Nguyễn - Senior Prototyping Architect

### Giới thiệu về Kiro

Kiro là một AI IDE được thiết kế đặc biệt để chuyển đổi từ prototype sang production một cách nhanh chóng và hiệu quả.

**Sự khác biệt giữa Kiro và VSCode:**

![Kiro vs VSCode](/images/4-EventParticipated/48757C46-B986-4A99-9CC1-B4048BB2E690.jpeg)

### Các tính năng chính

**Power, Flexibility, and Security:**

Kiro cung cấp sự kết hợp mạnh mẽ giữa:

- **Power:** Khả năng xử lý mạnh mẽ với sự hỗ trợ của AI
- **Flexibility:** Linh hoạt trong việc phát triển từ prototype đến production
- **Security:** Đảm bảo an toàn và bảo mật trong quá trình phát triển

---

## Kết quả và Giá trị đạt được

### Kiến thức thu được:

- Hiểu rõ về **AI-Driven Development Lifecycle (AI-DLC)** và cách áp dụng AI như một bạn đồng hành trong phát triển phần mềm
- Nắm vững kỹ thuật **Prompt Engineering** để tương tác hiệu quả với AI models
- Học được phương pháp **Mob Construction** để làm việc nhóm với AI
- Biết cách sử dụng Markdown files để quản lý project planning và AI context
- Làm quen với **Kiro IDE** - công cụ chuyển đổi từ prototype sang production

### Kỹ năng phát triển:

- Kỹ năng viết prompt hiệu quả và cấu trúc hóa yêu cầu cho AI
- Khả năng chia nhỏ dự án lớn thành các units có thể quản lý được
- Hiểu được nguyên tắc "Never Single-shot a Multi-step Problem"
- Biết cách review và validate code được AI tạo ra
- Nâng cao kỹ năng làm việc nhóm trong môi trường AI-assisted development

### Bài học quan trọng:

- Developer vẫn phải là người đưa ra quyết định cuối cùng và chịu trách nhiệm về code
- AI là công cụ hỗ trợ mạnh mẽ nhưng không thay thế được tư duy và kinh nghiệm của developer
- Cần có quy trình rõ ràng khi làm việc với AI để tránh mất kiểm soát chất lượng
- Collaboration và communication là yếu tố quan trọng trong AI-DLC
