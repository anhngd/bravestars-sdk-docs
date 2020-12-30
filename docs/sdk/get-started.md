---
id: get-started
title: Bắt đầu
sidebar_label: Bắt đầu
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/get-started.md
---

## Bắt đầu với Bravestars Authentication trên Unity
Bạn có thể sử dụng Bravestars Authentication để cho phép người dùng đăng nhập vào trò chơi của bạn bằng một hay nhiều phương thức đăng nhập, bao gồm đăng nhập bằng username và mật khẩu, hoặc sử dụng các nhà cung cấp danh tính như Google hay Facebook. Hướng dẫn này giúp bạn bắt đầu với xác thực với Bravestars Authentication bằng cách chỉ cho bạn cách thêm username và mật khẩu vào trò chơi của bạn
## Trước khi bắt đầu
Trước khi có thể sử dụng Bravestars Authentication, bạn cần phải thêm Bravestars SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở --link--
## Đăng ký người dùng mới
Tạo form cho phép người dùng mới đăng ký trò chơi của bạn bằng username và mật khẩu của họ. Khi người dùng hoàn thành form, hãy xác thực thông tin người dùng gửi lên và chuyển chúng đến phương thức
 **CreateUserWithUsernameAndPasswordAsync**
```csharp
auth.CreateUserWithUsernameAndPasswordAsync(username, password);
```
## Đăng nhập cho người dùng có tài khoản
Tạo một form cho phép người dùng sử dụng username, mật khẩu của họ đăng nhập vào trò chơi. Khi họ đã hoàn thành form, hãy gọi đến phương thức **SignInWithUsernameAndPasswordAsync**
```csharp
auth.SignInWithUsernameAndPasswordAsync(username, password);
```
## Kế tiếp
Tìm hiểu cách thêm hỗ trợ cho các nhà cung cấp danh tính khác và tài khoản khách ẩn danh:
- [Quản lý người dùng](sdk/manage-users.md)
- [Đăng nhập bằng Google](sdk/google-signin.md)
- [Đăng nhập bằng Facebook](sdk/facebook-signin.md)
- [Xác thực Ẩn danh](sdk/anonymous-authentication.md)
