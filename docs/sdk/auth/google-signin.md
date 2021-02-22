---
id: google-signin
title: Xác thực qua Google Sign-in và Unity
sidebar_label: Đăng nhập bằng Google
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/google-signin.md
---
## Trước khi bắt đầu
Trước khi có thể sử dụng BSG Authentication, bạn cần phải thêm BSG SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Truy cập lớp **Bravestars.Auth.BravestarsAuth**
Lớp BravestarsAuth là gateway cho tất cả lệnh gọi API. Nó có thể được truy cập thông qua ví dụ sau:
```csharp
Bravestars.Auth.AppInfo appInfo = new AppInfo("appId","secretKey");
Bravestars.Auth.AppClient appClient = new AppClient(appInfo); 

Bravestars.Auth.BravestarsAuth auth = new BravestarsAuth();
auth.GetApp(appClient);
```
>Để gọi API trong **môi trường Dev**, bạn cần khai báo đối tượng AppClient như sau
>
>```csharp
>Bravestars.Auth.AppClient appClient = new AppClient(appInfo, productionMode: false);
>```
## Xác thực
Sau khi người dùng đăng nhập qua Google thành công, hãy sử dụng accesstoken để lấy một Credential và xác thực bằng nó, ví dụ:
```csharp
Bravestars.Auth.Credential credential =
    Bravestars.Auth.GoogleAuthProvider(googleAccessToken, googleIdToken);
auth.SignInWithCredentialAsync(credential);
```
## Bước kế tiếp
Sau khi người dùng được xác thực, bạn có thể sử dụng thông tin người dùng đơn giản thông qua đối tượng **Bravestars.Auth.BravestarsUser**
```csharp
Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
if(user != null)
{
    string name = user.UserName;
    string email = user.Email;
    string id = user.Id;
}
```