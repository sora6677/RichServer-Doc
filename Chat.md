## 功能: verifyUser 驗證 User 登入是否合法

```bash
- request:
  string accessToken 待驗證的 Token
```

```bash
- response:
  int error 0: 成功, -1: Token 錯誤

  case error == 0:
    string userId 玩家ID
    string userName 玩家名稱/暱稱
```

## 功能: getPublicChatList 取得公共聊天室列表

```bash
- request:
```

```bash
- response:
  int error 0: 成功

  case error == 0:
    string[] chatIdList chatId列表
```

## 功能: getJoinedChatList 取得玩家聊天室列表

```bash
- request:
  string userId 玩家ID
```

```bash
- response:
  int error 0: 成功, -1: userId不存在

  case error == 0:
    string[] chatIdList chatId列表
```

## 功能: getChat 取得聊天室資訊

```bash
- request:
  string chatId 聊天室ID
```

```bash
- response:
  int error 0: 成功, -1: chatId不存在

  case error == 0:
    string notice 公告訊息
    string[] userIdList userId列表
```

## 功能: isChatExist 檢查聊天室 ID 是否可用

```bash
- request:
  string chatId 聊天室ID
```

```bash
- response:
  int error 0: 成功, -1: chatId重複
```

## 功能: createChat 建立聊天室

```bash
- request:
  string chatId 聊天室ID
```

```bash
- response:
  int error 0: 成功, -1: chatId重複
```

## 功能: dismissChat 解散聊天室

```bash
- request:
  string chatId 聊天室ID
```

```bash
- response:
  int error 0: 成功, -1: chatId不存在
```

## 功能: joinChat 加入聊天室

```bash
- request:
  string chatId 聊天室ID
  string userId 玩家ID
```

```bash
- response:
  int error 0: 成功, -1: chatId不存在, -2: userId不存在
```

## 功能: leaveChat 離開聊天室

```bash
- request:
  string chatId 聊天室ID
  string userId 玩家ID
```

```bash
- response:
  int error 0: 成功, -1: chatId不存在, -2: userId不存在
```

## 功能: sendChatMessage 新增聊天室訊息

```bash
- request:
  string from 訊息發送者ID
  string to 訊息接收者ID
  int toType: 0: user 玩家, 1: group 群組
  string messageId 訊息ID
  int messageType: 0: text 文字, 1: image 影像, 2: video 影片, 3: audio 語音
  int64 timestamp 訊息時間戳

  case messageType == 0:
    string text 訊息文字
```

```bash
- response:
  int error 0: 成功, -1: from不存在, -2: to不存在, -3: messageId重複

  case messageType == 1:
  case messageType == 2:
  case messageType == 3:
    string uploadUrl 供上傳的網址
```
