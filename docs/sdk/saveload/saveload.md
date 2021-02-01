---

id: saveload

title: Dịch vụ Save Load Config và UserData

sidebar_label: Dịch vụ Save Load

custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/saveload.md

---

# Save Load Service Document

## Save Load Services API

### **Purpose:**

- Load Configs for events, game system.
- Save/Load User Data.
  
### **Public Constructors:**

DataHelpers(string ApiUrl)

### **Public Methods:**

#### **GetConfigUrl(ConfigRequest request, bool getAll = false)**

- Get Api Config Url to get a key or list key.
- Method: GET
- Note: getAll = true get list keys by game, getAll = false get a key.
  
#### **GetUserDataUrl(UserDataRequest request, bool getAll = false)**

- Get Api User Data Url to get a key or list keys.
- Method: GET
- Note: getAll = true get list keys by game and user, getAll = false get a key.
  
#### **SaveOrUpdateConfigUrl()**

- Get Api Config Url to save or update value.
- Method: POST
  
#### **PostConfigRequest(ConfigRequest request)**

- Get body raw to post (include compress value to decrease size of bytes).
  
#### **SaveOrUpdateUserDataUrl()**

- Get Api UserData Url to save or update value.
- Method: POST
  
#### **PostUserDataRequest(UserDataRequest request)**

- Get body raw to post (include compress value to decrease size of bytes).

#### **GetConfigResponse(string result)**

- Convert result of api to object result (include decompress value).

#### **GetUserDataResponse(string result)**

- Convert result of api to object result (include decompress value).

### Models

#### **ConfigRequest**

- string gameId
- string key
- string value  
  Constructors:
  1. ConfigRequest(string gameId, string key)
  2. ConfigRequest(string gameId, string key, string value)

#### **ConfigResponse**

- string gameId
- string key
- string value

#### **ListConfigResponse**

- List(ConfigResponse) items

#### **UserDataRequest**

- string userId
- string gameId
- string key
- string value  
  Constructors:
  1. UserDataRequest(string userId, string gameId, string key)
  2. UserDataRequest(string userId, string gameId, string key, string value)

#### **UserDataResponse**

- string userId
- string gameId
- string key
- string value
  
#### **ListUserDataResponse**

- List(UserDataResponse) items
