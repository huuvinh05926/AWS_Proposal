---
title: "Blog 3"
date: "2025-12-07"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Dynamic configuration updates in .NET using Parameter Store and Secrets Manager

## Cập nhật cấu hình động trong .NET sử dụng Parameter Store và Secrets Manager

Tải cấu hình và thông tin bí mật trong các ứng dụng .NET là một bài tập phổ biến. Tuy nhiên, việc này đi kèm với những thách thức trong lưu trữ và truy cập an toàn, linh hoạt, mà không cần khởi động lại ứng dụng.

AWS Systems Manager Parameter Store cung cấp một giải pháp tập trung để lưu trữ và quản lý dữ liệu cấu hình và các dữ liệu mật. Bài blog này khám phá một cách tiếp cận nâng cao để quản lý chúng trong các ứng dụng .NET, tập trung vào:

- Tham chiếu các secrets của AWS Secrets Manager thông qua Parameter Store
- Tải cấu hình từ cả Parameter Store và Secrets Manager
- Triển khai tự động nạp lại cấu hình mà không cần khởi động lại ứng dụng

## Tổng quan giải pháp

Bạn có thể truy xuất secrets được lưu trong Secrets Manager trực tiếp từ Parameter Store bằng định dạng sau:

```
/aws/reference/secretsmanager/<secret-path>
```

Bằng cách tuân theo định dạng này, Systems Manager sẽ hiểu rằng nó cần lấy secret từ Secrets Manager thay vì từ Parameter Store.

Ví dụ, để tham chiếu một secret có tên `dev/DbPassword`, bạn sẽ sử dụng:

```
/aws/reference/secretsmanager/dev/DbPassword
```

Xem [Referencing AWS Secrets Manager secrets from Parameter Store parameters](https://docs.aws.amazon.com/systems-manager/latest/userguide/integration-ps-secretsmanager.html) để biết thêm thông tin.

Giải pháp này sử dụng Parameter Store và Secrets Manager, kết hợp với cấu hình .NET và IOptionsMonitor pattern, để giải quyết các thách thức phổ biến về cấu hình sau:

- **Truy cập thống nhất**: Sử dụng Parameter Store làm điểm truy cập duy nhất cho cả cấu hình và secrets của Secrets Manager.
- **Bảo mật**: Dữ liệu nhạy cảm được lưu trong Secrets Manager và tham chiếu trong Parameter Store, đảm bảo mã hóa và kiểm soát truy cập đúng cách.
- **Cập nhật động**: Triển khai tự động nạp lại các giá trị cấu hình mà không cần khởi động lại ứng dụng.
- **Phân tách môi trường**: Sử dụng cấu trúc phân cấp (hierarchical structure) trong Parameter Store để tách biệt cấu hình theo môi trường.

## Yêu cầu trước khi bắt đầu

- Tài khoản AWS với các quyền cần thiết
- .NET 8 SDK

## Kiến trúc

Xem xét một ứng dụng chạy trên EC2 instance cần truy cập cả các tham số cấu hình lẫn secrets nhạy cảm trong quá trình hoạt động. Ứng dụng này giả định một IAM role với các quyền cần thiết và lấy giá trị từ Parameter Store cho cả dữ liệu cấu hình và secrets.

- Khi ứng dụng yêu cầu một tham số cấu hình, Parameter Store sẽ trả về giá trị trực tiếp.
- Nếu tham số đó là một tham chiếu tới secret được lưu trong Secrets Manager, Parameter Store sẽ lấy secret từ Secrets Manager và trả về cho ứng dụng.

![Hình 1: Kiến trúc giải pháp](../../../images/3-Blog/Blog-3/img1.png)

## Hướng dẫn thực hành

Hãy cùng tìm hiểu cách lấy giá trị cấu hình từ các dịch vụ AWS trong ứng dụng nêu trên. Ứng dụng cần truy xuất hai loại dữ liệu:

- Tham số hệ thống như Database Hostname và API Endpoint từ Parameter Store
- Thông tin nhạy cảm như Database Password và API Key từ Secrets Manager

Trong hướng dẫn này, bạn sẽ xây dựng một ứng dụng .NET có khả năng truy cập an toàn các giá trị cấu hình từ cả hai dịch vụ AWS.

### Bước 1: Cấu hình các tham số và secrets

#### Lưu tham số trong AWS Systems Manager

Thiết lập các tham số trong AWS Systems Manager sử dụng cấu trúc phân cấp sau:

| Môi trường phát triển | Môi trường sản xuất |
| --------------------- | ------------------- |
| /dev/DbHostname       | /prod/DbHostname    |
| /dev/ApiEndpoint      | /prod/ApiEndpoint   |

#### Lưu secrets trong AWS Secrets Manager

Thiết lập secrets trong AWS Secrets Manager sử dụng cấu trúc phân cấp (hierarchical structure) sau:

| Môi trường phát triển | Môi trường sản xuất |
| --------------------- | ------------------- |
| /dev/DbPassword       | /prod/DbPassword    |
| /dev/ApiKey           | /prod/ApiKey        |

#### Tạo IAM Role để truy cập các tham số cấu hình và secrets

Để truy cập các tham số và secrets, bạn cần tạo một IAM Role với các quyền hạn sau. Role này sẽ cấp các quyền cần thiết để truy cập vào các tài nguyên yêu cầu.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor0",
      "Effect": "Allow",
      "Action": [
        "ssm:GetParameter",
        "ssm:GetParameters",
        "ssm:GetParametersByPath"
      ],
      "Resource": ["arn:aws:ssm:${Region}:${AccountId}:parameter/*"]
    },
    {
      "Sid": "VisualEditor1",
      "Effect": "Allow",
      "Action": "secretsmanager:GetSecretValue",
      "Resource": ["arn:aws:secretsmanager:${Region}:${AccountId}:secret:*"]
    }
  ]
}
```

### Bước 2: Thiết lập ứng dụng .NET

#### Cấu hình AWS Services Extension

Tạo hai phương thức mở rộng (extension methods) để cấu hình các dịch vụ AWS như sau.

Phương thức mở rộng sau sẽ thêm cấu hình ứng dụng từ Parameter Store dựa trên đường dẫn được cung cấp.

```csharp
public static void AddParameterStoreConfiguration(this WebApplicationBuilder builder)
{
    var configuration = builder.Configuration;

    // Retrieve current environment (e.g., /dev, /prod)
    var appSettingsPath = configuration["Environment"];

    configuration.AddSystemsManager(options =>
    {
        options.Path = appSettingsPath;
        options.ReloadAfter = TimeSpan.FromMinutes(5); // Reloads for every 5 minutes
    });
}
```

Phương thức mở rộng sau sẽ thêm cấu hình từ Secrets Manager bằng cách sử dụng đường dẫn tham chiếu của Systems Manager.

```csharp
public static void AddSecretsManagerConfiguration(this WebApplicationBuilder builder)
{
    var configuration = builder.Configuration;

    // Retrieve current environment (e.g., /dev, /prod)
    var environmentPath = configuration["Environment"];

    var secretPath = $"/aws/reference/secretsmanager/{environmentPath}/<SecretName>";
    configuration.AddSystemsManager(options =>
    {
        options.Path = secretPath;
        options.ReloadAfter = TimeSpan.FromMinutes(5);
        options.Optional = true;
    });
}
```

#### AppSettings

Để thử nghiệm cục bộ, vui lòng cấu hình tệp `appSettings.json` của bạn như sau.

```json
"AppConfig": {
  "DbHostname": "",
  "ApiEndpoint": ""
},
"Secrets": {
  "DbPassword": "",
  "ApiKey": ""
}
```

#### Configuration Model

Một model được sử dụng để ràng buộc các giá trị cấu hình từ Secrets Manager và Parameter Store. Thêm hai lớp sau vào dự án của bạn:

```csharp
public class SecretSettings
{
    public string DbPassword { get; set; }
    public string ApiKey { get; set; }
}

public class AppConfig
{
    public string DbHostname { get; set; }
    public string ApiEndpoint { get; set; }
}
```

#### Cấu hình Startup

Đăng ký cấu hình các dịch vụ AWS và cấu hình cần thiết cho IOptionsMonitor trong quá trình khởi động (startup):

```csharp
// Add AWS Configuration.
builder.AddParameterStoreConfiguration();
builder.AddSecretsManagerConfiguration();

builder.Services.Configure<AppConfig>(builder.Configuration.GetSection("AppConfig"));
builder.Services.PostConfigure<SecretSettings>(options =>
{
    options.ApiKey = builder.Configuration["ApiKey"];
    options.DbPassword = builder.Configuration["DbPassword"];
});
```

#### Sử dụng cấu hình động

Sử dụng `IOptionsMonitor<T>` để truy cập các giá trị cấu hình mới nhất và phản ứng với các thay đổi. Cách làm này tạo sự linh hoạt trong việc làm mới secrets mà không cần triển khai lại hoặc khởi động lại ứng dụng.

```csharp
public class MyService
{
    private readonly IOptionsMonitor<AppConfig> _appConfig;
    private readonly IOptionsMonitor<SecretSettings> _secretSettings;

    public MyService(
       IOptionsMonitor<AppConfig> appConfig,
       IOptionsMonitor<SecretSettings> secretSettings)
    {
        _appConfig = appConfig;
         _secretSettings = secretSettings;
    }

    public void DoSomething()
    {
        // Always get the latest configuration
        var config = _appConfig.CurrentValue;
        var apiEndpoint = config.ApiEndpoint; //Access parameter store value.
        var dbPassword = _secretSettings.CurrentValue.DbPassword; //Access secret value.
    }
}
```

### Cách hoạt động

Dưới đây là cách ứng dụng lấy giá trị từ Secrets Manager và Parameter Store:

1. Khi ứng dụng khởi động, nó tải cấu hình từ Parameter Store cho môi trường được chỉ định.
2. Ứng dụng tải cả cấu hình và secrets (sử dụng reference path) trực tiếp từ Parameter Store.
3. AWS SDK cho .NET sẽ tự động giải quyết các tham chiếu này, lấy giá trị thực của secret từ Secrets Manager.
4. Cấu hình được tải lại mỗi 5 phút (theo thiết lập trong ReloadAfter).
5. `IOptionsMonitor<T>` đảm bảo rằng ứng dụng luôn sử dụng giá trị cấu hình mới nhất.
6. Bất kỳ thay đổi nào về tham số trong Parameter Store hoặc secrets trong Secrets Manager sẽ được cập nhật trong ứng dụng trong vòng 5 phút, mà không cần khởi động lại.

## Các thực hành tốt nhất và cân nhắc

Tuân theo các thực hành tốt nhất sau để quản lý cấu hình trong .NET:

- **Phân tách môi trường**: Sử dụng các đường dẫn riêng cho từng môi trường để duy trì sự tách biệt rõ ràng.
- **Quyền tối thiểu**: Đảm bảo rằng các IAM roles chỉ có quyền cần thiết tối thiểu để truy cập Parameter Store và Secrets Manager.
- **Mã hóa**: Sử dụng AWS Key Management Service (AWS KMS) keys để mã hóa dữ liệu nhạy cảm.
- **Xử lý lỗi**: Thêm cơ chế xử lý lỗi mạnh mẽ cho các tình huống tải cấu hình thất bại.
- **Bộ nhớ đệm**: Cân nhắc triển khai lớp caching cho các giá trị được truy cập thường xuyên nhưng ít thay đổi để giảm số lần gọi API.
- **Theo dõi kiểm toán**: Kích hoạt AWS CloudTrail để lưu trữ nhật ký truy cập tham số và secrets.

## Dọn dẹp

Để tránh chi phí phát sinh liên tục và duy trì môi trường AWS sạch sẽ, hãy thực hiện các bước sau để xóa các tài nguyên đã tạo:

### Xóa các tham số trong Parameter Store:

1. Mở AWS Systems Manager console.
2. Trong bảng điều hướng, chọn Parameter Store.
3. Trên tab My parameters, chọn ô kiểm bên cạnh từng tham số cần xóa.
4. Chọn Delete.
5. Trong hộp thoại xác nhận, chọn Delete parameters.

### Xóa các secrets trong Secrets Manager:

1. Mở AWS Secrets Manager console.
2. Trong danh sách secrets, chọn secret bạn muốn xóa.
3. Trong phần Secret details, chọn Actions, sau đó chọn Delete secret.
4. Trong hộp thoại Disable secret and schedule deletion, tại mục Waiting period, nhập số ngày chờ trước khi xóa vĩnh viễn. Secrets Manager sẽ thêm một trường gọi là DeletionDate và đặt giá trị là ngày giờ hiện tại cộng với số ngày đã chỉ định cho recovery window.
5. Chọn Schedule deletion.

## Kết luận

Cách tiếp cận này mang lại một phương pháp mạnh mẽ, an toàn và linh hoạt để quản lý cấu hình trong các ứng dụng .NET sử dụng các dịch vụ AWS. Bằng cách tận dụng kết hợp Parameter Store và Secrets Manager, bạn có thể tập trung quản lý cấu hình, xử lý an toàn thông tin nhạy cảm, cập nhật cấu hình động mà không cần khởi động lại ứng dụng, và duy trì sự tách biệt rõ ràng giữa các môi trường. Sự tích hợp này cung cấp một giải pháp vững chắc cho việc quản lý cài đặt ứng dụng và secrets trong bối cảnh cloud-native, đồng thời nâng cao cả bảo mật lẫn hiệu quả vận hành. Để tìm hiểu thêm, xem [Referencing AWS Secrets Manager secrets từ Parameter Store parameters](https://docs.aws.amazon.com/systems-manager/latest/userguide/integration-ps-secretsmanager.html) trong Systems Manager User Guide.

---

## Tác giả

![](../../../images/3-Blog/Blog-3/img2.png)

### Raghavender Madamshitti

Raghavender Madamshitti là Lead Consultant tại AWS Professional Services, người mang đến chuyên môn về hiện đại hóa các workload .NET và xây dựng các giải pháp dựa trên đám mây trên AWS.

![](../../../images/3-Blog/Blog-3/img3.png)

### Mahesh Kumar Vemula

Mahesh Kumar Vemula là Lead Consultant tại AWS Professional Services. Anh là một người đam mê serverless, giúp khách hàng hiện đại hóa các workload .NET bằng các giải pháp dựa trên đám mây.

![](../../../images/3-Blog/Blog-3/img4.png)

### Sandeep Tammisetty

Sandeep Tammisetty là Lead Consultant tại AWS Professional Services. Anh giúp khách hàng di chuyển và hiện đại hóa các workload .NET lên AWS bằng các giải pháp dựa trên đám mây.
