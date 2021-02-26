---
id: app-client
title: Bravestars.Auth.AppClient
sidebar_label: AppClient
---
## Mô tả
Đối tượng client
## Thông tin chi tiết
### Contructors và Destructors
```
//Khởi tạo AppClient với các thông tin trong đối tượng AppOptions
AppClient(AppOptions appOptions)
```

### Properties
```
//Access token được Identity server cung cấp
public readonly string AccessToken;
```

### Public functions
```csharp
//Gửi request với sự ủy quyền từ client
public string SendHttpRequestWithAuthorization(HttpRequestMessage requestMessage, Object content)

//Ping tới open api để kiểm tra server có hoạt động không
public bool CheckOpenApiServer()
```