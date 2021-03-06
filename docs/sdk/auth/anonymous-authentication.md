---
id: anonymous-authentication
title: Xác thực Ẩn danh
sidebar_label: Xác thực Ẩn danh
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/anonymous-authentication.md
---
Bạn có thể sử dụng Xác thực ẩn danh để xác thực các tài khoản ẩn danh tạm thời. Các tài khoản ẩn danh
tạm thời này có thể được sử dụng để cho phép người dùng chưa đăng ký ứng dụng của bạn làm việc với các dữ liệu được bảo vệ trong hệ thống.
## Trước khi bắt đầu
Trước khi có thể sử dụng BSG Authentication, bạn cần phải thêm BSG SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Xác thực ẩn danh
Lớp [BravestarsAuth](../../reference/auth/bravestars-auth.md) là gateway cho tất cả lệnh gọi API. Nó có thể được truy cập thông qua ví dụ sau:
```csharp
Bravestars.Auth.AppOptions appOptions = new AppOptions(){appId = "appId", secretKey = "secretKey"};
Bravestars.Auth.AppClient appClient = new AppClient(appOptions); 

Bravestars.Auth.BravestarsAuth auth = new BravestarsAuth();
auth.GetApp(appClient);
```
>Để cấu hình môi trường của app, bạn cần khai báo đối tượng [AppOptions](reference/auth/app-options.md) như sau
>
>```csharp
>Bravestars.Auth.AppOptions appOptions = new AppOptions(){
>   appId = "appId",
>   secretKey = "secretKey",
>   Mode = AppMode.Production,  //AppMode là một enum gồm các giá trị như Production, Development, Local
>                               //Quy định môi trường của app khi chạy
>                               //Giá trị mặc định là Production
>
>   RequestTimeOut = 10000      //Quy định thời gian tối đa request của api, đơn vị ms
>                               //Giá trị mặc định là 10000 ms 
>};
>```
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