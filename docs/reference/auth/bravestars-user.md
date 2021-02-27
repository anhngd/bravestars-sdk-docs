---
id: bravestars-user
title: Bravestars.Auth.BravestarsUser
sidebar_label: BravestarsUser
---
## Mô tả
Đối tượng tài khoản người dùng
## Thông tin chi tiết
### Properties
```csharp
//id của người dùng
public string Id

//tên tài khoản
public string UserName

//tên tài khoản bình thường hóa
public string NormalizedUserName
...
```
### Public functions
```csharp
//Thay đổi Username của người dùng
public Task UpdateUsernameAsync(string username)

//Đổi mật khẩu của người dùng
public Task ChangePasswordAsync(string oldPassword, string newPassword)
```