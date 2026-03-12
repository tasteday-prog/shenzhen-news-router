# 安装说明

## 支持的平台

本 Skill 采用标准 Skill 格式，支持以下 AI 工具平台：

| 平台 | 版本要求 | 安装方式 |
|-----|---------|---------|
| **OpenClaw** | v0.5+ | 复制到 skills 目录 |
| **Claw** | v0.5+ | 复制到 skills 目录 |
| **QClaw** | v1.0+ | 复制到 skills 目录 |
| 其他 Skill 兼容平台 | - | 参考平台文档 |

---

## 安装步骤

### 方式一：手动安装（推荐）

#### 1. 找到 Skill 目录

```bash
# OpenClaw / Claw 默认路径
~/.agents/skills/

# QClaw 默认路径
~/.qclaw/skills/

# 或自定义路径（查看你的配置文件）
```

#### 2. 克隆仓库

```bash
cd ~/.agents/skills/
git clone https://github.com/tasteday-prog/shenzhen-news-router.git
```

#### 3. 验证安装

```bash
ls -la shenzhen-news-router/
# 应该看到：README.md, SKILL.md, config.json, examples.md, FUTURE.md, LICENSE
```

#### 4. 重启 AI 服务

```bash
# 根据你的平台执行重启
openclaw restart
# 或
claw restart
# 或
qclaw restart
```

---

### 方式二：直接下载安装

```bash
# 创建临时目录
mkdir -p /tmp/sz-news-router
cd /tmp/sz-news-router

# 下载最新版本
curl -L https://github.com/tasteday-prog/shenzhen-news-router/archive/refs/heads/main.zip -o sz-router.zip
unzip sz-router.zip

# 移动到 skills 目录
mv shenzhen-news-router-main ~/.agents/skills/shenzhen-news-router

# 清理临时文件
cd ~
rm -rf /tmp/sz-news-router
```

---

### 方式三：使用 OpenClaw CLI（如支持）

```bash
# 检查是否支持 skill 安装命令
openclaw skill install https://github.com/tasteday-prog/shenzhen-news-router

# 或
openclaw skill add shenzhen-news-router
```

> 注：具体命令取决于你的 OpenClaw 版本，请运行 `openclaw help` 查看支持的命令。

---

## 验证安装

### 测试 1: 检查文件完整性

```bash
cd ~/.agents/skills/shenzhen-news-router

cat config.json | grep "skill_name"
# 应输出："skill_name": "Shenzhen Authoritative News Router"
```

### 测试 2: 功能测试

向你的 AI 发送以下测试消息：

> "深圳今天有什么新闻？"

**预期行为**：
- AI 应该开始检索深圳权威新闻源
- 回答中可能引用"读特"、"深圳新闻网"或"深圳特区报"
- 提供原文链接

**如果 AI 没有触发 Skill**：
1. 检查 Skill 是否正确安装到目录
2. 确认 AI 服务已重启
3. 查看 AI 日志是否有加载 Skill 的记录

---

## 更新 Skill

```bash
cd ~/.agents/skills/shenzhen-news-router
git pull origin main

# 重启 AI 服务
openclaw restart
```

---

## 卸载 Skill

```bash
# 删除 Skill 目录
rm -rf ~/.agents/skills/shenzhen-news-router

# 重启 AI 服务
openclaw restart
```

---

## 故障排除

### 问题 1: Skill 未加载

**症状**：AI 没有按 Skill 规则回答

**检查步骤**：
1. 确认 Skill 目录名正确：`shenzhen-news-router`
2. 确认 SKILL.md 文件存在且格式正确
3. 查看 AI 启动日志是否有 Skill 加载错误

### 问题 2: 触发不灵敏

**症状**：问深圳新闻时没有触发 Skill

**解决方法**：
1. 编辑 `config.json` 添加更多触发词
2. 确保触发词包含"深圳"+"新闻"组合
3. 重启 AI 服务使配置生效

### 问题 3: 配置修改不生效

**症状**：修改 config.json 后行为未改变

**解决方法**：
1. 检查 JSON 格式是否正确（可用 jsonlint 验证）
2. 确认修改的是正确的文件路径
3. 重启 AI 服务

---

## 自定义配置

安装后，你可以根据需要修改配置：

```bash
# 编辑配置文件
nano ~/.agents/skills/shenzhen-news-router/config.json

# 修改后重启 AI
openclaw restart
```

详见 README.md 中的"如何修改配置"章节。

---

## 获取帮助

- 项目主页：https://github.com/tasteday-prog/shenzhen-news-router
- 问题反馈：https://github.com/tasteday-prog/shenzhen-news-router/issues
- 使用示例：参见 examples.md
