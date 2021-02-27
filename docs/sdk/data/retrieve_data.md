---
id: retrieve_data
title: Dịch vụ lấy dữ liệu của Config và User
sidebar_label: Dịch vụ lấy dữ liệu config và người chơi
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/retrieve_data.md
---

## Dịch vụ truy xuất dữ liệu Config

### Trước khi bắt đầu

Trước khi sử dụng dịch vụ Data Service, bạn cần phải thêm BSG SDK vào Unity project của bạn

> Tìm hướng dẫn chi tiết ở [đây](../get-started/setup.md)

### Truy xuất dữ liệu

Để đọc dữ liệu từ cơ sở dữ liệu, bạn cần 1 phiên bản DataHelpers

```C#
using Bravestars.SDK;
using Bravestars.SDK.Data;

public class MyScript: MonoBehaviour {
  void Start() {
    Bravestars.Auth.AppOptions appOptions = new AppOptions(){appId = "appId", secretKey = "secretKey"};
    Bravestars.Auth.AppClient appClient = new AppClient(appOptions); 
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
try {
  ConfigResponse response = helpers.LoadConfig(request);
} catch (ApiException ex) {
  Debug.Log(ex);
}
```

### Lấy tất cả dữ liệu config 1 lần

Bạn sử dụng phương thức ``LoadAllConfig`` để lấy tất cả dữ liệu Config

```C#
string gameId = '1';
ConfigRequest request = new ConfigRequest(gameId);
try {
  List<ConfigResponse> response = helpers.LoadAllConfig(request);
} catch (ApiException ex) {
  Debug.Log(ex);
}

```

### Lấy dữ liệu user 1 lần

Bạn sử dụng phương thức ``LoadUserData`` để
lấy dữ liệu User.

```C#
string gameId = '1';
string userId = '1';
string key = 'Arena';
UserDataRequest request = new UserDataRequest(userId, gameId, key);
try {
  UserDataResponse response = helpers.LoadUserData(request);
} catch (ApiException ex) {
  Debug.Log(ex);
}
```

### Lấy tất cả dữ liệu của 1 user 1 lần

Bạn sử dụng phương thức ``LoadAllUserData`` để
lấy tất cả dữ liệu của 1 User.

```C#
string gameId = '1';
string userId = '1';
UserDataRequest request = new UserDataRequest(userId, gameId);
try {
  List<UserDataResponse> response = helpers.LoadUserData(request);
} catch (ApiException ex) {
  Debug.Log(ex);
}
```
