# 使用指南

## 快速开始

### 完整流程：获取指定用户的推文

```bash
# 1. 安装依赖
bun install

# 2. 获取用户信息（只需要 username）
bun run scripts/index.ts

# 3. 关注用户
bun run scripts/batch-follow.ts

# 4. 获取推文（你的首页时间线）
bun run scripts/fetch-tweets.ts
```

### 解释

- **`dev-accounts.json`**：只需要 `username` 字段，其他字段（`id`, `description`, `tags`）是为了方便阅读，脚本实际不使用
- **`accounts/` 目录**：存放获取到的用户完整信息，包含 `restId`
- **`batch-follow.ts`**：读取 `accounts/` 目录，关注所有用户
- **`fetch-tweets.ts`**：获取你**已关注用户**的首页推文

### 添加新用户

1. 编辑 `dev-accounts.json`，添加用户：
```json
{
  "username": "nytimes",
  "twitter_url": "https://x.com/nytimes",
  "description": "纽约时报",
  "tags": ["新闻"],
  "id": "52896925"
}
```

2. 运行脚本：
```bash
bun run scripts/index.ts        # 获取用户信息
bun run scripts/batch-follow.ts # 关注用户
bun run scripts/fetch-tweets.ts # 获取推文
```

### 自动运行

推送到 GitHub 后，GitHub Actions 会每天自动运行。

### 查看数据

- 用户信息：`accounts/` 目录
- 推文数据：`tweets/` 目录（按日期命名）
