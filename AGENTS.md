# AGENTS.md
定义 Agent 执行闭环与协作规则，确保任务稳定、可验证、可追溯。Agent 必须遵循本流程。

## 一、核心原则
1. 只实现当前 task 要求
2. 遵循 prompt.md 约束
3. 不做无关优化、重构或扩展
4. 不改变未涉及模块
5. 保持现有结构与代码风格
6. 在完全理解需求之前不进行修改
7. 避免破坏性操作（删除/覆盖/重置）
8. 禁止修改 implement.md、prompt.md、plan.md 和 documentation.md
禁止：主动扩展需求、推测未要求功能、重写模块、改变架构（除非 task 明确要求）

## 二、OpenSpec 任务创建规范

### 任务创建流程
1. 使用 openspec 创建任务定义后，Agent 必须强制调用 superpowers:brainstorming 技能
2. superpowers:brainstorming 阶段用于：
   - 详细讨论任务需求和细节
   - 确认任务目标和验收标准
   - 识别潜在风险和技术难点
   - 完善任务实现方案
3. superpowers:brainstorming 完成后，才能进入任务执行阶段

### 强制 superpowers:brainstorming 要求
- 每个通过 OpenSpec 创建的任务都必须经过 superpowers:brainstorming 技能讨论
- superpowers:brainstorming 必须记录在任务日志中
- superpowers:brainstorming 阶段发现的问题必须在执行前解决
- 如果 superpowers:brainstorming 发现任务定义存在问题，应标记任务为 blocked 状态

## 三、工作闭环
每个 task 按顺序执行：
1. 理解约束
2. 确认当前 task
3. 如果是 OpenSpec 创建的任务，调用 superpowers:brainstorming 技能进行讨论
4. 执行最小修改
5. 按验收标准验证
6. 更新日志
7. 进入下一个 task
未完成当前 task 前不得进入下一个 task。

## 四、执行顺序
开始 task 时按顺序读取：
AGENTS.md → implement.md → prompt.md → plan.md → documentation.md 和 logs文件夹(按需) → openspec tasks
确认目标、约束、当前 task、验收标准后再执行。

对于 OpenSpec 创建的任务：
1. 读取任务定义后必须调用 superpowers:brainstorming 技能
2. 完成 superpowers:brainstorming 讨论并记录结果
3. 确认任务细节和实现方案之后才能开始执行任务

## 五、任务执行规则
仅修改与当前 task 相关的代码；保持改动最小；遵循现有结构与命名；避免扩大修改范围。
如遇问题：在不影响已有功能的前提下优先修复阻塞当前 task 的问题，避免扩散影响。

对于 OpenSpec 任务：
- 必须遵循 superpowers:brainstorming 阶段确定的实现方案
- superpowers:brainstorming 中发现的风险和问题必须在执行时特别注意
- 如果执行过程中发现新问题，应重新进行 superpowers:brainstorming 讨论

## 六、验证规则
必须依据 openspec tasks 的验收标准验证结果。
未通过验证必须修复，不得跳过或继续下一个 task。

## 七、文件职责
prompt.md：定义代码约束、修改范围与优先级，防止过度修改。
plan.md：定义 task 顺序与检查点规则，确保按顺序执行。
implement.md：定义执行流程、验证方式、文档更新规则。
documentation.md：定义日志格式规范，不记录状态，仅规定 logs 写法。