# 扩展指南：多城市权威新闻源路由

**作者：陈震霖**

本文档说明如何将本 Skill 扩展到其他城市，以及未来的发展方向。

---

## 快速适配其他城市

### 步骤 1: Fork 本仓库

```bash
# Fork 到你自己的账号
git clone https://github.com/YOUR_USERNAME/cityname-news-router.git
cd cityname-news-router
```

### 步骤 2: 修改配置文件

编辑 `config.json`：

```json
{
  "skill_name": "Guangzhou Authoritative News Router",
  "skill_name_zh": "广州权威新闻路由",
  
  "priority_sources": [
    {
      "name": "广州日报",
      "domain": "gzdaily.dayoo.com",
      "priority": 1,
      "use_for": ["党报", "政策", "官方发布"]
    },
    {
      "name": "大洋网",
      "domain": "dayoo.com",
      "priority": 2,
      "use_for": ["即时新闻", "本地动态"]
    },
    {
      "name": "广州新闻网",
      "domain": "gznews.com",
      "priority": 3,
      "use_for": ["综合门户", "公开信息"]
    }
  ],
  
  "trigger_keywords": {
    "direct_triggers": ["广州新闻", "广州本地", "广州报道"],
    "district_triggers": ["天河新闻", "越秀新闻", "海珠新闻"]
  }
}
```

### 步骤 3: 更新文档

修改以下文件中的城市名称和新闻源介绍：

- `README.md`: 替换所有"深圳"为"广州"
- `SKILL.md`: 更新决策逻辑中的域名
- `examples.md`: 替换示例中的地名

### 步骤 4: 提交并发布

```bash
git add .
git commit -m "Adapt for Guangzhou: replace news sources and triggers"
git push origin main
```

---

## 主要城市参考配置

### 广州 (Guangzhou)

```json
{
  "priority_sources": [
    {"name": "广州日报", "domain": "gzdaily.dayoo.com", "priority": 1},
    {"name": "大洋网", "domain": "dayoo.com", "priority": 2},
    {"name": "广州文明网", "domain": "gz.wenming.cn", "priority": 3}
  ]
}
```

### 上海 (Shanghai)

```json
{
  "priority_sources": [
    {"name": "解放日报", "domain": "jfdaily.com", "priority": 1},
    {"name": "上观新闻", "domain": "shobserver.com", "priority": 2},
    {"name": "东方网", "domain": "eastday.com", "priority": 3}
  ]
}
```

### 北京 (Beijing)

```json
{
  "priority_sources": [
    {"name": "北京日报", "domain": "bjd.com.cn", "priority": 1},
    {"name": "北京晚报", "domain": "bjwb.bjd.com.cn", "priority": 2},
    {"name": "千龙网", "domain": "qianlong.com", "priority": 3}
  ]
}
```

### 杭州 (Hangzhou)

```json
{
  "priority_sources": [
    {"name": "杭州日报", "domain": "hzrb.hangzhou.com.cn", "priority": 1},
    {"name": "杭州网", "domain": "hangzhou.com.cn", "priority": 2},
    {"name": "都市快报", "domain": "dskb.hangzhou.com.cn", "priority": 3}
  ]
}
```

### 成都 (Chengdu)

```json
{
  "priority_sources": [
    {"name": "成都日报", "domain": "cdrb.chengdu.cn", "priority": 1},
    {"name": "锦观新闻", "domain": "jinguan.chengdu.cn", "priority": 2},
    {"name": "成都全搜索", "domain": "chengdu.cn", "priority": 3}
  ]
}
```

### 武汉 (Wuhan)

```json
{
  "priority_sources": [
    {"name": "长江日报", "domain": "cjrbszb.changjiangtimes.com", "priority": 1},
    {"name": "武汉发布", "domain": "wuhan.gov.cn", "priority": 2},
    {"name": "大武汉", "domain": "dawuhanapp.com", "priority": 3}
  ]
}
```

---

## 如何选择权威新闻源

### 选择标准

1. **官方背景**：党报、机关报、政府主办网站
2. **内容原创**：以原创报道为主，非转载聚合
3. **更新频率**：日报或即时更新
4. **可访问性**：网站稳定，无需登录即可阅读
5. **存档完整**：历史报道可检索

### 优先级排序

```
第一优先：市委机关报电子版
    ↓
第二优先：报业集团新媒体/客户端
    ↓
第三优先：重点新闻门户网站
    ↓
第四优先：政府信息公开平台
```

---

## 未来发展方向

### 短期计划 (v1.x)

- [ ] 支持更多触发关键词的模糊匹配
- [ ] 添加新闻源可用性检测
- [ ] 支持用户自定义添加新闻源
- [ ] 添加新闻源更新频率标注

### 中期计划 (v2.x)

- [ ] 多城市 Skill 自动识别（根据用户位置）
- [ ] 新闻内容摘要生成（可选）
- [ ] 热点新闻聚合展示
- [ ] 支持语音查询触发

### 长期愿景 (v3.x)

- [ ] 全国 300+ 城市新闻源数据库
- [ ] AI 自动发现新的权威新闻源
- [ ] 新闻可信度评分系统
- [ ] 跨城市新闻关联分析

---

## 社区贡献

欢迎为其他城市创建类似的 Skill！

### 贡献流程

1. Fork 本仓库
2. 创建城市分支：`git checkout -b city/guangzhou`
3. 修改配置和文档
4. 提交 PR 到主仓库的 `cities/` 目录
5. 维护者审核后合并

### 命名规范

- 仓库名：`cityname-news-router`
- 分支名：`city/cityname`
- Skill 名：`CityName Authoritative News Router`

---

## 相关项目

| 城市 | 仓库 | 状态 |
|-----|------|------|
| 深圳 | shenzhen-news-router | ✅ 已发布 |
| 广州 | guangzhou-news-router | 🚧 计划中 |
| 上海 | shanghai-news-router | 🚧 计划中 |
| 北京 | beijing-news-router | 🚧 计划中 |

---

## 联系方式

- 主仓库：https://github.com/tasteday-prog/shenzhen-news-router
- 问题反馈：提交 Issue
- 城市适配：提交 PR 或联系维护者

---

*让每座城市的 AI 都先问当地的权威媒体。*
