---
id: bravestars-auth
title: Bravestars.Auth.BravestarsAuth
sidebar_label: BravestarsAuth
---
## Mô tả
Đối tượng xác thực
## Thông tin chi tiết
### Contructors và Destructors
```
//Khởi tạo đối tượng BravestarsAuth
public BravestarsAuth()
```

### Properties
```csharp
//Đối tượng user đã được xác thực, mặc định là null
public BravestarsUser CurrentUser;
```

### Public functions
```csharp
//Đăng ký appClient
public BravestarsAuth GetApp(AppClient appClient)

//Tạo người dùng với tài khoản và mật khẩu
public Task CreateUserWithUsernameAndPasswordAsync(string username, string password)

//Đăng nhập với chứng chỉ
public Task<BravestarsUser> SignInWithCredentialAsync(Credential credential)

//Đăng nhập ẩn danh
public Task<BravestarsUser> SignInAnonymouslyAsync(string deviceId = null)

//Giải mã chuỗi json và đưa về đối tượng BravestarsUser
public static BravestarsUser JsonDecodeToBravestarsUser(string raw)
```