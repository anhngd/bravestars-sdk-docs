---
id: retrieve_data
title: Dịch vụ lấy dữ liệu của Config và User
sidebar_label: Dịch vụ lấy dữ liệu config và người chơi
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/retrieve_data.md
---

## Dịch vụ truy xuất dữ liệu Config

### Trước khi bắt đầu

Trước khi sử dụng dịch vụ Data Service, bạn cần phải thêm thư viện Bravestars Data Plugin vào Unity Project

> - Tải thư viện Bravestars Data
> - Assets > Import Package > Custom Package

### Truy xuất dữ liệu

Để đọc dữ liệu từ cơ sở dữ liệu, bạn cần 1 phiên bản DataHelpers

```C#
using Bravestars.SDK;
using Bravestars.SDK.Data;

public class MyScript: MonoBehaviour {
  void Start() {
    Bravestars.Auth.AppInfo appInfo = new AppInfo("appId","secretKey");
    Bravestars.Auth.AppClient appClient = new AppClient(appInfo); 
    DataHelpers helpers = new DataHelpers(appClient);
  }
}
```

### Lấy dữ liệu config 1 lần

Bạn sử dụng phương thức ``LoadConfig`` để
lấy dữ liệu Config.

```C#
string gameId = '1';
string key = 'Cfg_Arena';
ConfigRequest request = new ConfigRequest(gameId, key);
ConfigResponse response = helpers.LoadConfig(request);
```

### Lấy tất cả dữ liệu config 1 lần

Bạn sử dụng phương thức ``LoadAllConfig`` để lấy tất cả dữ liệu Config

```C#
string gameId = '1';
ConfigRequest request = new ConfigRequest(gameId);
ConfigResponse response = helpers.LoadAllConfig(request);
```

### Lấy dữ liệu user 1 lần

Bạn sử dụng phương thức ``LoadUserData`` để
lấy dữ liệu User.

```C#
string gameId = '1';
string userId = '1';
string key = 'Arena';
UserDataRequest request = new UserDataRequest(userId, gameId, key);
UserDataResponse response = helpers.LoadUserData(request);
```

### Lấy tất cả dữ liệu của 1 user 1 lần

Bạn sử dụng phương thức ``LoadAllUserData`` để
lấy tất cả dữ liệu của 1 User.

```C#
string gameId = '1';
string userId = '1';
UserDataRequest request = new UserDataRequest(userId, gameId);
UserDataResponse response = helpers.LoadUserData(request);
```
