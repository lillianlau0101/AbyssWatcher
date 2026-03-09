<div align="center">

# 🌊 AbyssWatcher

**合规导向的公开专业人才信号研究框架**
*A Compliance-First Public Talent Signal Research Framework*

[![Ethics First](https://img.shields.io/badge/Ethics-First-green.svg?style=flat-square)](docs/ethics-compliance.md)
[![Strategy](https://img.shields.io/badge/Strategy-Operational-blue.svg?style=flat-square)](docs/strategy.md)
[![License](https://img.shields.io/badge/License-MIT%20with%20Ethics%20Clause-yellow.svg?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/Status-PoC-orange.svg?style=flat-square)](https://github.com/lillianlau0101/AbyssWatcher)
[![GitHub Stars](https://img.shields.io/github/stars/lillianlau0101/AbyssWatcher?style=flat-square)](https://github.com/lillianlau0101/AbyssWatcher/stargazers)

[中文文档](#-核心理念) | [English](#-core-concept)

</div>

---

## 💡 核心理念

**发布者悖论（Publisher Paradox）**：90% 的行业顶尖专家在社交媒体选择"潜水模式"——他们不生产内容，但无法抑制在专业讨论中评论的冲动。

> 发帖 = 暴露身份 + 引来骚扰  
> 评论 = 满足表达欲 + 保持低调

这个悖论，就是 AbyssWatcher 的切入点。

**传统猎头 vs. AbyssWatcher：**

| | 传统方式 | AbyssWatcher |
|--|--------|-------------|
| 路径 | 搜索关键词 → 查看博主主页 → 群发私信 | 监控技术讨论区 → 识别高质量评论 → 建立专业对话 |
| 精准度 | 低（靠内容生产者，非真正专家） | 高（靠行为信号，捕捉沉默的专家） |
| 对象感受 | ❌ 骚扰感强 | ✅ 尊重且精准 |
| 效率 | 低 | 高 |

---

## 🎯 应用场景矩阵

| 目标人群 | 信号特征 | 潜在需求 | 合规风险等级 |
|---------|---------|---------|------------|
| 量化研究员 | 深夜评论因子细节、夏普/回撤讨论 | 跳槽 / 募资 | 🟡 中 |
| 基金经理 | 宏观帖下纠错数据、主页空白 | 寻找新平台 | 🟢 低 |
| Web3 开发者 | 技术讨论深度回帖、链上术语 | 找合伙人 | 🟢 低 |
| AI 研究员 | 论文复现问题解答、行话密度高 | 创业机会 | 🟡 中 |

---

## 🔍 信号识别方法论

### Phase 1：关键词信号捕获

高价值评论者通常会暴露以下语言特征：

```json
{
  "量化领域高频词": ["因子", "夏普", "回撤", "Alpha", "Tick数据", "Barra", "滑点"],
  "行话黑话": ["过拟合", "样本外", "实盘", "IC衰减", "截面动量"],
  "质疑语气（专家标志）": [
    "这个不对",
    "实测过吗",
    "忽略了...",
    "其实可以优化",
    "你的假设有问题"
  ]
}
```

> 💡 **核心逻辑**：真正的专家评论时会不自觉使用高密度行话，并倾向于指出错误而非附和。这是区分「真懂」与「假懂」的关键信号。

### Phase 2：信号评分（Signal Scoring）

每条评论经过多维打分，综合判断发言者的专业价值：

```python
def score_comment(comment: dict) -> float:
    """
    综合评分：专业词密度 + 情感极性 + 互动深度
    """
    score = 0.0
    
    # 专业词汇密度（权重 40%）
    score += keyword_density(comment['text'], domain_dict) * 0.4
    
    # 纠错行为加分（权重 30%）
    if has_correction_pattern(comment['text']):
        score += 0.3
    
    # 评论深度（字数 + 结构）（权重 20%）
    score += depth_score(comment['text']) * 0.2
    
    # 时间信号（深夜/工作日发言）（权重 10%）
    score += time_signal(comment['timestamp']) * 0.1
    
    return min(score, 1.0)
```

### Phase 3：分层触达话术

不同评分段位对应不同的首触策略：

```markdown
## 高分段（0.8+）— 直接专业切入
"看到你在 [X帖子] 下提到 [具体观点]，
我们正在研究类似的方向，想交流一下..."

## 中分段（0.5-0.8）— 先建立共鸣
"你对 [X问题] 的理解很有意思，
我自己也踩过这个坑，想多聊聊..."

## 低分段（<0.5）— 暂时观察，持续跟踪
```

---

## 🏗️ 系统架构

```
┌─────────────────────────────────────────┐
│           指挥中枢 (Commander)            │
│    - 任务调度（非侵入式浏览模式）           │
│    - 合规检查层（GDPR / 个保法过滤）        │
└──────────────┬──────────────────────────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
┌───────┐  ┌───────┐  ┌───────┐
│Node-1 │  │Node-2 │  │Node-3 │  ← 移动端 Residential IP 池
│(上海) │  │(北京) │  │(深圳) │
└───┬───┘  └───┬───┘  └───┬───┘
    │          │          │
    ▼          ▼          ▼
┌─────────────────────────────────────┐
│       行为模拟层 (Behavior Mimic)     │
│  - 人类浏览轨迹模拟                   │
│  - 随机停留时间（5–45s）              │
│  - 自然滚动（贝塞尔曲线算法）          │
│  - 设备指纹轮换（iOS / Android）      │
└─────────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│       信号处理层 (Signal Engine)      │
│  - 关键词匹配 + 语义评分              │
│  - 用户画像构建（公开信息）            │
│  - 高价值目标标记与追踪               │
└─────────────────────────────────────┘
```

**关键设计原则：**
- 仅采集公开可见评论，不触碰私信/私密内容
- 所有节点模拟真实用户浏览行为，避免对平台造成异常请求压力
- 合规检查层在数据进入分析管道前过滤敏感字段

---

## 🚀 快速开始

### 方式一：手动 MVP（零成本验证）

在小红书 / 知乎搜索以下组合，人工筛选高质量评论者：

```
"因子挖掘" + 评论区 + 最新
"回撤控制" + 回复 + 深度讨论
"Alpha" + "实盘" + 纠错
```

筛选标准：评论字数 > 100字 + 含行话 + 有纠错行为 = 值得跟进

### 方式二：半自动化（配合现有工具）

1. 使用 [八爪鱼](https://www.bazhuayu.com/) 等可视化爬虫抓取目标帖评论
2. 将评论导入 `src/analysis/signal_scorer.py` 批量评分
3. 对评分 > 0.6 的用户运行话术模板触达

### 方式三：完整部署（进阶）

```bash
# 克隆项目
git clone https://github.com/lillianlau0101/AbyssWatcher.git
cd AbyssWatcher

# 安装依赖
pip install -r requirements.txt

# 配置目标平台和关键词
cp config/example.yaml config/local.yaml
# 编辑 local.yaml，填写目标平台和词库路径

# 运行信号采集
python src/main.py --platform xiaohongshu --domain quant
```

---

## 📁 项目结构

```
AbyssWatcher/
├── src/
│   ├── keywords/
│   │   ├── quant_dict.json       # 量化核心词库
│   │   └── web3_dict.json        # Web3 扩展词库
│   ├── analysis/
│   │   └── signal_scorer.py      # 信号评分算法
│   └── templates/
│       └── outreach_msgs.md      # 分阶段话术模板
├── docs/
│   ├── strategy.md               # 操作策略手册
│   ├── ethics-compliance.md      # 合规与伦理指南
│   └── anti_patterns.md          # 常见错误模式
├── cases/
│   └── example_analysis.md       # 脱敏案例分析
├── config/
│   └── example.yaml              # 配置模板
├── LICENSE                       # MIT + 伦理约束条款
└── README.md
```

---

## ⚖️ 合规边界

AbyssWatcher 基于以下原则设计，使用者需自行确保合规：

| 操作 | 状态 |
|------|------|
| 采集平台公开评论内容 | ✅ 合规（公开信息） |
| 分析用户公开行为模式 | ✅ 合规（研究目的） |
| 向目标用户发送骚扰性私信 | ❌ 禁止 |
| 采集、存储个人隐私信息 | ❌ 禁止 |
| 绕过平台明确禁止的访问限制 | ⚠️ 使用者自行评估风险 |
| 批量自动化操作违反平台 ToS | ⚠️ 使用者自行评估风险 |

> 📋 详细合规指南见 [docs/ethics-compliance.md](docs/ethics-compliance.md)

---

## 🗺️ Roadmap

- [x] 手动 MVP 方法论文档
- [x] 信号评分算法（`signal_scorer.py`）
- [x] 量化 / Web3 词库
- [x] 合规框架文档
- [ ] 小红书评论自动采集模块
- [ ] 知乎评论采集模块
- [ ] 用户画像自动生成
- [ ] 话术效果追踪与 A/B 测试
- [ ] 多行业词库扩展（医疗 / 法律 / 学术）

---

## 🤝 Contributing

欢迎贡献词库、案例和改进建议。特别欢迎：
- 垂直行业词库（法律、医疗、学术等）
- 真实脱敏案例
- 话术模板的 A/B 测试数据

---

## 📄 License

MIT with Ethics Clause © [Lillian Lau](https://github.com/lillianlau0101)

使用本项目即表示同意遵守 [伦理使用条款](docs/ethics-compliance.md)。

---

<div align="center">

**Watch the abyss. Find the signal.**
*潜入深处，捕捉信号。*

⭐ 如果这个框架对你有启发，欢迎 Star — 这是对独立研究者最直接的支持。

</div>
