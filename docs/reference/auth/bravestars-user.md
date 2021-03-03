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

//email của tài khoản
public string Email

//Xác nhận email
public bool EmailConfirmed

//Xác nhận người dùng ẩn danh 
public bool IsAnonymous 

//Số điện thoại của tài khoản
public string PhoneNumber

//Xác nhận số điện thoại
public bool PhoneNumberConfirmed

//Thời gian tạo 
public DateTimeOffset? Created

//Thời gian chỉnh sửa 
public DateTimeOffset? Modifed
```
### Public functions
```csharp
//Thay đổi Username của người dùng
public Task UpdateUsernameAsync(string username)

//Đổi mật khẩu của người dùng
public Task ChangePasswordAsync(string oldPassword, string newPassword)
```