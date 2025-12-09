---
title: "Event 4"
date: "2025-11-29"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# 29/11/2025

# AWS IAM Security Best Practices

## Speaker Information

- **Huynh Hoang Long** - AWS Expert
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud Journey

## What is IAM?

IAM (Identity and Access Management) is AWS's identity and access management service, allowing management of **roles** with specific permissions assigned to specific **users**, enhancing system security.

**Key Components:**

- **Users**: Individual users
- **Groups**: User groups
- **Roles**: Roles with specific permissions
- **Policies**: Policies defining permissions

## IAM Best Practices

### 1. Principle of Least Privilege

**Don't grant excessive permissions**, only grant minimum necessary permissions.

- Reduce risk when account is compromised
- Limit damage if incidents occur
- Developers only need deploy permissions, not database deletion rights

### 2. Delete Root Access Keys

**Delete root access keys immediately after setup.**

- Root has the highest permissions
- Don't use root for daily work
- Store root credentials securely

### 3. Avoid Wildcards (\*)

**Don't use "\*"** as it grants full permissions.

```json
// Avoid
{"Action": "*", "Resource": "*"}

// Use instead
{"Action": ["s3:GetObject", "s3:PutObject"],
 "Resource": "arn:aws:s3:::my-bucket/*"}
```

### 4. Use AWS SSO

**AWS SSO instead of regular IAM users.**

- Credentials auto-reset (15 minutes - 36 hours)
- Enhanced security, centralized management

## Single Sign-On (SSO)

![Credentials Spectrum](/images/4-EventParticipated/7E18B68B-FAF5-48D7-8216-46DAE1FB7B90.jpeg)

**SSO** allows single login to access multiple systems.

**Benefits:**

- Easy management of multiple roles and accounts
- No need to login again when switching apps
- Activating SSO simultaneously activates AWS Organizations

## Multi-Factor Authentication (MFA)

![Multi-Factor Authentication (MFA)](/images/4-EventParticipated/312A5E8A-5CC2-4087-8D9C-B04BC59C5B03.jpeg)

**MFA** is an additional authentication step, protecting accounts even when passwords are compromised.

**Types:**

- Virtual MFA: Google/Microsoft Authenticator, Authy
- Hardware: YubiKey, Gemalto tokens
- SMS OTP (less secure)

**Best practices:** Mandatory MFA for all users, prioritize Virtual/Hardware MFA.

## Password Policies

**Strong password policies:**

- Length: 12-14 characters
- Complexity: Uppercase, lowercase, numbers, special characters
- Expiration: 60-90 days
- No reuse of last 5 passwords

## Service Control Policies (SCP)

**SCP** defines maximum permissions in account/OU.

- Doesn't grant permissions, only limits them
- Applied at AWS Organizations level
- Overrides all IAM policies

## Permission Boundaries

**Permission Boundaries** set maximum permission limits for IAM entities.

**Use cases:**

- Allow developers to create roles but not exceed boundary
- Prevent privilege escalation

## Credentials Rotation

**AWS Secrets Manager** auto-rotation:

1. Create new credentials
2. Test credentials
3. Apply to app
4. Delete old credentials

**Best practices:** Rotate access keys at least every 90 days, use IAM roles when possible.

## IAM Access Analyzer

![IAM Access Analyzer](/images/4-EventParticipated/AADDB3CC-6E5D-4B91-9DE2-28C7A00B915A.jpeg)

**IAM Access Analyzer** analyzes and monitors access permissions:

- Detects resources shared with external entities
- Validates policy syntax
- Suggests least-privilege policies

**Common findings:**

- Public/externally shared S3 buckets
- Externally accessible KMS keys
- IAM roles assumable from external accounts

## Key Takeaways

### About IAM Security

1. **Least Privilege**: Grant minimum permissions only
2. **No Root Keys**: Don't use root for daily work
3. **Avoid Wildcards**: Specify actions and resources clearly
4. **Enable MFA**: Mandatory for all users

### About Authentication

1. **AWS SSO**: Centralized management, auto-rotate credentials
2. **MFA**: Critical security layer
3. **Strong Passwords**: Complex, periodic rotation
4. **Temporary Credentials**: Prioritize IAM roles

### About Governance

1. **SCP**: Limit permissions at organization level
2. **Permission Boundaries**: Prevent privilege escalation
3. **Credentials Rotation**: Automated with Secrets Manager
4. **Access Analyzer**: Continuous monitoring

## Event Experience

Attending the **"AWS IAM Security Best Practices"** workshop helped me gain deep understanding of AWS security.

### Learning from Experts

- Long and Anh shared hands-on IAM experience
- Case studies about security incidents and prevention
- Best practices from large enterprises

### Important Insights

- **Least Privilege**: Mandatory requirement, not just theory
- **Defense in Depth**: Multiple security layers (MFA, SCP, Permission Boundaries)
- **Automation**: Auto credential rotation reduces risks

### Key Tools

- **AWS SSO**: Modern enterprise authentication
- **IAM Access Analyzer**: Audit and validate policies
- **Secrets Manager**: Automated credentials management

### Applying to Work

1. **Audit permissions**: Review and tighten policies
2. **Enable MFA**: Deploy for all users
3. **Setup SSO**: Migrate from IAM users
4. **Credential rotation**: Use Secrets Manager
5. **Access Analyzer**: Monitor security findings

> In conclusion, the workshop emphasized security mindset - least privilege, multiple security layers, and continuous monitoring.
