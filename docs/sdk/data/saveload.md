---

id: saveload
title: Dịch vụ Save Load Config và UserData
sidebar_label: Dịch vụ Save Load
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/sdk/data/saveload.md

---

# Save Load Service Document

## Save Load Services API

### Purpose

- Load Configs for events, game system.
- Save/Load User Data.

### Server Enum

- PROD: production server
- DEV: testing server

### Public Constructors

DataHelpers(ServerEnum server))

### Public Methods

#### LoadConfig(ConfigRequest request)

- Input: ConfigRequest (string gameId, string key)
- Output: ConfigResponse (string gameId, string key, string value)
- Purpose: load config

#### LoadAllConfig(ConfigRequest request)

- Input: ConfigRequest (string gameId)
- Output: List\<ConfigResponse> (string gameId, string key, string value)
- Purpose: load all configs by gameId

#### LoadUserData(UserDataRequest request)

- Input: UserDataRequest (string gameId, string userId, string key)
- Output: UserDataResponse (string gameId, string userId, string key, string value)
- Purpose: load user data

#### LoadAllUserData(UserDataRequest request)

- Input: UserDataRequest (string gameId, string userId)
- Output: List\<UserDataResponse> (string gameId, string userId, string key, string value)
- Purpose: load all user data by gameId and userId

#### SaveUserData(UserDataRequest request)

- Input: UserDataRequest (string gameId, string userId, string key, string value)
- Output: UserDataResponse (string gameId, string userId, string key, string value)
- Purpose: save user data

### Models

#### ConfigRequest

- string gameId
- string key
- string value
  Constructors:
  1. ConfigRequest(string gameId)
  2. ConfigRequest(string gameId, string key)
  3. ConfigRequest(string gameId, string key, string value)

#### ConfigResponse

- string gameId
- string key
- string value

#### UserDataRequest

- string userId
- string gameId
- string key
- string value
  Constructors:
  1. UserDataRequest(string userId, string gameId)
  2. UserDataRequest(string userId, string gameId, string key)
  3. UserDataRequest(string userId, string gameId, string key, string value)

#### UserDataResponse

- string userId
- string gameId
- string key
- string value
