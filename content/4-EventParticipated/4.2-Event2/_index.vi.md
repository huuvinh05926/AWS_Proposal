---
title: "Event 2"
date: "2025-11-15"
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# 15/11/2025

# Generative AI with Amazon Bedrock

## Thông tin diễn giả

- **Lam Tuan Kiet** - Sr. DevOps Engineer, FPT Software
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud Journey

## Bối cảnh và động lực chuyển đổi

Hiện nay, nhiều doanh nghiệp đang đối mặt với các nền tảng công nghệ đã lỗi thời. Việc đầu tư xây dựng nền tảng mới từ đầu thường đòi hỏi chi phí rất cao về cả tài chính và thời gian. Giải pháp tối ưu là tận dụng công nghệ cloud và các dịch vụ serverless để giảm thiểu chi phí vận hành và tăng tốc độ triển khai.

## Foundation Models - Nền tảng của Gen AI

![Why foundation models?](/images/4-EventParticipated/3C0E9B79-FBAE-426F-934F-F054076921AE.jpeg)

### Generative AI là gì?

Generative AI (Gen AI) là công nghệ cho phép tạo ra nội dung mới như văn bản, hình ảnh, âm thanh dựa trên các prompt (câu lệnh) đầu vào. Điểm đặc biệt của Gen AI là khả năng tạo ra nội dung có tính sáng tạo và phù hợp với ngữ cảnh.

### Foundation Models

Foundation Models là các mô hình AI được huấn luyện trên khối lượng dữ liệu khổng lồ và có khả năng:

- Xử lý đa dạng các tác vụ khác nhau
- Tổng quát hóa kiến thức từ dữ liệu huấn luyện
- Có thể fine-tune cho các ứng dụng cụ thể
- Tiết kiệm thời gian và chi phí phát triển

## Amazon Bedrock

Amazon Bedrock là dịch vụ được quản lý hoàn toàn (fully managed service) cung cấp quyền truy cập vào nhiều Foundation Models hàng đầu thông qua một API duy nhất.

![Supported foundation models in Amazon Bedrock](/images/4-EventParticipated/0D0458A0-B9F7-46CC-9405-C289F209CA7F.jpeg)

### Các Foundation Models được hỗ trợ

Amazon Bedrock hỗ trợ nhiều models từ các nhà cung cấp hàng đầu:

- **Claude** (Anthropic): Mạnh về reasoning và phân tích
- **Titan** (Amazon): Models tối ưu cho các use case AWS
- **Jurassic** (AI21 Labs): Tốt cho xử lý ngôn ngữ
- **Llama** (Meta): Open-source, linh hoạt tùy chỉnh
- **Stable Diffusion**: Chuyên về tạo hình ảnh

## Prompt Engineering

![What is a prompt?](/images/4-EventParticipated/0184C2FC-A3FE-4383-A620-1B308810C1F0.jpeg)

### Prompt là gì?

Prompt là câu lệnh hoặc đoạn text mà chúng ta cung cấp cho AI model để nhận được kết quả mong muốn. Chất lượng của prompt ảnh hưởng trực tiếp đến chất lượng đầu ra.

![What is Prompt Engineering? - An Example](/images/4-EventParticipated/4B30DA12-5B1E-4330-B990-A6053E5424CA.jpeg)

### Prompt Engineering

Prompt Engineering là nghệ thuật và khoa học thiết kế prompts hiệu quả để tối ưu hóa kết quả từ AI models. Đây là kỹ năng quan trọng khi làm việc với Generative AI.

## Các kỹ thuật Prompting

### 1. Zero-Shot Prompting

![Prompting Techniques - Zero-Shot Prompting](/images/4-EventParticipated/4A2925C5-03A2-49A8-BD4B-6537AD872D9E.jpeg)

**Zero-Shot Prompting** là kỹ thuật đưa ra câu hỏi hoặc yêu cầu trực tiếp mà không cung cấp ví dụ cụ thể. Model sẽ sử dụng kiến thức đã được huấn luyện để trả lời.

**Ưu điểm:**

- Đơn giản, nhanh chóng
- Phù hợp với các câu hỏi cơ bản

**Nhược điểm:**

- Kết quả có thể không chính xác với các tác vụ phức tạp

### 2. Few-Shot Prompting

![Prompting Techniques - Few-shot prompting](/images/4-EventParticipated/571A852C-ADD7-4037-9F07-AA48ED36816B.jpeg)

**Few-Shot Prompting** cung cấp một vài ví dụ minh họa trước khi đưa ra yêu cầu chính. Điều này giúp model hiểu rõ hơn format và context mong muốn.

**Ưu điểm:**

- Cải thiện độ chính xác đáng kể
- Model hiểu rõ hơn yêu cầu
- Phù hợp với các tác vụ cụ thể

**Nhược điểm:**

- Cần thời gian chuẩn bị ví dụ
- Tốn token (chi phí cao hơn)

### 3. Chain of Thought (CoT)

![Prompting Techniques - Chain of Thought (CoT)](/images/4-EventParticipated/D26171ED-FE57-457A-9288-A3267EEAD3F3.jpeg)

![Prompting Techniques - Chain of Thought (CoT)](/images/4-EventParticipated/16685DB4-D8E4-4074-8996-AA524CE40307.jpeg)

**Chain of Thought (CoT)** là kỹ thuật yêu cầu model giải thích từng bước suy nghĩ trước khi đưa ra câu trả lời cuối cùng.

**Ưu điểm:**

- Tăng độ chính xác cho các bài toán phức tạp
- Giúp debug và hiểu logic của model
- Phù hợp với các bài toán cần reasoning

**Cách sử dụng:**

- Thêm cụm từ "Let's think step by step" vào prompt
- Yêu cầu model giải thích từng bước
- Kiểm tra logic trước khi sử dụng kết quả

## Retrieval Augmented Generation (RAG)

![RAG in Action](/images/4-EventParticipated/54EF9821-5DB9-41DA-A5B3-0E585B9EFAA2.jpeg)

### RAG là gì?

**Retrieval Augmented Generation (RAG)** là kiến trúc kết hợp giữa:

1. **Retrieval**: Truy xuất thông tin từ nguồn dữ liệu nội bộ
2. **Generation**: Sử dụng AI model để tạo câu trả lời

### Quy trình hoạt động của RAG

1. **User Query**: Người dùng đưa ra câu hỏi
2. **Document Retrieval**: Hệ thống tìm kiếm thông tin liên quan trong knowledge base
3. **Context Building**: Kết hợp thông tin tìm được với prompt gốc
4. **Generation**: AI model tạo ra câu trả lời dựa trên context đầy đủ
5. **Response**: Trả về kết quả cho người dùng

### Lợi ích của RAG

- **Accuracy**: Tăng độ chính xác với dữ liệu nội bộ
- **Up-to-date**: Luôn sử dụng thông tin mới nhất
- **Cost-effective**: Không cần fine-tune model
- **Security**: Kiểm soát được nguồn dữ liệu

### Use cases phổ biến

- **Customer Support**: Chatbot trả lời dựa trên documentation
- **Internal Knowledge Base**: Hỗ trợ nhân viên tìm kiếm thông tin nội bộ
- **Document Analysis**: Phân tích và tóm tắt tài liệu

---

## Kết quả và Giá trị đạt được

### Kiến thức thu được:

- Hiểu sâu về **Amazon Bedrock** và các **Foundation Models** từ nhiều nhà cung cấp khác nhau (Claude, Titan, Llama, Stable Diffusion)
- Nắm vững các kỹ thuật **Prompt Engineering** cơ bản và nâng cao:
  - Zero-Shot Prompting: Đơn giản, nhanh chóng
  - Few-Shot Prompting: Cải thiện độ chính xác với ví dụ
  - Chain of Thought (CoT): Giải quyết bài toán phức tạp
- Hiểu rõ kiến trúc **RAG (Retrieval Augmented Generation)** và cách kết hợp AI với dữ liệu nội bộ
- Học được cách chọn model phù hợp cho từng use case cụ thể

### Kỹ năng phát triển:

- Kỹ năng thiết kế và tối ưu hóa prompts để đạt kết quả mong muốn
- Khả năng phân tích và lựa chọn kỹ thuật prompting phù hợp với bài toán
- Hiểu cách tính toán chi phí (tokens) khi sử dụng Gen AI
- Biết cách implement RAG architecture cho ứng dụng thực tế
- Nâng cao khả năng đánh giá chất lượng output từ AI models

### Bài học quan trọng:

- Gen AI không thay thế con người mà là công cụ augment khả năng của developer
- Chất lượng prompt quyết định chất lượng output
- Cần cân nhắc giữa độ chính xác và chi phí khi chọn kỹ thuật prompting
- RAG là giải pháp tối ưu để kết hợp sức mạnh của Gen AI với dữ liệu riêng của doanh nghiệp
- Bảo mật và kiểm soát dữ liệu rất quan trọng khi triển khai Gen AI

### Ứng dụng thực tế:

- Có thể áp dụng ngay vào các dự án cần chatbot hoặc document analysis
- Hiểu cách tích hợp Amazon Bedrock vào hệ thống hiện tại
- Biết cách xây dựng knowledge base và implement RAG pipeline

- Chatbot hỗ trợ khách hàng
- Hệ thống Q&A nội bộ doanh nghiệp
- Document search và summarization
- Knowledge management systems

## Các dịch vụ AI khác của AWS

### Amazon Rekognition

![Amazon Rekognition](/images/4-EventParticipated/9C0D5865-CD50-4C39-8C20-774DD59461EC.jpeg)

**Amazon Rekognition** là dịch vụ phân tích hình ảnh và video sử dụng machine learning.

**Tính năng chính:**

- **Face Detection & Recognition**: Nhận diện khuôn mặt
- **Object & Scene Detection**: Phát hiện đối tượng và cảnh
- **Celebrity Recognition**: Nhận dạng người nổi tiếng
- **Text in Image**: Trích xuất văn bản từ hình ảnh
- **Content Moderation**: Lọc nội dung không phù hợp

**Use cases:**

- Hệ thống xác thực bằng khuôn mặt
- Phân loại và tìm kiếm hình ảnh
- Video surveillance và security
- Media content analysis

### Amazon Comprehend

![Amazon Comprehend](/images/4-EventParticipated/AE51DEB2-ACBA-4230-AA3D-DB5BFD7DE9C0.jpeg)

**Amazon Comprehend** là dịch vụ Natural Language Processing (NLP) để phân tích văn bản.

**Tính năng chính:**

- **Sentiment Analysis**: Phân tích cảm xúc (positive, negative, neutral)
- **Entity Recognition**: Nhận dạng tên, địa điểm, tổ chức
- **Key Phrase Extraction**: Trích xuất cụm từ quan trọng
- **Language Detection**: Phát hiện ngôn ngữ
- **Topic Modeling**: Phân loại chủ đề

**Use cases:**

- Phân tích feedback khách hàng
- Social media monitoring
- Content categorization
- Document classification

## Key Takeaways

### Về Technology

1. **Amazon Bedrock** là giải pháp tối ưu để triển khai Gen AI với nhiều model lựa chọn
2. **Prompt Engineering** là kỹ năng quan trọng để tận dụng tối đa khả năng của AI
3. **RAG** giúp kết hợp sức mạnh của AI với dữ liệu nội bộ doanh nghiệp
4. AWS cung cấp ecosystem AI services đa dạng cho nhiều use cases khác nhau

### Về Implementation

1. **Bắt đầu đơn giản**: Sử dụng zero-shot prompting cho các tác vụ cơ bản
2. **Tối ưu dần**: Áp dụng few-shot hoặc CoT khi cần độ chính xác cao
3. **RAG cho dữ liệu riêng**: Không cần fine-tune model, tiết kiệm chi phí
4. **Kết hợp services**: Tận dụng nhiều dịch vụ AI của AWS cho giải pháp toàn diện

### Về Business Value

1. **Giảm chi phí**: Sử dụng managed services thay vì tự xây dựng infrastructure
2. **Tăng tốc độ**: Deploy nhanh với pre-trained models
3. **Scalability**: AWS tự động scale theo nhu cầu
4. **Security**: AWS đảm bảo bảo mật và compliance

## Trải nghiệm tại sự kiện

Tham gia workshop **"Generative AI with Amazon Bedrock"** là một trải nghiệm vô cùng bổ ích, giúp tôi hiểu sâu hơn về công nghệ Gen AI và cách áp dụng vào thực tế.

### Học hỏi từ các chuyên gia

- Các diễn giả có kinh nghiệm thực chiến đã chia sẻ những case studies cụ thể về triển khai Gen AI trong doanh nghiệp
- Được tìm hiểu chi tiết về các kỹ thuật Prompt Engineering và cách tối ưu hóa prompts
- Hiểu rõ hơn về kiến trúc RAG và cách implement trong các hệ thống thực tế

### Kiến thức kỹ thuật thu được

- Nắm vững các kỹ thuật prompting: Zero-shot, Few-shot, Chain of Thought
- Hiểu rõ workflow của RAG và cách kết hợp với knowledge base nội bộ
- Biết cách lựa chọn Foundation Model phù hợp cho từng use case
- Tìm hiểu về các dịch vụ AI khác của AWS: Rekognition, Comprehend

### Ứng dụng thực tế

Workshop đã cho tôi nhiều ý tưởng để áp dụng vào công việc:

- **Xây dựng chatbot**: Sử dụng RAG để tạo chatbot có kiến thức về sản phẩm/dịch vụ công ty
- **Document processing**: Tự động trích xuất và phân loại thông tin từ documents
- **Content generation**: Hỗ trợ tạo nội dung marketing, technical documentation
- **Customer insights**: Phân tích feedback và sentiment của khách hàng

### Networking

- Gặp gỡ và trao đổi với các professionals trong lĩnh vực AI/ML
- Chia sẻ kinh nghiệm và best practices với cộng đồng
- Tạo kết nối cho các cơ hội hợp tác trong tương lai

> Tổng kết, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn mở ra tầm nhìn về xu hướng AI và cách doanh nghiệp có thể tận dụng công nghệ này để tạo competitive advantage.
