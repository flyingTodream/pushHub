# 用户指南

> 🎉 **本应用完全免费** · 无订阅 · 所有功能永久免费使用

## 1. 下载 APP

### Android（华为）

**方式一：直接点击下载**

👉 [华为应用市场下载](https://appgallery.huawei.com/app/detail?id=com.xinhua.push&channelId=SHARE&source=appshare)

**方式二：扫码下载**

用华为手机的「浏览器」「微信」或「相机」扫描下方二维码即可跳转应用市场：

<p align="center">
  <img src="https://api.qrserver.com/v1/create-qr-code/?size=240x240&data=https%3A%2F%2Fappgallery.huawei.com%2Fapp%2Fdetail%3Fid%3Dcom.xinhua.push%26channelId%3DSHARE%26source%3Dappshare" alt="华为应用市场下载二维码" width="240" />
  <br/><sub><b>鸿蒙 / 华为</b></sub>
</p>

### iOS

**方式一：直接点击下载**

👉 [App Store 下载](https://apps.apple.com/cn/app/pushhub-%E7%A6%BB%E7%BA%BF%E9%80%9A%E7%9F%A5%E5%B9%B3%E5%8F%B0/id6785841579)

**方式二：扫码下载**

用 iPhone 的「相机」或「App Store」扫码即可跳转：

<p align="center">
  <img src="https://api.qrserver.com/v1/create-qr-code/?size=240x240&data=https%3A%2F%2Fapps.apple.com%2Fcn%2Fapp%2Fpushhub-%25E7%25A6%25BB%25E7%25BA%25BF%25E9%2580%259A%25E7%259F%25A5%25E5%25B9%25B3%25E5%258F%25B0%2Fid6785841579" alt="App Store 下载二维码" width="240" />
  <br/><sub><b>iOS</b></sub>
</p>

> 服务端默认地址在 APP 内已内置，用户无需手动填写。

## 2. 注册 / 登录

APP 端使用系统账号一键登录：

- **Android**：使用华为账号授权登录
- **iOS**：使用 Apple ID（Sign in with Apple）登录

首次登录会自动创建账号，无需输入用户名密码。

## 3. 接收推送

登录后请允许通知权限。若收不到推送，请按顺序检查：

1. 系统设置 → 通知 → 找到本 APP → 允许通知
2. APP 内「我的」→「设置」→ 确认「推送通知」开关已开启
3. 华为设备需确认「自启动」与「后台运行」权限已授予
4. iOS 设备需确认未开启「专注模式」

## 4. 给好友发消息

1. 在「好友」页面添加对方（需要对方的 apiToken / 二维码）
2. 进入好友对话，点击「发送消息」
3. 输入标题与正文，发送

对方设备会收到系统推送通知。

## 5. 加入群组

- 由群主邀请，或通过群组二维码加入
- 群消息会按 pushType 分类（聊天 / 订单 / 工作 / 订阅）

## 6. 消息管理

- **消息列表**：APP 内「消息」标签查看全部历史消息
- **删除消息**：单条左滑即可删除
- **清空消息**：「设置」→「清空消息列表」

## 7. 常见问题

### Q：换手机后还能收到以前的消息吗？
A：使用同一华为账号 / Apple ID 登录即可，历史消息会自动同步。

### Q：为什么有时候推送会延迟？
A：华为 / Apple 系统推送通道偶尔会有几秒延迟；若长期延迟，请检查 APP 是否被系统「省电策略」限制。

### Q：群消息能撤回吗？
A：当前版本不支持撤回，仅支持删除本地消息记录。

### Q：违规内容会被拦截吗？
A：会。服务端会自动检测违规内容与消息类型一致性，命中后会被拦截或标记。

### Q：我的推送 Token 泄漏了怎么办？
A：在 APP「我的」页面点击「刷新 Token」即可，旧 Token 立即失效。
