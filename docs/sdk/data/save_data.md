---
id: save_data
title: Dịch vụ lưu dữ liệu người chơi
sidebar_label: Dịch vụ lưu dữ liệu người chơi
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/save_data.md
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

### Lưu trữ dữ liệu người chơi

Bạn sử dụng phương thức ``SaveOrUpdateUserData`` để
 lưu trữ dữ liệu người chơi

```C#
string key = 'Arena';
string value = '{\'Key\':\'ABC\',\'Value\':\'123456\'}';
UserDataRequest request = new UserDataRequest(key, value);
try {
  UserDataResponse response = helpers.SaveOrUpdateUserData(request);
} catch (ApiException ex) {
  Debug.Log(ex);
}
```

### Chú ý

Tham số cuối cùng của UserDataRequest phải là 1 chuỗi Json String hợp lệ.
Trước khi truyền tham số cuối cùng của UserDataRequest, bạn nên sử dụng JsonUtility.ToJson() để chuyển hóa object sang raw Json.
