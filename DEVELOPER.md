# 开发者指南

面向接入推送 API 的下游开发者。

> 🎉 **完全免费接入** · 无需付费 · 无需商业授权

## 1. 总览

| 接口 | 方法 | 说明 |
|------|------|------|
| `/push/:apiToken` | POST | 给指定用户发推送（华为设备） |
| `/push/ios/:apiToken` | POST | 给指定用户发推送（iOS 设备） |

## 2. 鉴权方式

调用推送接口只需在 URL 中带目标用户的 `apiToken`。`apiToken` 是用户唯一标识，长期有效，用户可在 APP「我的」页面复制或手动重置。

## 3. 调用示例

### 3.1 发送推送（华为设备）

```bash
curl -X POST https://your-server.com/push/<apiToken> \
  -H "Content-Type: application/json" \
  -d '{
    "title": "会议提醒",
    "body": "下午 3 点 4 楼会议室",
    "pushType": "work"
  }'
```

**字段说明**

| 字段 | 类型 | 必填 | 说明 |
|------|------|:----:|------|
| title | string | ✓ | 通知标题，最长 128 字符 |
| body | string | ✓ | 通知内容，最长 4096 字符 |
| pushType | string | - | 消息类型：`chat` / `order` / `work` / `subscription`，默认 `chat` |

### 3.2 发送推送（iOS 设备）

```bash
curl -X POST https://your-server.com/push/ios/<apiToken> \
  -H "Content-Type: application/json" \
  -d '{
    "title": "会议提醒",
    "body": "下午 3 点 4 楼会议室",
    "pushType": "work"
  }'
```

字段与华为端完全一致，服务端会根据目标用户的平台自动选择通道。

## 4. SDK 代码片段

### Node.js

```javascript
async function sendPush(apiToken, { title, body, pushType = 'chat' }) {
  const resp = await fetch(`https://your-server.com/push/${apiToken}`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title, body, pushType }),
  });
  return resp.json();
}
```

### Python

```python
import requests

def send_push(api_token, title, body, push_type='chat'):
    return requests.post(
        f"https://your-server.com/push/{api_token}",
        json={"title": title, "body": body, "pushType": push_type},
    ).json()
```

## 5. 限流策略

| 维度 | 限制 |
|------|------|
| `/push/:apiToken` | 每个 apiToken 每分钟 5 次、每天 20 次 |

超过限流返回 429，响应体中带 `Retry-After` 提示。

## 6. 内容审核机制

服务端会对所有推送内容做两层审核：

### 6.1 违规检测
- 基于语义相似度匹配违规样本库
- 命中后：默认标记（flagged），开启严格模式后拦截（返回 400）

### 6.2 类型一致性检测
- 比对内容与声明 pushType 的语义一致性
- 例如：内容明显是「订单」却声明 `chat` 会被拦截

## 7. 错误码

| HTTP | 含义 |
|------|------|
| 200 | 成功 |
| 400 | 参数错误 / 内容被拦截 |
| 403 | 目标用户已关闭推送 |
| 404 | 目标用户不存在或已禁用 |
| 429 | 限流 |
| 500 | 服务内部错误 |
| 502 | 上游推送服务（华为 / APNs）异常 |

## 8. 完整接口文档

更详细的字段、响应、错误码请访问 👉 [在线文档](https://push.199802.top/docs/push)
