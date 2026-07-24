# 百官纳谏 / Digital Court

一个为 Codex 设计的真实多智能体决策 Skill：召集彼此独立的“群臣”，从不同利益、时间尺度和专业角度审议复杂问题，经过交叉质询、丞相综合与御史封驳，最后把决定权交还给用户。

> A real multi-agent deliberation skill for Codex, inspired by the Chinese imperial court. Independent agents submit sealed opinions, challenge one another, synthesize options, and preserve the user's final authority.

## 它解决什么问题

当一个问题没有唯一正确答案，而是需要同时考虑风险、利益相关者、长期影响和执行约束时，单一视角很容易形成盲区。“百官纳谏”把审议拆成多个相互独立的角色，让分歧真正发生，再把结果收敛成可执行建议。

适合：

- 商业与产品决策
- 职业和个人选择
- 战略、政策与资源取舍
- 方案 A/B 比较
- 风险审查与反方论证

简单事实题不会强制开朝。

## 朝廷架构

四位固定核心朝臣：

- **御史大夫**：检查证据、隐性成本、最坏情况和虚假自信。
- **谏议大夫**：挑战默认假设，提出逆耳但有依据的意见。
- **民意使**：分析客户、员工、家人、公众等利益相关者的影响。
- **史官**：考察历史类比、长期后果、路径依赖和不可逆风险。

常朝与大朝会还会根据问题召集动态特使，例如工程师、财务专家、律师、消费者、竞争对手或行业老兵。

用户是最终裁决者；主智能体负责主持，丞相负责独立综合。

## 议事流程

1. **立案**：整理目标、事实、约束和未知假设。
2. **密封奏议**：各子智能体在隔离上下文中独立作答，不能预先看到其他意见。
3. **廷议驳奏**：群臣阅读匿名奏议，指出最强异议、遗漏和虚假共识。
4. **丞相拟旨**：区分真实共识、主要分歧、少数意见和关键未知。
5. **御史封驳**：审查事实跳跃、风险淡化、虚假精确和被抹平的异议。
6. **请君裁决**：给出首选、备选、停止条件和最小下一步，但不替用户决定。

## 朝会规模

- **小朝会**：四位核心朝臣与一位丞相。
- **常朝**：四位核心朝臣、两位动态特使与一位丞相；默认选择。
- **大朝会**：增加三至四位动态特使，用于重大、高风险或跨领域决策。

## 安装

使用 Skills CLI：

```bash
npx skills add https://github.com/Rayze-png/baiguan-najian --skill digital-court -g -y
```

安装后，新建一个 Codex 任务即可使用。

## 使用示例

```text
使用 $digital-court 开常朝：我是否应该离开稳定工作去创业？
```

```text
使用 $digital-court 开大朝会：我们的 SaaS 应该直接涨价，还是先做价格实验？
```

```text
使用 $digital-court 开廷辩：产品方案 A 与方案 B 应该选哪个？
```

English example:

```text
Use $digital-court to convene a standard court and evaluate whether we should launch now or run a closed beta first.
```

## 运行要求与边界

- 需要运行环境支持创建彼此独立的子智能体。
- 并发数量不足时可以分批运行，但首轮意见必须保持隔离。
- 如果无法创建真实子智能体，Skill 会明确说明，不会用单模型角色扮演冒充多智能体。
- 医疗、法律、金融等高风险问题仍需核实权威资料，并在适当时咨询合格专业人士。
- 多数票和群臣共识不能替代事实证据。

## 仓库结构

Skill 位于 [`skills/digital-court/`](skills/digital-court/)。角色定义、提示模板和验收方法均随 Skill 一同提供。

## 贡献

欢迎提交 Issue 或 Pull Request，尤其是：

- 更有效的角色分工与反同质化方法
- 不同类型决策的前向测试案例
- 多智能体运行环境的兼容性改进
- 对事实纪律、少数意见保护和失败降级的改进

## License

[MIT](LICENSE) © 2026 Rayze-png

