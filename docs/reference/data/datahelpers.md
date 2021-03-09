---
id: data-helpers
title: Bravestars.SDK.Data.DataHelpers
sidebar_label: Data Helpers
---
## Mô tả

Lớp chứa khởi tạo dịch vụ data và các dịch vụ liên quan

### Contructors

``` Khởi tạo
public DataHelpers(AppClient appClient)
```

### Public functions

``` Các dịch vụ
// Giải nén chuối string
public static string Decompress(string s)
// Truy xuất 1 dữ liệu config trong game
public ConfigResponse LoadConfig(ConfigRequest request)
// Truy xuất 1 danh sách dữ liệu config trong game
public List<ConfigResponse> LoadAllConfig()
// Truy xuất 1 dữ liệu người chơi trong game
public UserDataResponse LoadUserData(UserDataRequest request)
// Truy xuất 1 danh sách dữ liệu của 1 người chơi trong game
public List<UserDataResponse> LoadAllUserData()
// Lưu trữ dữ liệu người chơi trong game 
public UserDataResponse SaveOrUpdateUserData(UserDataRequest request)
```
