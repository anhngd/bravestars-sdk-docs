---
id: get-started
title: Bắt đầu
sidebar_label: Bắt đầu
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/get-started.md
---

## Bắt đầu với BSG Authentication trên Unity
BSG Authentication hiện tại cho phép người dùng đăng nhập vào trò chơi bằng nhiều phương thức đăng nhập, bao gồm:
- Đăng nhập bằng **Facebook**/**Google**.
- Đăng nhập bằng **username** và **mật khẩu**.
- Xác thực ẩn danh.

Hướng dẫn sau đây chỉ cách tạo tài khoản người dùng bằng username và mật khẩu.
## Trước khi bắt đầu
Trước khi có thể sử dụng BSG Authentication, bạn cần phải thêm BSG SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Đăng ký người dùng mới
Tạo form cho phép người dùng mới đăng ký trò chơi của bạn bằng username và mật khẩu của họ. Khi người dùng hoàn thành form, hãy xác thực thông tin người dùng gửi lên và chuyển chúng đến phương thức
 **CreateUserWithUsernameAndPasswordAsync**
```csharp
auth.CreateUserWithUsernameAndPasswordAsync(username, password);
```

[comment]: <> (## Đăng nhập cho người dùng có tài khoản)

[comment]: <> (Tạo một form cho phép người dùng sử dụng username, mật khẩu của họ đăng nhập vào trò chơi. Khi họ đã hoàn thành form, hãy gọi đến phương thức **SignInWithUsernameAndPasswordAsync**)

[comment]: <> (```csharp)

[comment]: <> (auth.SignInWithUsernameAndPasswordAsync&#40;username, password&#41;;)

[comment]: <> (```)
## Kế tiếp
Tìm hiểu cách thêm hỗ trợ cho các nhà cung cấp danh tính khác và tài khoản khách ẩn danh:
- [Quản lý người dùng](sdk/auth/manage-users.md)
- [Đăng nhập bằng Google](sdk/auth/google-signin.md)
- [Đăng nhập bằng Facebook](sdk/auth/facebook-signin.md)
- [Xác thực Ẩn danh](sdk/auth/anonymous-authentication.md)
