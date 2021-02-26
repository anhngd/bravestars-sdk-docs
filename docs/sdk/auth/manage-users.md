---
id: manage-users
title: Quản lý người dùng
sidebar_label: Quản lý người dùng
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/manage-users.md
---
## Tạo tài khoản người dùng mới
Bạn có thể tạo một tài khoản người dùng mới bằng cách gọi đến phương thức **CreateUserWithUsernameAndPasswordAsync** hoặc đăng nhập bằng **Facebook**, **Google**

## Lấy người dùng đang đăng nhập
Cách được đề xuất là lấy thông qua [BravestarsAuth](../../reference/auth/bravestars-auth.md) object
```csharp
Bravestars.Auth.BravestarsAuth auth;
Bravestars.Auth.BravestarsUser user;

if(auth.CurrentUser != null)
{
    user = auth.CurrentUser;
}
```
## Lấy thông tin người dùng
Để lấy thông tin người dùng, bạn hãy sử dụng accessor method của một instance **[BravestarsUser](../../reference/auth/bravestars-user.md)**
```csharp
Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
if(user != null)
{
    string name = user.UserName;
    string email = user.Email;
    string id = user.Id;
}
```

## Cập nhật username
Bạn có thể set username bằng phương thức **UpdateUsernameAsync**. Ví dụ:
```csharp
Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
if(user != null)
{
    user.UpdateUsernameAsync("new_username");
}
```
## Đổi mật khẩu người dùng
Bạn có thể thay đổi mật khẩu người dùng bằng phương thức **ChangePasswordAsync**. Ví dụ:
```csharp
Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
string newPassword = "Pa$$word123";
if(user != null)
{
    user.ChangePasswordAsync(oldPassword, newPassword);
}
```