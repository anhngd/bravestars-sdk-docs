---
id: facebook-signin
title: Xác thực qua Facebook Login và Unity
sidebar_label: Đăng nhập bằng Facebook
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/facebook-signin.md
---
## Trước khi bắt đầu
Trước khi có thể sử dụng Bravestars Authentication, bạn cần phải thêm Bravestars SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Truy cập lớp **Bravestars.Auth.BravestarsAuth**
Lớp BravestarsAuth là gateway cho tất cả lệnh gọi API. Nó có thể được truy cập thông qua ví dụ sau:
```csharp
Bravestars.Auth.AppInfo appInfo = new AppInfo("appId","secretKey");
Bravestars.Auth.AppClient appClient = new AppClient(appInfo); 

Bravestars.Auth.BravestarsAuth auth = new BravestarsAuth();
auth.GetApp(appClient);
```

## Xác thực
Sau khi người dùng đăng nhập qua Facebook thành công, hãy sử dụng accesstoken để lấy một Credential và xác thực bằng nó, ví dụ:
```csharp
Bravestars.Auth.Credential credential =
    Bravestars.Auth.FacebookAuthProvider(facebookAccessToken);
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