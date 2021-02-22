---
id: anonymous-authentication
title: Xác thực Ẩn danh
sidebar_label: Xác thực Ẩn danh
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/anonymous-authentication.md
---
Bạn có thể sử dụng Xác thực ẩn danh để xác thực các tài khoản ẩn danh tạm thời. Các tài khoản ẩn danh
tạm thời này có thể được sử dụng để cho phép người dùng chưa đăng ký ứng dụng của bạn làm việc với các dữ liệu được bảo vệ trong hệ thống.
## Trước khi bắt đầu
Trước khi có thể sử dụng Bravestars Authentication, bạn cần phải thêm Bravestars SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Xác thực ẩn danh
Lớp BravestarsAuth là gateway cho tất cả lệnh gọi API. Nó có thể được truy cập thông qua ví dụ sau:
```csharp
Bravestars.Auth.AppInfo appInfo = new AppInfo("appId","secretKey");
Bravestars.Auth.AppClient appClient = new AppClient(appInfo); 

Bravestars.Auth.BravestarsAuth auth = new BravestarsAuth();
auth.GetApp(appClient);
```
Gọi tới phương thức **Bravestars.Auth.BravestarsAuth.SignInAnonymouslyAsync** để hoàn tất xác thực
```csharp
auth.SignInAnonymouslyAsync(deviceId);

Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
if(user != null)
{
    string name = user.UserName;
    string email = user.Email;
    string id = user.Id;
}
```
>deviceId là mã của thiết bị, chúng tôi sử dụng nó để phân biệt các tài khoản ẩn danh với nhau.