# 烧掉 1000 亿 token 之后，我终于教会了 GPT 做设计（Agent UI Design）

面向 AI Agent 与开发者的 UI 设计工作流与 Prompt 仓库。

把模糊的功能需求，分步变成字段清单、ASCII 文本原型、黑白灰页面，最后加上颜色和样式生成完整的前端代码。

---

## 为什么大模型写出的页面总是很难看？

大模型做页面难看，问题往往不在配色，而在**信息层级混乱**：
1. **盲目堆砌说明**：怕漏掉信息，把所有说明、协议和次要操作从上往下全摊在页面上；
2. **没有视觉重点**：所有文字大小差不多、按钮互相抢视线，超出人脑一次能处理的 4 个信息块（米勒定律）；
3. **排版和配色混在一起做**：一边排位置一边调颜色，结果间距忽大忽小，满屏手写样式。

解法很简单：**先把布局和黑白灰层级定下来，再去加颜色和样式细节**。

---

## 四步工作流

```text
[ 功能需求 ] 
     │
     ▼
【第一步：梳理功能场景】 ── 产出：目标用户、核心操作、页面必留字段清单
     │
     ▼
【第二步：画 ASCII 原型】── 产出：合并为 3~4 张卡片，次要信息放进点击弹窗
     │
     ▼
【第三步：生成 HTML 页面】── 产出：先出黑白灰页面定好字号间距，再加颜色和样式细节
     │
     ▼
【第四步：搭建自动反馈】 ── 机制：存下组件变量、记录改错文档、配置 pre-commit 自动检查
```

---

## 提示词清单

| 步骤 | 文件 | 说明 |
| :--- | :--- | :--- |
| **01 功能场景** | [`prompts/01-requirement-tree.md`](prompts/01-requirement-tree.md) | 从具体场景和用户操作倒推页面必留字段与状态分支 |
| **02 文本原型** | [`prompts/02-ascii-wireframe.md`](prompts/02-ascii-wireframe.md) | 把零散字段合并成 3~4 张卡片，生成等宽 ASCII 文本原型 |
| **03 页面生成** | [`prompts/03-ui-design-system.md`](prompts/03-ui-design-system.md) | 2.1 万字排版与灰度规则，先生成黑白灰页面再补充样式细节 |

---

## 使用方式

### 方式一：直接复制 Prompt 使用
适用于任何 AI 工具（Codex、Claude、Claude Code、Cursor 等）：
1. 复制 `01-requirement-tree.md`，输入你的业务功能，确认页面字段清单；
2. 复制 `02-ascii-wireframe.md`，生成并调整 ASCII 文本原型；
3. 复制 `03-ui-design-system.md`，先让 AI 输出黑白灰页面，确认无误后再加颜色和组件细节。

### 方式二：作为 Agent Skill 加载
如果你使用的编程 Agent 支持加载本地 Skill（如 Codex、Claude Code、Cursor 等），可以直接克隆本仓库并放入项目的技能目录：
```bash
git clone https://github.com/tinybamz-labs/agent-ui-design.git .agents/skills/agent-ui-design
```

---

## 开源协议

[MIT License](LICENSE)
