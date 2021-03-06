---
id: facebook-signin
title: Xác thực qua Facebook Login và Unity
sidebar_label: Đăng nhập bằng Facebook
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/facebook-signin.md
---
## Trước khi bắt đầu
Trước khi có thể sử dụng BSG Authentication, bạn cần phải thêm BSG SDK vào Unity project của bạn
>Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)
## Truy cập lớp **Bravestars.Auth.BravestarsAuth**
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
## Xác thực
Sau khi người dùng đăng nhập qua Facebook thành công, hãy sử dụng accesstoken để lấy một [Credential](../../reference/auth/credential.md) và xác thực bằng nó, ví dụ:
```csharp
Bravestars.Auth.Credential credential =
    Bravestars.Auth.FacebookAuthProvider(facebookAccessToken);
auth.SignInWithCredentialAsync(credential);
```
## Bước kế tiếp
Sau khi người dùng được xác thực, bạn có thể sử dụng thông tin người dùng đơn giản thông qua đối tượng **[Bravestars.Auth.BravestarsUser](../../reference/auth/bravestars-user.md)**
```csharp
Bravestars.Auth.BravestarsUser user = auth.CurrentUser;
if(user != null)
{
    string name = user.UserName;
    string email = user.Email;
    string id = user.Id;
}
```