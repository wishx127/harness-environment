# harness-environment

Agent 工作流框架，基于 spec-driven 模式的任务执行系统。

## 项目结构

```
harness-environment/
├── openspec/
│   └── config.yaml          # openspec 配置
├── logs/                     # 执行日志
├── AGENTS.md                 # Agent 执行闭环与协作规则
├── prompt.md                 # 代码约束与修改范围
├── plan.md                   # 任务序列与检查点规则
├── implement.md              # 执行流程与验证规范
├── documentation.md          # 日志格式规范
└── LICENSE
```

## 核心规范

| 文件 | 用途 |
|------|------|
| AGENTS.md | 定义 Agent 执行闭环与协作规则 |
| prompt.md | 代码约束、修改范围与优先级 |
| plan.md | 任务顺序与检查点规则 |
| implement.md | 执行流程、验证方式、文档更新规则 |
| documentation.md | 日志格式规范 |