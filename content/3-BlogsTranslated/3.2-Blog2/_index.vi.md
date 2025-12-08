---
title: "Blog 2"
date: "2025-12-07"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Introducing: Guidance for a media lake on AWS

## Giới thiệu: Hướng dẫn xây dựng Media Lake trên AWS

Nhiều doanh nghiệp hiện đang gặp khó khăn trong việc quản lý khối lượng lớn các tệp phương tiện số được lưu trữ rải rác trên nhiều Amazon Simple Storage Service (Amazon S3) buckets. Cách lưu trữ phân tán này gây ra nhiều thách thức nghiêm trọng. Việc tìm kiếm nội dung cụ thể có thể rất khó khăn và tốn nhiều thời gian (việc tổ chức tệp một cách hiệu quả cũng trở thành một nhiệm vụ phức tạp), khiến cho việc khai thác hết giá trị từ nội dung hiện có trở nên đầy thách thức.

Các nhóm truyền thông thường phải tìm kiếm thủ công qua nhiều vị trí lưu trữ khác nhau, chỉ dựa vào tên tệp để nhận diện nội dung. Quy trình kém hiệu quả này làm chậm trễ luồng công việc sản xuất và cản trở khả năng tái sử dụng tài nguyên truyền thông một cách hiệu quả.

Hướng dẫn xây dựng Media Lake trên Amazon Web Services (AWS) của chúng tôi sẽ chỉ cho bạn cách tạo ra một hệ thống tập trung để tìm kiếm và quản lý tài sản truyền thông được lưu trữ trên AWS. Giải pháp này cung cấp giao diện người dùng thân thiện và API tiện lợi để tìm kiếm và quản lý tệp phương tiện, đồng thời cho phép bạn tạo một danh mục thống nhất cho toàn bộ tài sản truyền thông — dù chúng đang nằm ở nhiều S3 bucket khác nhau. Quan trọng hơn, bạn có thể đạt được sự tổ chức này mà không cần thay đổi cấu trúc lưu trữ hiện có. Hướng dẫn của chúng tôi sử dụng các quy trình tự động để lập danh mục và xử lý các tệp phương tiện, giúp tăng tốc độ tìm kiếm và khai thác nội dung một cách hiệu quả hơn.

Chúng tôi sẽ hướng dẫn bạn cách một media lake có thể giúp bạn khai thác nhiều giá trị hơn từ nội dung số bằng cách tạo ra một hệ thống lưu trữ media có thể mở rộng và tìm kiếm được, hoạt động liền mạch với các dịch vụ AWS và các giải pháp từ đối tác. Chúng tôi sẽ giải thích thiết kế của hệ thống, giới thiệu các cách khác nhau để thiết lập nó, và trình bày cách biến các tệp media rải rác của bạn thành một bộ sưu tập được sắp xếp và dễ tìm kiếm.

## Tổng quan

Hướng dẫn của chúng tôi về media lake trên AWS cung cấp một kiến trúc tham chiếu và mẫu mã nguồn mà bạn có thể triển khai để tạo hệ thống quản lý media. Giải pháp này minh họa cách để:

- Tạo một giao diện tìm kiếm thống nhất, cho phép bạn tìm kiếm các tệp media trên tất cả các vị trí lưu trữ Amazon S3 cùng một lúc.
- Xây dựng các quy trình xử lý media tự động theo sự kiện, bằng cách sử dụng các pipeline mặc định và tùy chỉnh trong giao diện kéo thả.
- Kích hoạt khả năng tìm kiếm bằng ngôn ngữ tự nhiên thông qua các tích hợp được hỗ trợ bởi AI.
- Tổ chức các tệp media của bạn bằng cách tìm nhanh chóng, xem trước nội dung, và xem thông tin kỹ thuật cũng như mô tả và chi tiết của chúng.

## Triển khai

Media lake sử dụng AWS Cloud Development Kit (AWS CDK) cho mô hình Cơ sở hạ tầng dưới dạng mã (IaC). Bạn có thể thiết lập mã mẫu bằng một trong ba phương pháp sau:

### 1. Mẫu AWS CloudFormation

Sử dụng mẫu CloudFormation được cung cấp sẵn để tự động tạo AWS CodePipeline. Pipeline này sẽ dùng AWS CodeBuild để triển khai ứng dụng AWS CDK trong tài khoản AWS và khu vực mà bạn chọn.

### 2. Triển khai trong môi trường cục bộ

Triển khai media lake trực tiếp từ máy tính của bạn bằng các phương pháp triển khai chuẩn của AWS CDK. Tùy chọn này mang lại nhiều linh hoạt hơn, cho phép bạn thay đổi cấu hình triển khai, cũng như chọn AWS profile trước khi triển khai đến các AWS Region khác nhau khi cần.

### 3. Pipeline Tích hợp và Triển khai Liên tục (CI/CD)

Nếu bạn đã có pipeline CI/CD hiện có dùng để triển khai mã AWS CDK, bạn có thể tích hợp media lake vào pipeline đó, cho phép bạn triển khai media lake thông qua pipeline CI/CD sẵn có của tổ chức.

Dù bạn chọn phương pháp nào, cả ba cách đều thiết lập cùng một bộ tài nguyên AWS. Sự linh hoạt này giúp bạn chọn phương pháp triển khai phù hợp nhất với quy trình và nhu cầu hiện tại của tổ chức.

## Tổng quan kiến trúc

Hệ thống này cung cấp giao diện người dùng và RESTful API được xây dựng theo kiến trúc không máy chủ nhằm đảm bảo khả năng mở rộng và tính bảo mật. Amazon CloudFront phân phối nội dung tĩnh của giao diện người dùng được lưu trữ trong Amazon S3, giúp truy cập nhanh và ổn định trên toàn cầu, trong khi đó AWS WAF bảo vệ hệ thống khỏi các lỗ hổng và tấn công web phổ biến. Amazon API Gateway xử lý các yêu cầu, trong khi Amazon Cognito đảm nhiệm việc xác thực người dùng, đồng thời tạo mã token bảo mật để truy cập tài nguyên API.

Media lake lưu trữ dữ liệu backend trong Amazon DynamoDB và Amazon OpenSearch Service. Các tệp phương tiện, nhật ký và mã hạ tầng được lưu trữ trong Amazon S3. Hệ thống quản lý quy trình làm việc của mình bằng AWS Step Functions, thành phần này chịu trách nhiệm điều phối toàn bộ quy trình, trong khi các hàm AWS Lambda đảm nhiệm công việc thực tế là truy cập và quản lý dữ liệu trong các hệ thống lưu trữ.

Để điều phối quy trình luồng công việc media, được sử dụng để tương tác với các kho dữ liệu backend và bộ lưu trữ, hãy xem kiến trúc tham chiếu dành cho media lake.

## Bắt đầu

Khi bạn triển khai hệ thống của chúng tôi, hệ thống sẽ tự động tạo một tài khoản quản trị viên. Một email mời sẽ được gửi đến địa chỉ bạn đã cung cấp trong suốt quá trình thiết lập. Khi đăng nhập lần đầu, bạn sẽ cần đưa ra một quyết định quan trọng về cách bạn muốn tìm kiếm media asset của mình.

Bạn có hai lựa chọn chính:

### Tìm kiếm theo metadata truyền thống

Phương pháp này dựa vào từ khóa được tạo bởi AI, siêu dữ liệu kỹ thuật, hoặc tệp để tìm các media asset. Cách này tương tự như các hệ thống tìm kiếm tệp truyền thống.

### Tìm kiếm ngữ nghĩa

Tính năng nâng cao này cho phép bạn sử dụng truy vấn ngôn ngữ tự nhiên để tìm kiếm media. Ví dụ: bạn có thể gõ "tìm các ảnh về xe đua màu đỏ" hoặc "cho tôi xem video về bờ biển lúc hoàng hôn". Phương pháp này vượt xa việc khớp từ khóa đơn thuần — nó hiểu được ý nghĩa đằng sau truy vấn của bạn.

Điều quan trọng là phải quyết định phương pháp tìm kiếm và cấu hình cài đặt trước khi bắt đầu nhập media vào media lake. Điều này đảm bảo rằng tất cả tài sản media được lập chỉ mục đúng cách ngay từ đầu, giúp tăng tốc độ tìm kiếm sau này.

Nếu bạn bật tìm kiếm ngữ nghĩa, tìm kiếm siêu dữ liệu truyền thống vẫn khả dụng, và bạn có thể chuyển đổi linh hoạt giữa hai phương pháp này. Hình 1 là ví dụ về tìm kiếm ngữ nghĩa, hiển thị truy vấn: "những ngọn núi với tuyết trên chúng và có nền màu tím".

![Hình 1: Ví dụ về semantic search.](../../../images/3-Blog/Blog-2/img1.png)

Hiện tại, để kích hoạt semantic search, hệ thống hướng dẫn của chúng tôi sử dụng mô hình nhúng TwelveLabs' Marengo cho khả năng hiểu đoạn video AI-powered, kết hợp với OpenSearch Service đóng vai trò như cơ sở dữ liệu vector. Hãy chọn TwelveLabs API làm nhà cung cấp nhúng và OpenSearch Service làm kho lưu trữ nhúng. Tiếp theo, cấu hình tích hợp TwelveLabs và nhập các pipeline âm thanh, hình ảnh và video được cấu hình sẵn của TwelveLabs. Sau khi hoàn tất cấu hình, các pipelines này sẽ tự động tạo embeddings cho toàn bộ phương tiện được hỗ trợ được nạp vào, từ đó kích hoạt chức năng tìm kiếm ngữ nghĩa.

## Storage connectors

Hệ thống hướng dẫn này sử dụng storage connectors để liên kết các S3 buckets hiện có của bạn với hệ thống. Các connectors này có hai mục đích quan trọng: Thứ nhất, chúng tự động xử lý mọi tệp media mới được thêm vào trong S3 buckets của bạn; Thứ hai, chúng đồng bộ các tệp media hiện có trong S3 buckets với media lake của bạn. Điều này giúp tạo ra một giao diện thống nhất, hiển thị toàn bộ các tệp media của bạn từ nhiều vị trí lưu trữ khác nhau.

Khi bạn thêm một storage connector, hệ thống hướng dẫn sẽ bắt đầu chuỗi bước để tích hợp nội dung của bạn:

1. Kích hoạt các thông báo về Amazon EventBridge trên S3 bucket mục tiêu, nếu chưa được bật.
2. Tạo một EventBridge rule để chuyển các Amazon S3 events đến Amazon Simple Queue Service (Amazon SQS) queue nhằm đảm bảo quá trình xử lý sự kiện ổn định.
3. Khi được triển khai, hệ thống lưu Amazon S3 ingest Lambda function vào IaC S3 bucket. Hàm Lambda này xử lý các sự kiện được xếp hàng để tự động lập chỉ mục các tài sản media mới.
4. Sau khi Lambda function xử lý media asset, một event sẽ được gửi đến media lake analysis event bus để thực hiện phân tích và chuyển đổi bổ sung cho media asset đó.

Hướng dẫn của chúng tôi hiện tại yêu cầu các storage connectors phải nằm trong cùng một AWS Region và account với media lake. Sau khi bạn thêm media được hỗ trợ mới vào S3 bucket sau khi đã tạo storage connector, hệ thống sẽ tự động phát hiện, lập chỉ mục, và cho phép tìm kiếm các tệp media này.

## Media lake integrations

Các media lake integrations cung cấp khả năng quản lý thông tin xác thực an toàn, được sử dụng bởi các pipelines để truy cập vào các dịch vụ bên ngoài trong media workflows của bạn. Bằng cách tách riêng thông tin xác thực khỏi cấu hình pipeline, bạn có thể xoay vòng API keys và quản lý quyền truy cập một cách độc lập mà không cần chỉnh sửa workflows. Cách tiếp cận này cho phép bạn cập nhật thông tin xác thực ở một nơi duy nhất, và sự thay đổi đó sẽ tự động áp dụng cho tất cả các pipelines đang sử dụng thông tin xác thực đó. Bạn có thể sử dụng media lake interface để tạo, chỉnh sửa, và cập nhật các integrations cho các dịch vụ bên ngoài.

Hệ thống hướng dẫn này sử dụng AWS Secrets Manager để lưu trữ an toàn toàn bộ thông tin xác thực. Khi bạn tạo một pipeline, hệ thống sẽ lưu các thông tin xác thực cần thiết dưới dạng biến môi trường thông qua Secrets Manager ARNs (Amazon Resource Names). Trong quá trình pipeline execution, mỗi bước cần truy cập vào external service sẽ truy xuất thông tin xác thực tương ứng từ Secrets Manager bằng ARN đã được lưu. Cách tiếp cận này mang lại hai lợi ích chính: tuân thủ AWS security best practices trong việc quản lý third-party API keys và cung cấp khả năng kiểm soát tập trung đối với toàn bộ thông tin xác thực trong media workflows của bạn. Phương pháp này giúp quản lý thông tin xác thực an toàn và hiệu quả trong suốt quá trình xử lý media.

## Media lake pipelines

Hệ thống hướng dẫn này giúp tối ưu hóa việc tạo các media workflows trên AWS thông qua tính năng pipeline. Trong quá trình triển khai, hệ thống sẽ đọc các tệp cấu hình từ repository của nó để xác định các node cần được tạo và thiết lập. Các node này sau đó sẽ hiển thị trong giao diện kéo-thả, cho phép bạn thiết kế trực quan workflow của mình.

Khi bạn đã sắp xếp workflow và lưu pipeline, hệ thống sẽ chuyển đổi bản thiết kế của bạn thành một AWS Step Functions state machine. State machine này sẽ điều phối quá trình media workflow theo đúng cấu hình cụ thể mà bạn đã định nghĩa.

Để quản lý quá trình thực thi workflow, hệ thống sẽ thiết lập thêm ba thành phần bổ sung: một Amazon EventBridge rule, một Amazon SQS queue, và một AWS Lambda function. EventBridge rule chịu trách nhiệm gửi events đến SQS queue, trong khi Lambda function sẽ xử lý các events này từ queue và kích hoạt Step Function tương ứng, bắt đầu media workflow của bạn.

Cơ chế này mang lại một cách tiếp cận thân thiện với người dùng để xây dựng các quy trình xử lý các media phức tạp, đồng thời tận dụng sức mạnh của các dịch vụ AWS ở tầng phía sau.

Khi được triển khai, hệ thống sẽ tự động triển khai ba pipeline mặc định: Default Video Pipeline, Default Audio Pipeline, và Default Image Pipeline. Các pipeline này chịu trách nhiệm tạo bản sao, thumbnail, và trích xuất siêu dữ liệu kỹ thuật từ các media assets được xử lý bởi quá trình storage connectors. Khi các tệp media được hỗ trợ mới được tải lên S3 buckets đã được kết nối, các pipeline mặc định sẽ tự động bắt đầu xử lý chúng, đảm bảo rằng toàn bộ media assets của bạn được xử lý một cách nhất quán. Hình bên dưới minh họa mã video mặc định trong giao diện kéo-thả.

![Hình 2: Media lake default pipeline.](../../../images/3-Blog/Blog-2/img2.png)

Media lake hỗ trợ nhập các pipeline template được cấu hình sẵn; repository mã nguồn bao gồm các sample template minh họa cho các mô hình xử lý media phổ biến. Khi nhập pipeline templates, hệ thống sẽ yêu cầu bạn ánh xạ các integrations cần thiết, đồng thời duy trì quản lý thông tin xác thực an toàn trên toàn bộ workflows của bạn.

Hệ thống hướng dẫn này thu thập metadata của media asset trong quá trình thực thi pipeline để giúp bạn hiểu rõ hơn và làm việc hiệu quả hơn với media assets. Siêu dữ liệu này được lưu trữ qua hai dịch vụ AWS bổ trợ: Amazon DynamoDB đóng vai trò kho lưu trữ siêu dữ liệu chính, trong khi Amazon OpenSearch Service cung cấp khả năng tìm kiếm toàn văn bản. Khi các pipelines xử lý media assets, technical metadata sẽ được trích xuất — bao gồm độ phân giải, độ sâu bit, tần số mẫu, thông tin codec, bitrate, và thời lượng. Media lake sẽ tự động lưu dữ liệu này vào DynamoDB và lập chỉ mục trong OpenSearch Service.

Đối với nội dung audio và video, các dịch vụ phiên âm AI-powered sẽ tạo ra các đoạn văn bản được căn chỉnh theo thời gian, giúp nội dung thoại có thể tìm kiếm và truy cập được. Bạn cũng có thể cấu hình và thêm các trường siêu dữ liệu bổ sung cho tổ chức của mình để theo dõi, xem và sử dụng. Cách tiếp cận lưu trữ kép này giúp tìm kiếm nhanh như chớp, hiểu rõ chất lượng và thông số kỹ thuật của asset, truy cập vào các insight do AI tạo ra, và trích xuất tệp ở định dạng phù hợp cho các downstream workflows.

Sau khi người dùng tìm kiếm assets, họ có thể điều hướng đến màn hình chi tiết asset để xem media assets của mình. Đối với audio và video assets, kiến trúc hệ thống sử dụng Omakase Player, một trình phát web mã nguồn mở được thiết kế cho các tình huống sử dụng trong chuỗi cung ứng media. Omakase Player mang lại trải nghiệm xem chính xác từng khung hình và cho phép hiển thị metadata theo thời gian tương ứng với proxy.

Khi người dùng chọn một asset, hệ thống hướng dẫn sẽ tạo một pre-signed Amazon S3 URL an toàn, giới hạn thời gian, cho phép truy cập vào proxy được lưu trong Amazon S3. Các pre-signed URLs này cho phép phát nội dung trực tiếp từ Amazon S3 và tự động hết hạn sau một khoảng thời gian xác định, đảm bảo truy cập thuận tiện mà vẫn duy trì bảo mật.

Trang asset chi tiết cung cấp giao diện chi tiết cho media assets của bạn, kết hợp xem trước, tùy chọn tải xuống, và metadata chi tiết. Bạn có thể xem nhanh bản proxy của media để phát lại, đồng thời vẫn giữ quyền truy cập vào cả tệp gốc và các phiên bản proxy phục vụ cho những yêu cầu workflow khác nhau.

## Kết luận

Hệ thống hướng dẫn cho media lake trên AWS minh họa cách xây dựng giải pháp quản lý media trên AWS, giúp hợp nhất các assets từ nhiều S3 buckets thành một danh mục có thể tìm kiếm đồng thời tạo ra các media workflows. Hệ thống này sử dụng các dịch vụ serverless như Amazon CloudFront, Amazon API Gateway, AWS Lambda, và Amazon DynamoDB để xây dựng một kho lưu trữ media có khả năng mở rộng.

Các khả năng chính bao gồm tạo các media workflows trực quan (gọi là pipelines), sử dụng AWS Step Functions cho quá trình xử lý media tự động, và dùng AWS Secrets Manager để quản lý thông tin xác thực an toàn trong các tích hợp với bên thứ ba. Người dùng có thể tìm kiếm nội dung theo hai cách: thông qua tìm kiếm truyền thống bằng metadata, hoặc tìm kiếm ngữ nghĩa được hỗ trợ bởi AI, có khả năng hiểu ý nghĩa đằng sau các cụm tìm kiếm. Hệ thống hướng dẫn này giúp bạn duy trì lưu trữ hiện tại trên Amazon S3, đồng thời kết hợp khả năng khám phá tập trung, quy trình tự động hóa, và phát lại media chuyên nghiệp thông qua proxy streaming chính xác từng khung hình.

Bằng cách triển khai Guidance cho một media lake trên AWS patterns, bạn có thể chuyển đổi các kho lưu trữ media rời rạc thành một hệ thống thông minh có khả năng xử lý, lập chỉ mục và hiển thị nội dung thông qua một giao diện duy nhất. Các nhóm của bạn sẽ có thể tìm kiếm và sử dụng media assets một cách hiệu quả trên toàn bộ tổ chức, bất kể vị trí lưu trữ.

Liên hệ với AWS Representative để biết thêm chi tiết về cách chúng tôi có thể hỗ trợ tăng tốc cho doanh nghiệp của bạn.

## Đọc thêm

- NAB SHOW 2025 Trình diễn Demo – Tăng cường nội dung Podcast
- AWS cho Truyền thông & Giải trí
- Hướng dẫn về Tự động hóa Media Workflow theo Sự kiện trên AWS

---

## Tác giả

![](../../../images/3-Blog/Blog-2/img3.png)

### Robert Raver

Robert Raver là Sr. Solutions Architect cho truyền thông và giải trí tại AWS, đồng thời dẫn dắt các sáng kiến Media Supply Chain. Ông thiết kế các kiến trúc đám mây sáng tạo nhằm tối ưu hóa media workflows, giải quyết các thách thức ngành liên quan đến xử lý media, quyền, tiêu đề, QC, và quản lý metadata. Robert có hơn 20 năm kinh nghiệm trong các vai trò liên quan đến Media & Entertainment và ngành Tài chính, bao gồm lãnh đạo, kiến trúc, và kỹ thuật.
