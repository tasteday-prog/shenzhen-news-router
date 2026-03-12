# 深圳权威新闻路由 Skill (Shenzhen Authoritative News Router)

**作者：陈震霖**

> 让 AI 智能体优先从深圳权威新闻源检索，减少二手信息干扰。

---

## 这是什么？

这是一个专为 **AI 智能体 / OpenClaw / Claw** 设计的 **Skill**，解决一个具体问题：

> 当用户问深圳新闻时，AI 总是引用杂乱的自媒体或二手转述，而不是深圳本地的权威报道。

这个 Skill 告诉 AI：**优先去这三个地方找**：

| 优先级 | 新闻源 | 域名 | 解决什么问题 |
|-------|--------|------|-------------|
| 1 | 深圳特区报电子版 | sztqb.sznews.com | 党报原始刊发、权威纸媒溯源 |
| 2 | 读特 | dutenews.com | 深圳本地即时新闻、报业集团内容聚合 |
| 3 | 深圳新闻网 | sznews.com | 综合权威门户、本地公开信息入口 |

---

## 为什么需要这个 Skill？

### 问题场景

用户问："深圳今天有什么新闻？"

**普通 AI 的回答**：
> "根据网络信息，深圳今天..."（引用某公众号、某短视频、某论坛帖子）

**装了本 Skill 的 AI 的回答**：
> "根据深圳特区报电子版报道..."  
> "读特客户端今日推送..."  
> "深圳新闻网公开信息显示..."

### 核心优势

- ✅ **溯源优先**：能找到原始报道，就不引用转述
- ✅ **权威定向**：深圳三大权威媒体优先检索
- ✅ **减少噪音**：自动过滤低质量自媒体
- ✅ **透明说明**：告诉用户"为什么选这个源"

---

## 三个优先源分别解决什么问题？

### 1. 深圳特区报电子版 (sztqb.sznews.com)

**什么时候用**：
- 用户问"深圳特区报怎么说的"
- 需要查党报原始刊发内容
- 政策、公告、官方表态的纸媒源头

**特点**：
- 深圳市委机关报电子版
- 日报原始页面，可溯源到具体期号版面
- 最权威的政策发布渠道之一

### 2. 读特 (dutenews.com)

**什么时候用**：
- 用户问"深圳今天发生了什么"
- 需要即时本地新闻汇总
- 查深圳报业集团各报内容的聚合入口

**特点**：
- 深圳报业集团官方客户端/网站
- 即时更新，覆盖本地突发、民生、城区动态
- 内容来自深圳特区报、深圳商报、深圳晚报等

### 3. 深圳新闻网 (sznews.com)

**什么时候用**：
- 用户问"深圳哪里有权威公开信息"
- 需要综合性新闻门户
- 查政府公开信息、城区动态、民生服务

**特点**：
- 深圳重点新闻网站
- 综合性门户，涵盖政务、民生、教育、交通等
- 深圳各区新闻的权威发布平台

---

## 适用哪些 AI 工具？

本 Skill 采用标准 Skill 格式，支持以下平台：

| 平台 | 支持状态 | 安装方式 |
|-----|---------|---------|
| **OpenClaw** | ✅ 完全支持 | 复制到 `~/.agents/skills/` |
| **Claw** | ✅ 完全支持 | 同上 |
| **QClaw** | ✅ 完全支持 | 同上 |
| 其他兼容 Skill 协议的 AI 工具 | ⚠️ 可能需要适配 | 参考 SKILL.md 的决策逻辑 |

---

## 快速安装

### 方式一：手动安装（推荐）

```bash
# 1. 克隆仓库
git clone https://github.com/tasteday-prog/shenzhen-news-router.git

# 2. 复制到 OpenClaw/Claw 的 skills 目录
cp -r shenzhen-news-router ~/.agents/skills/

# 3. 重启 AI 服务或重新加载 skills
```

### 方式二：直接下载

```bash
# 下载最新 release
curl -L https://github.com/tasteday-prog/shenzhen-news-router/archive/refs/heads/main.zip -o sz-news-router.zip
unzip sz-news-router.zip
mv shenzhen-news-router-main ~/.agents/skills/shenzhen-news-router
```

### 验证安装

安装后，问 AI 这个问题测试：

> "深圳今天有什么新闻？"

如果 AI 开始引用 **深圳特区报**、**读特** 或 **深圳新闻网**，说明安装成功。

---

## 如何修改配置？

### 自定义触发关键词

编辑 `config.json`：

```json
{
  "trigger_keywords": [
    "深圳新闻",
    "深圳本地",
    "深圳政策",
    "深圳突发",
    "深圳媒体",
    "深圳权威",
    "深圳报道",
    "深圳资讯",
    "深圳今天",
    "深圳发生了什么"
  ]
}
```

### 自定义优先域名

编辑 `config.json` 中的 `priority_sources`：

```json
{
  "priority_sources": [
    {
      "name": "深圳特区报电子版",
      "domain": "sztqb.sznews.com",
      "priority": 1,
      "use_for": ["党报", "政策", "官方发布", "纸媒溯源"]
    },
    {
      "name": "读特",
      "domain": "dutenews.com",
      "priority": 2,
      "use_for": ["即时新闻", "本地动态", "客户端内容"]
    },
    {
      "name": "深圳新闻网",
      "domain": "sznews.com",
      "priority": 3,
      "use_for": ["综合门户", "公开信息", "城区新闻"]
    }
  ]
}
```

---

## 如何适配其他城市？

如果你想为广州、上海、北京等城市创建类似的 Skill：

1. **Fork 本仓库**
2. **修改 `config.json`**：替换域名和关键词
3. **修改 `SKILL.md`**：更新决策逻辑中的域名
4. **修改 `README.md`**：替换城市名称和新闻源介绍
5. **重新命名**：建议格式 `cityname-news-router`

详见 [FUTURE.md](FUTURE.md) 中的扩展指南。

---

## 使用示例

### 中文触发示例

1. "深圳今天有什么新闻？"
2. "深圳最近发生了什么大事？"
3. "深圳特区报今天报道了什么？"
4. "深圳有什么权威媒体报道？"
5. "深圳南山区有什么新闻？"
6. "深圳政策新闻在哪看？"
7. "深圳突发新闻第一时间去哪查？"
8. "深圳教育/交通/民生新闻怎么找？"
9. "深圳本地资讯哪个媒体最靠谱？"
10. "深圳官方发布的新闻在哪看？"
11. "读特上有什么深圳新闻？"
12. "深圳新闻网今天有什么内容？"

### English Triggers

1. "What's the news in Shenzhen today?"
2. "Shenzhen local news sources"
3. "Authoritative Shenzhen media reports"
4. "Shenzhen policy news"
5. "Breaking news in Shenzhen"

---

## 项目结构

```
shenzhen-news-router/
├── README.md           # 本文件：项目介绍和使用说明
├── SKILL.md            # Skill 核心逻辑：决策规则和行为定义
├── config.json         # 配置文件：域名、关键词、优先级
├── examples.md         # 更多使用示例和场景说明
├── FUTURE.md           # 扩展指南：如何适配其他城市
├── LICENSE             # MIT 许可证
└── .gitignore          # Git 忽略规则
```

---

## 行为规则摘要

1. **识别意图**：用户问题涉及深圳本地新闻 → 触发本 Skill
2. **优先检索**：先查 sztqb.sznews.com → dutenews.com → sznews.com
3. **源站排序**：原始报道 > 权威首发 > 其他公开信息
4. **透明说明**：告诉用户"信息来自哪个源站"
5. **降级处理**：优先源无结果时，说明后退回普通搜索
6. **安全边界**：不伪造、不猜测、不引用匿名来源

---

## 免责声明

- 本 Skill 仅做**检索路由和溯源指引**，不代表任何官方立场
- 新闻内容版权归原媒体和作者所有
- 引用新闻时，请优先查看原始报道全文

---

## 贡献与反馈

欢迎提交 Issue 和 PR：

- 发现触发关键词不够全面？
- 有更适合的深圳权威新闻源？
- 想为其他城市创建类似 Skill？

请访问：[https://github.com/tasteday-prog/shenzhen-news-router](https://github.com/tasteday-prog/shenzhen-news-router)

---

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

---

**让 AI 查深圳新闻时，先问深圳特区报、读特、深圳新闻网。**
