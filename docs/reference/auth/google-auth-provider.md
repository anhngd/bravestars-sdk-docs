---
id: google-auth-provider
title: Bravestars.Auth.GoogleAuthProvider
sidebar_label: GoogleAuthProvider
---
## Mô tả
Sử dụng mã Id token và access token do Google cung cấp để xác thực.
## Thông tin chi tiết
### Public functions
```csharp
//Lấy chứng chỉ của google
public static Credential GetCredential(string accessToken, string idToken)
```