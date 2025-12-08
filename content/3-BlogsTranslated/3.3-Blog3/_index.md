---
title: "Blog 3"
date: "2025-12-07"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Dynamic configuration updates in .NET using Parameter Store and Secrets Manager

Loading configuration and secrets in .NET applications is a common task. However, this comes with challenges in secure storage and flexible access without requiring application restarts.

AWS Systems Manager Parameter Store provides a centralized solution for storing and managing configuration data and sensitive information. This blog explores an advanced approach to managing them in .NET applications, focusing on:

- Referencing AWS Secrets Manager secrets through Parameter Store
- Loading configuration from both Parameter Store and Secrets Manager
- Implementing automatic configuration reloading without application restarts

## Solution Overview

You can retrieve secrets stored in Secrets Manager directly from Parameter Store using the following format:

```
/aws/reference/secretsmanager/<secret-path>
```

By following this format, Systems Manager understands it needs to retrieve the secret from Secrets Manager instead of Parameter Store.

For example, to reference a secret named `dev/DbPassword`, you would use:

```
/aws/reference/secretsmanager/dev/DbPassword
```

See [Referencing AWS Secrets Manager secrets from Parameter Store parameters](https://docs.aws.amazon.com/systems-manager/latest/userguide/integration-ps-secretsmanager.html) for more information.

This solution uses Parameter Store and Secrets Manager, combined with .NET configuration and IOptionsMonitor pattern, to address the following common configuration challenges:

- **Unified Access**: Use Parameter Store as the single access point for both configuration and Secrets Manager secrets.
- **Security**: Sensitive data is stored in Secrets Manager and referenced in Parameter Store, ensuring proper encryption and access control.
- **Dynamic Updates**: Implement automatic reloading of configuration values without application restarts.
- **Environment Separation**: Use hierarchical structure in Parameter Store to separate configuration by environment.

## Prerequisites

- AWS account with necessary permissions
- .NET 8 SDK

## Architecture

Consider an application running on an EC2 instance that needs to access both configuration parameters and sensitive secrets during operation. This application assumes an IAM role with necessary permissions and retrieves values from Parameter Store for both configuration data and secrets.

- When the application requests a configuration parameter, Parameter Store returns the value directly.
- If the parameter is a reference to a secret stored in Secrets Manager, Parameter Store retrieves the secret from Secrets Manager and returns it to the application.

![Figure 1: Solution architecture](../../../images/3-Blog/Blog-3/img1.png)

## Hands-on Guide

Let's explore how to retrieve configuration values from AWS services in the above application. The application needs to access two types of data:

- System parameters like Database Hostname and API Endpoint from Parameter Store
- Sensitive information like Database Password and API Key from Secrets Manager

In this guide, you'll build a .NET application capable of securely accessing configuration values from both AWS services.

### Step 1: Configure parameters and secrets

#### Store parameters in AWS Systems Manager

Set up parameters in AWS Systems Manager using the following hierarchical structure:

| Development Environment | Production Environment |
| ----------------------- | ---------------------- |
| /dev/DbHostname         | /prod/DbHostname       |
| /dev/ApiEndpoint        | /prod/ApiEndpoint      |

#### Store secrets in AWS Secrets Manager

Set up secrets in AWS Secrets Manager using the following hierarchical structure:

| Development Environment | Production Environment |
| ----------------------- | ---------------------- |
| /dev/DbPassword         | /prod/DbPassword       |
| /dev/ApiKey             | /prod/ApiKey           |

#### Create IAM Role to access configuration parameters and secrets

To access parameters and secrets, you need to create an IAM Role with the following permissions. This role grants necessary permissions to access required resources.

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

### Step 2: Set up .NET Application

#### Configure AWS Services Extension

Create two extension methods to configure AWS services as follows.

The following extension method adds application configuration from Parameter Store based on the provided path.

```csharp
public static void AddParameterStoreConfiguration(this WebApplicationBuilder builder)
{
    var configuration = builder.Configuration;

    // Retrieve current environment (e.g., /dev, /prod)
    var appSettingsPath = configuration["Environment"];

    configuration.AddSystemsManager(options =>
    {
        options.Path = appSettingsPath;
        options.ReloadAfter = TimeSpan.FromMinutes(5); // Reloads every 5 minutes
    });
}
```

The following extension method adds configuration from Secrets Manager using the Systems Manager reference path.

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

For local testing, please configure your `appSettings.json` file as follows.

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

A model is used to bind configuration values from Secrets Manager and Parameter Store. Add the following two classes to your project:

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

#### Startup Configuration

Register AWS services configuration and necessary configuration for IOptionsMonitor during startup:

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

#### Using Dynamic Configuration

Use `IOptionsMonitor<T>` to access the latest configuration values and react to changes. This approach provides flexibility in refreshing secrets without redeployment or application restarts.

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

### How It Works

Here's how the application retrieves values from Secrets Manager and Parameter Store:

1. When the application starts, it loads configuration from Parameter Store for the specified environment.
2. The application loads both configuration and secrets (using reference path) directly from Parameter Store.
3. AWS SDK for .NET automatically resolves these references, retrieving the actual secret values from Secrets Manager.
4. Configuration is reloaded every 5 minutes (as set in ReloadAfter).
5. `IOptionsMonitor<T>` ensures the application always uses the latest configuration values.
6. Any changes to parameters in Parameter Store or secrets in Secrets Manager will be updated in the application within 5 minutes, without requiring a restart.

## Best Practices and Considerations

Follow these best practices for managing configuration in .NET:

- **Environment Separation**: Use separate paths for each environment to maintain clear separation.
- **Least Privilege**: Ensure IAM roles only have the minimum necessary permissions to access Parameter Store and Secrets Manager.
- **Encryption**: Use AWS Key Management Service (AWS KMS) keys to encrypt sensitive data.
- **Error Handling**: Add robust error handling for configuration loading failure scenarios.
- **Caching**: Consider implementing a caching layer for frequently accessed but rarely changed values to reduce API calls.
- **Audit Logging**: Enable AWS CloudTrail to log parameter and secret access.

## Cleanup

To avoid ongoing costs and maintain a clean AWS environment, perform the following steps to delete created resources:

### Delete parameters in Parameter Store:

1. Open the AWS Systems Manager console.
2. In the navigation panel, choose Parameter Store.
3. On the My parameters tab, select the checkbox next to each parameter to delete.
4. Choose Delete.
5. In the confirmation dialog box, choose Delete parameters.

### Delete secrets in Secrets Manager:

1. Open the AWS Secrets Manager console.
2. In the secrets list, choose the secret you want to delete.
3. In the Secret details section, choose Actions, then choose Delete secret.
4. In the Disable secret and schedule deletion dialog box, under Waiting period, enter the number of days to wait before permanent deletion. Secrets Manager adds a field called DeletionDate and sets the value to the current date and time plus the specified number of days for the recovery window.
5. Choose Schedule deletion.

## Conclusion

This approach provides a robust, secure, and flexible method for managing configuration in .NET applications using AWS services. By leveraging the combination of Parameter Store and Secrets Manager, you can centrally manage configuration, securely handle sensitive information, update configuration dynamically without application restarts, and maintain clear separation between environments. This integration provides a solid solution for managing application settings and secrets in a cloud-native context, while enhancing both security and operational efficiency. To learn more, see [Referencing AWS Secrets Manager secrets from Parameter Store parameters](https://docs.aws.amazon.com/systems-manager/latest/userguide/integration-ps-secretsmanager.html) in the Systems Manager User Guide.

---

## Authors

![](../../../images/3-Blog/Blog-3/img2.png)

### Raghavender Madamshitti

Raghavender Madamshitti is Lead Consultant at AWS Professional Services, bringing expertise in modernizing .NET workloads and building cloud-based solutions on AWS.

![](../../../images/3-Blog/Blog-3/img3.png)

### Mahesh Kumar Vemula

Mahesh Kumar Vemula is Lead Consultant at AWS Professional Services. He is a serverless enthusiast, helping customers modernize .NET workloads with cloud-based solutions.

![](../../../images/3-Blog/Blog-3/img4.png)

### Sandeep Tammisetty

Sandeep Tammisetty is Lead Consultant at AWS Professional Services. He helps customers migrate and modernize .NET workloads to AWS with cloud-based solutions.
