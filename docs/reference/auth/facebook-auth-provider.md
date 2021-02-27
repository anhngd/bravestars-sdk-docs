---
id: facebook-auth-provider
title: Bravestars.Auth.FacebookAuthProvider
sidebar_label: FacebookAuthProvider
---
## Mô tả
Sử dụng access token do Facebook cung cấp để xác thực.
## Thông tin chi tiết
### Public functions
```csharp
//Khởi tạo đối tượng FacebookAuthProvider mặc định
public static FacebookAuthProvider DefaultInstance

//Lấy chứng chỉ của facebook provider
public static Credential GetCredential(string accessToken)
```