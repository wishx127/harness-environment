# plan.md

plan.md 不定义任务内容，仅定义任务执行协议。

## 任务来源
任务唯一来源：openspec 输出的 tasks

Agent 不得：
  - 自行新增 task
  - 合并 task
  - 修改 task 目标
  - 重排 task 顺序

如任务存在问题：必须记录问题，而不是修改任务定义。

## 单任务执行协议

每个 task 必须按照以下流程执行：

1. 理解任务目标
2. 实现最小可行修改
3. 执行任务验收，测试等工作
4. 更新 documentation.md
5. 标记任务状态

任务未完成前不得进入下一个 task。

## 任务状态

每个 task 必须处于以下状态之一：

  - pending -- 尚未开始
  - in_progress -- 正在执行
  - blocked -- 缺少必要信息或依赖
  - completed -- 通过验收标准
  - failed -- 多次尝试仍未通过验收

## 验收规则

验收标准：

以 openspec task 定义和spec为准。

最低验证要求：

  - 输出符合 task和 spec 描述
  - 未引入明显错误
  - 未破坏已有功能
  - 修改范围合理

## 失败处理

单次失败：

  - 记录失败原因
  - 进行修复
  - 更新 documentation.md

连续失败 ≥ 2 次：

  - 标记 task 为 failed
  - 停止继续尝试
  - 回到上一个 completed task
  - 复核任务定义

禁止无限重试。

## 与 documentation.md 的同步

每次 task 完成或失败时：

必须更新 documentation.md：

记录：

  - 当前 task
  - 状态变化
  - 关键决策
  - 已知问题
