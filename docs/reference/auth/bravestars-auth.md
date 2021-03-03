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
//createNewAccount mặc định là true, có nghĩa là tự động tạo tài khoản nếu chưa tồn tại và ngược lại.
public Task<BravestarsUser> SignInWithCredentialAsync(Credential credential, bool createNewAccount = true)

//Đăng nhập ẩn danh
//createNewAccount mặc định là true, có nghĩa là tự động tạo tài khoản nếu chưa tồn tại và ngược lại.
public Task<BravestarsUser> SignInAnonymouslyAsync(string deviceId, bool createNewAccount = true)

//Giải mã chuỗi json và đưa về đối tượng BravestarsUser
public static BravestarsUser JsonDecodeToBravestarsUser(string raw)
```