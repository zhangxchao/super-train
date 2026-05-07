# 🚄 super-train

火车票智能中转方案推荐助手 — Claude Code Skill。

基于 [flyai](https://flyai.open.fliggy.com/) `search-train` 命令，查询 12306 余票并智能拼接中转换乘方案，学习用户的坐席、时间与中转偏好，给出可解释的推荐。

## 特性

- 🎯 **直达 + 中转双策略**：直达无票自动转中转拼接
- 💺 **坐席偏好感知**：卧铺、二等座、软卧等偏好动态匹配；过夜车默认推卧铺
- 🕒 **自然语言时段识别**："明天上午""下午 3 点"自动转换为查询参数
- 🔄 **同站换乘优先**：默认过滤跨站中转，照顾老人与多行李场景
- 📊 **多方案评分**：总时长 40% + 舒适度 40% + 价格 20%，支持按"最快""最便宜"动态调权
- 🧠 **偏好持久化**：硬约束 (`preferences.json`) + 历史路线 (`history.json`) 联合记忆

## 前置依赖

```bash
npm i -g @fly-ai/flyai-cli
```

无需 API 密钥即可试用；如需更稳定结果，访问 [flyai.open.fliggy.com](https://flyai.open.fliggy.com/) 获取 key 后：

```bash
flyai config set FLYAI_API_KEY "your-key"
```

## 安装

将本仓库放入 Claude Code 的 skills 目录：

```bash
git clone git@github.com:zhangxchao/super-train.git ~/.claude/skills/super-train
```

## 使用

直接对 Claude 说：

- "查一下明天北京到上海的高铁票"
- "从深圳到拉萨怎么中转？"
- "经武汉中转，要硬卧"
- "帮我订火车票去桂林"

详细行为规范见 [SKILL.md](SKILL.md)，flyai CLI 参数见 [references/flyai-cli-reference.md](references/flyai-cli-reference.md)。

## 目录结构

```
super-train/
├── SKILL.md                          ← 完整技能说明
├── assets/
│   ├── preferences.json              ← 用户偏好（硬约束）
│   └── history.json                  ← 历史查询/购票记录
└── references/
    └── flyai-cli-reference.md        ← flyai CLI 参数速查
```

## License

MIT
