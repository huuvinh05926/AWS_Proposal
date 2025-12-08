---
title: "Blog 1"
date: "2025-12-07"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Automating Budget Management Across Multi-Account Environments

## Tự động hóa Quản lý Ngân sách trong Môi trường Đa Tài Khoản

Quản lý chi tiêu AWS trên nhiều tài khoản đòi hỏi một cách tiếp cận tinh vi đối với kiểm soát và giám sát ngân sách. Giải pháp tùy chỉnh của chúng tôi cho phép quản lý ngân sách tập trung với các thông báo email tự động, giúp tổ chức có thể thiết lập và áp dụng ngân sách riêng cho từng tài khoản từ một central management account. Hệ thống tự động này theo dõi chi tiêu trên từng tài khoản riêng lẻ và gửi cảnh báo kịp thời khi tài khoản tiến gần hoặc vượt quá ngân sách đã được phân bổ. Central management account đóng vai trò là single source of truth, nơi các nhóm tài chính có thể cấu hình ngưỡng ngân sách riêng cho từng tài khoản và nhận thông báo về mô hình chi tiêu trên toàn bộ hệ thống tài khoản của tổ chức.

## Tổng quan giải pháp

Giải pháp của chúng tôi triển khai một kiến trúc event-driven nhằm tự động hóa quản lý ngân sách trên toàn bộ AWS Organization. Quy trình bắt đầu tại management account, nơi các ngân sách riêng cho từng tài khoản được định nghĩa và lưu trữ trong một bảng Amazon DynamoDB. AWS Lambda function sẽ tự động phân phối (propagate) các cấu hình ngân sách này đến từng tài khoản thông qua AWS Systems Manager (SSM) Parameter Store tương ứng. AWS Budgets giám sát chi tiêu theo thời gian thực, kích hoạt thông báo email khi các tài khoản tiến gần hoặc vượt quá allocated thresholds. Kiến trúc tinh gọn này loại bỏ việc quản lý ngân sách thủ công đồng thời cung cấp cho các nhóm sự linh hoạt trong việc vận hành trong phạm vi chi phí đã được định nghĩa.

## Kiến trúc giải pháp

### Các thành phần của Giải pháp

**AWS Control Tower Management Account:**

- DynamoDB Table lưu trữ thông tin ngân sách cho từng linked account.
- Lambda Function được kích hoạt bởi các cập nhật trong DynamoDB Table và tiến hành cập nhật ngân sách trong các spoke accounts thông qua AWS Systems Manager.

**Linked Account:**

- Kho lưu trữ tham số AWS SSM lưu giữ giá trị ngân sách đã được cập nhật.
- Các sự kiện Amazon CloudWatch kích hoạt quy trình tự động khi tham số (AWS SSM parameter) được cập nhật.
- AWS Budgets quản lý chi phí của tài khoản dựa trên các tham số này.
- AWS Budgets gửi thông báo qua email nếu ngưỡng ngân sách (budget threshold) bị vượt quá.

![Budget Management Architecture & Flow Diagram](../../../images/3-Blog/Blog-1/img1.png)

### Quy trình làm việc:

1. **Nâng cấp bảng DynamoDB**: Người dùng cập nhật giá trị ngân sách cho một linked account trong bảng DynamoDB (BlogBudgetsDynamoDB) nằm trong phần quản lý tài khoản.

2. **DynamoDB Stream Trigger**: Bản cập nhật này kích hoạt một DynamoDB Stream, từ đó kích hoạt chức năng của Lambda (BlogBudgetsUpdateLambda) trong phần quản lý tài khoản.

3. **Chức năng Lambda cập nhật Tham số AWS SSM**: Chức năng của Lambda đọc giá trị ngân sách đã cập nhật từ bảng DynamoDB, thực hiện việc đảm nhận vai trò liên tài khoản (BlogBudgetsSpokeRole) và cập nhật SSM Parameter Store (/BlogBudgets/CostThreshold) trong spoke account với giá trị ngân sách mới.

4. **Quy tắc Amazon EventBridge kích hoạt sự kiện**: Khi SSM Parameter Store trong spoke account được cập nhật, một EventBridge Rule (BlogBudgetsSSMTrigger) sẽ kích hoạt AWS SSM Automation document (BlogBudgetsAutomationDoc) trong spoke account.

5. **Nâng cấp Budgets**: Tài liệu Tự động hóa AWS SSM trong spoke account đọc giá trị ngân sách mới từ SSM Parameter Store và cập nhật giá trị Budgets (SpokeAccountBudget) tương ứng.

6. **Thông báo Email**: Khi chi tiêu đạt đến các ngưỡng được cấu hình, hệ thống sẽ gửi thông báo đến các bên liên quan được chỉ định.

## Vận hành Giải pháp

Dựa trên hành vi của dịch vụ, khi bạn cập nhật giá trị ngân sách cho một tài khoản, giới hạn ngân sách trong AWS Budgets sẽ được cập nhật tương ứng. Tuy nhiên, có một số điểm quan trọng cần lưu ý liên quan đến cảnh báo:

- Ngay cả khi bạn cập nhật giá trị ngân sách sau khi một cảnh báo đã được kích hoạt, trạng thái cảnh báo vẫn giữ nguyên ở trạng thái "Exceeded" (hoặc trạng thái mà nó đang ở thời điểm được kích hoạt). Cảnh báo sẽ không tự đặt lại chỉ vì bạn đã thay đổi giới hạn ngân sách.
- Có thể mất tối đa 8 giờ để trạng thái ngân sách mới được phản ánh trong hệ thống cảnh báo, nghĩa là các thay đổi đối với ngân sách sẽ không ngay lập tức cập nhật trạng thái của cảnh báo.

### Ví dụ minh họa:

Giả sử bạn đặt ngân sách hàng tháng là 100 USD, với cảnh báo được kích hoạt ở 100% mức chi tiêu thực tế.

- Trong tháng, bạn chi tiêu vượt mức và đạt 200 USD.
- Cảnh báo sẽ được kích hoạt, và bạn sẽ nhận được thông báo cho biết ngân sách đã bị vượt quá.
- Ngay cả khi bạn tăng giới hạn ngân sách lên 250 USD (để phản ánh các chi phí bổ sung), cảnh báo vẫn sẽ giữ nguyên ở trạng thái "Exceeded" cho đến khi kết thúc tháng.

Điều này xảy ra vì trạng thái cảnh báo được xác định dựa trên mức chi tiêu thực tế và giới hạn ngân sách ban đầu tại thời điểm cảnh báo được kích hoạt, chứ không phải giới hạn đã được cập nhật. Hành vi này đảm bảo rằng bạn luôn nhận biết được mọi trường hợp vượt ngân sách, đồng thời ngăn việc tự động đặt lại cảnh báo, vốn có thể khiến bạn bỏ sót các mô hình chi tiêu quan trọng.

## Điều kiện tiên quyết

### Thiết lập Tài khoản AWS

- AWS Organizations hoặc AWS Control Tower với cấu trúc đa tài khoản
- Một management account
- Ít nhất một spoke account

### Các dịch vụ AWS bắt buộc truy cập

- AWS Budgets
- AWS Lambda
- Amazon DynamoDB
- AWS Systems Manager (SSM)
- Amazon CloudWatch
- AWS CloudFormation

### Yêu cầu quyền truy cập

Đảm bảo rằng bạn có các quyền tối thiểu cần thiết sau trong các tài khoản AWS của mình:

**Management Account:**

- Quyền triển khai AWS CloudFormation
- Quyền quản lý bảng DynamoDB table management access
- Quyền giám sát Lambda function và CloudWatch logs
- Quyền quản lý cross-account AWS Identity and Access Management (IAM) roles

**Spoke Accounts:**

- Quyền triển khai AWS CloudFormation
- Quyền truy cập read-only để giám sát các quy tắc EventBridge, các tham số và quy trình tự động của Systems Manager, và AWS Budgets
- Địa chỉ email để nhận thông báo ngân sách

Các bước triển khai chi tiết sẽ được trình bày trong các phần tiếp theo của bài viết này.

## Triển khai giải pháp

### 1. Triển khai Stack cho Tài khoản Quản lý

Trong tài khoản quản lý, triển khai CloudFormation Stack có tên 'budget_mgmt_account.yaml', nhấn vào đây để tải mẫu này.

![](../../../images/3-Blog/Blog-1/img2.png)

Mẫu này sẽ triển khai:

- Bảng DynamoDB dùng để lưu trữ giá trị ngân sách (budget) cho từng tài khoản spoke.
- Hàm Lambda được kích hoạt bởi DynamoDB stream để cập nhật SSM Parameter Store (cụ thể là, /BlogBudgets/CostThreshold) trong từng tài khoản spoke với các giá trị ngân sách mới.
- Các vai trò AWS IAM với các quyền cần thiết cho chức năng của Lambda, bao gồm cả quyền truy cập cross-account.

### 2. Triển khai Stack cho các Tài khoản Spoke

Bạn có thể thiết lập stack cho tài khoản spoke theo một trong các cách sau:

**Cách 1**: Triển khai trực tiếp AWS CloudFormation Stack có tên 'budget_spoke_account.yaml' trong từng tài khoản spoke tương ứng.

![](../../../images/3-Blog/Blog-1/img2.png)

**Cách 2**: Sử dụng AWS CloudFormation StackSets từ tài khoản quản lý để triển khai tự động template này cho nhiều tài khoản spoke cùng lúc. Cách này phù hợp nếu bạn đang quản lý nhiều tài khoản spoke và muốn đơn giản hóa quá trình triển khai.

### 3. Cập nhật Bảng DynamoDB

Sau khi triển khai xong:

1. Truy cập vào tài khoản quản lý.
2. Điều hướng đến bảng DynamoDB có tên 'BlogBudgetsDynamoDB'.
3. Đối với mỗi tài khoản spoke, thêm một mục mới:
   - 'AccountId': Nhập ID tài khoản spoke gồm 12 chữ số ví dụ: 111122223333.
   - 'BudgetValue': Nhập giá trị ngân sách mong muốn (dạng số), ví dụ: 1000.

![Hình 2: Bảng Amazon DynamoDB lưu trữ thông tin ngân sách](../../../images/3-Blog/Blog-1/img3.png)

Khi bảng DynamoDB được cập nhật với thông tin tài khoản và giá trị ngân sách, hàm Lambda có tên 'BlogBudgetsUpdateLambda' sẽ tự động được kích hoạt thông qua luồng DynamoDB để cập nhật giá trị ngân sách mới vào SSM Parameter Store của từng tài khoản spoke.

### 4. Cập nhật SSM Parameter Store

Sau khi đảm nhận vai trò liên tài khoản, hàm Lambda sẽ cập nhật SSM Parameter Store trong tài khoản spoke với giá trị ngân sách mới (ví dụ: /BlogBudgets/CostThreshold).

Bước này đảm bảo rằng thông tin ngân sách được đồng bộ sang tài khoản spoke và sẵn sàng cho các hành động tiếp theo.

![Hình 3: Tham số AWS SSM cho Ngưỡng Chi Phí (Cost Threshold)](../../../images/3-Blog/Blog-1/img4.png)

### 5. Kích hoạt Quy tắc Amazon EventBridge

Giá trị được cập nhật trong SSM Parameter Store sẽ kích hoạt một quy tắc của Amazon CloudWatch/EventBridge. Quy tắc này có nhiệm vụ giám sát các thay đổi trong tham số AWS SSM, và phát sinh sự kiện mỗi khi tham số /BlogBudgets/CostThreshold được cập nhật.

![Hình 4: Quy tắc EventBridge kích hoạt AWS SSM](../../../images/3-Blog/Blog-1/img5.png)

### 6. Kích hoạt Quy trình Tự động hóa SSM

Sự kiện CloudWatch sẽ tự động kích hoạt việc thực thi tài liệu SSM Automation trong tài khoản spoke. Tài liệu này sẽ thực hiện hành động cập nhật giá trị Budgets dựa trên giá trị tham số ngân sách mới được lưu trong SSM Parameter Store.

![Hình 5: Tự động cập nhật Ngân sách bằng AWS SSM Automation](../../../images/3-Blog/Blog-1/img6.png)

### 7. Cập nhật Ngân sách

Tài liệu AWS SSM Automation sẽ cập nhật cấu hình Budgets trong tài khoản spoke. Bước này đảm bảo rằng giá trị ngân sách mới được thiết lập trong Budgets, từ đó hệ thống có thể theo dõi và giám sát chi phí một cách chính xác theo ngân sách được cập nhật.

![Hình 6: Cấu hình AWS Budgets sau khi được cập nhật](../../../images/3-Blog/Blog-1/img7.png)

### 8. Thông báo Cảnh báo qua Email

Khi giá trị ngân sách đã được cập nhật trong Budgets, hệ thống sẽ kiểm tra các ngưỡng cảnh báo đã được cấu hình sẵn. Nếu mức chi tiêu hiện tại vượt quá ngưỡng này, một cảnh báo qua email sẽ tự động được kích hoạt. Email này sẽ thông báo cho những người nhận được chỉ định về việc vượt ngân sách, giúp đảm bảo có thể thực hiện hành động kịp thời để kiểm soát chi phí.

![Hình 7: Email thông báo vượt ngưỡng AWS Budgets](../../../images/3-Blog/Blog-1/img8.png)

## Dọn dẹp tài nguyên

Để tránh phát sinh chi phí trong tương lai, bạn nên xóa các tài nguyên đã được triển khai cho mục đích kiểm thử giải pháp, bằng cách xóa các AWS CloudFormation Stack đã được triển khai trong môi trường của bạn.

## Các cải tiến trong tương lai

### Kích hoạt Hành động Khắc phục

Để nâng cao hơn nữa khả năng kiểm soát chi phí AWS, bạn có thể triển khai các hành động khắc phục tự động bằng cách sử dụng AWS Budget Actions. Tính năng này cho phép tự động kích hoạt các phản ứng điều chỉnh chi phí khi ngưỡng ngân sách bị vượt quá. A Budget Action là một tính năng trong AWS Budgets cho phép bạn định nghĩa các phản hồi tiết kiệm chi phí tự động bất cứ khi nào cảnh báo ngân sách được kích hoạt. Điều này giúp đảm bảo phản ứng được thực hiện mà không cần can thiệp thủ công, đồng thời thúc đẩy văn hóa tiết kiệm chi phí trong tổ chức.

Bạn có thể gắn các hành động khắc phục vào các cảnh báo ngân sách, được cấu hình để kích hoạt hành động khi ngân sách vượt quá một ngưỡng nhất định — dù là chi tiêu thực tế hay dự đoán. Điều này đặc biệt hữu ích trong việc tránh chi tiêu vượt mức ngoài ý muốn.

**Ví dụ:**

- **Chính sách IAM**: Bạn có thể áp dụng chính sách IAM "Deny EC2 Run Instances" cho người dùng, nhóm hoặc vai trò khi ngân sách EC2 bị vượt quá.
- **Nhắm mục tiêu các phiên bản cụ thể**: Bạn có thể định nghĩa hành động dừng các EC2 instance trong một khu vực cụ thể khi ngân sách sử dụng EC2 bị vi phạm.

Tính năng này giúp các tổ chức tự động hóa phản ứng tối ưu chi phí dựa trên ngưỡng ngân sách được xác định, giúp duy trì sự phù hợp với các mục tiêu tài chính.

### Tích hợp với ServiceNow để Tự động hóa Quy trình ITSM

Một hướng cải tiến khác trong tương lai là tích hợp giải pháp này với ServiceNow nhằm tự động hóa liền mạch các quy trình Quản lý Dịch vụ CNTT (ITSM). Bằng cách kết hợp AWS Budgets và các hành động khắc phục với ServiceNow, tổ chức có thể tự động tạo ticket hoặc sự cố khi một ngưỡng ngân sách bị vượt quá. Các sự cố này sau đó có thể kích hoạt các quy trình tự động hóa được định nghĩa sẵn trong ServiceNow, chẳng hạn như thông báo cho các nhóm liên quan hoặc khởi động quy trình tối ưu hóa chi phí.

**Ví dụ:**

- Khi cảnh báo ngân sách vượt quá một ngưỡng nhất định, một incident sẽ tự động được tạo trong ServiceNow để thông báo cho đội ngũ tài chính hoặc vận hành đám mây.
- ServiceNow có thể tự động leo thang vấn đề lên các nhóm cấp cao hơn, hoặc khởi tạo các hành động khắc phục như yêu cầu phê duyệt để giảm quy mô tài nguyên hoặc thực hiện đánh giá chi phí.

- Sự tích hợp này giúp tăng cường luồng thông tin giữa các nhóm tài chính và vận hành, tự động hóa quy trình ticketing, và đảm bảo các vấn đề vượt ngân sách được xử lý kịp thời và hiệu quả.

## Kết luận

Giải pháp này mang đến một phương thức tự động và có khả năng mở rộng để quản lý ngân sách trên nhiều tài khoản AWS, tận dụng các dịch vụ như Amazon DynamoDB, AWS Systems Manager Parameter Store, AWS Lambda, và AWS Budgets. Giải pháp giúp các tổ chức giám sát chi phí hiệu quả và nhận thông báo kịp thời khi ngân sách bị vượt quá giới hạn cho phép.

Các nâng cấp trong tương lai, như tích hợp AWS Budget Actions để tự động khắc phục và liên kết với ServiceNow để tự động hóa quy trình ITSM, sẽ tăng cường khả năng quản lý chi phí, đồng thời cải thiện tốc độ phản hồi khi xảy ra vi phạm ngân sách. Bằng cách triển khai giải pháp này, các tổ chức có thể kiểm soát chi phí AWS tốt hơn, duy trì chi tiêu trong phạm vi ngân sách, và tối ưu hóa hiệu quả sử dụng tài nguyên đám mây.

Giải pháp hiện có sẵn tại [AWS-SAMPLES-REPO](https://github.com/aws-samples/sample-event-driven-budget-management-on-aws)

**TAGS:** AWS Budget, CFM

---

## Tác giả

![](../../../images/3-Blog/Blog-1/img9.png)

### Gautam Bhaghavatula

Là Kiến trúc sư Giải pháp Đối tác Cấp cao (Senior Partner Solutions Architect) tại AWS, Gautam Bhaghavatula tận dụng nền tảng chuyên sâu về kiến trúc hạ tầng đám mây để thiết kế các giải pháp có khả năng mở rộng cao và triển khai các biện pháp bảo mật mạnh mẽ. Chuyên môn của ông bao gồm hệ thống, mạng, microservices và DevOps, với việc ứng dụng các công nghệ tiên tiến nhất của AWS. Hiện tại, ông hợp tác cùng các đối tác của AWS nhằm thúc đẩy các dự án di chuyển và hiện đại hóa hệ thống lên đám mây, thông qua định hướng chiến lược và lãnh đạo kỹ thuật chuyên sâu.

![](../../../images/3-Blog/Blog-1/img10.png)

### Matt Saeger

Chuyên gia Tư vấn Triển khai Cấp cao tại Amazon Web Services (AWS), người dẫn dắt các sáng kiến chiến lược về điện toán đám mây và điều phối các chương trình chuyển đổi quy mô doanh nghiệp cho khách hàng trong lĩnh vực dịch vụ tài chính. Sở hữu 11 chứng chỉ AWS, Matt kết hợp kiến thức chuyên sâu về kiến trúc đám mây, DevOps, và kiến trúc mạng cùng với kinh nghiệm lãnh đạo các chương trình triển khai đám mây phức tạp. Ông chuyên về xây dựng chiến lược đám mây ở cấp doanh nghiệp, thiết kế các giải pháp an toàn và có khả năng mở rộng cao, đồng thời phát triển các giải pháp tự động hóa với trọng tâm là bảo mật và tuân thủ. Hãy liên hệ với Matt để trao đổi về chiến lược chuyển đổi đám mây, ứng dụng đám mây trong lĩnh vực tài chính, và các phương pháp bảo mật tốt nhất trong môi trường cloud.
