---
id: app-options
title: Bravestars.Auth.AppOptions
sidebar_label: AppOptions
---
## Mô tả
Lớp chứa thông tin khởi tạo kết nối với Server và các tùy chọn
## Thông tin chi tiết
### Contructors và Destructors
```
//Khởi tạo AppOptions
AppOptions()
```

### Properties
```
//Id của app
public string appId

//Mã bí mật của app
public string secretKey

//Quy định request time out, đơn vị ms
//Giá trị mặc định là 10000ms
public int RequestTimeOut

//Quy định chế độ của app
//Có thể là Production, Development, Local
public AppMode Mode
```

### Public functions