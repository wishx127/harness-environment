# documentation.md

## 目的

定义日志的写入规则与格式。

用于：
  - 统一日志结构
  - 保证执行过程可追溯
  - 降低上下文混乱
  - 便于人类与 Agent 理解执行历史

所有执行记录必须写入 logs/ 文件夹。

## 日志目标

日志必须能够回答：
  - 当前做了什么
  - 为什么这样做
  - 是否遇到问题
  - 问题如何解决
  - 任务是否完成

日志必须：简洁，一致，可解析，可追溯
每个任务只对应一份日志文件，不支持重复创建(即使时间不一样也不允许)

## 日志文件命名规则

格式：

YYYY-MM-DD__task-name.md

示例：

2026-03-28__implement-user-api.md

## task-name 规则

task-name 必须：简短，语义明确，使用 kebab-case模式命名与 openspec task 语义一致。

## 日志模板
  ### task log

  task_name:
  implement-user-api

  date:
  2026-03-28

  status:
  in_progress

  #### summary

  实现用户创建 API，并完成参数校验与验证流程。

  #### changes

  - 创建 POST /api/users endpoint
  - 添加请求参数 schema 校验
  - 增加 email 必填规则
  - 更新错误返回结构

  #### issues(非必要)

  ##### issue 1

  problem:
  缺少 email 字段校验导致验证失败

  impact:
  可能产生无效用户数据

  resolution:
  新增 email required 校验规则

  status:
  resolved

  #### decisions

  ##### decision 1

  decision:
  沿用现有 validation 结构

  reason:
  符合 minimal change 原则

  impact:
  无需重构现有 middleware

  #### validation

  method:
  使用示例请求进行接口验证

  result:
  通过

  notes:
  返回结构符合 openspec 验收标准

  #### change_history

  2026-03-28 10:00
  创建日志文件

  2026-03-28 10:05
  完成 API 基础实现

  2026-03-28 10:08
  发现参数校验问题

  2026-03-28 10:12
  修复校验规则

  2026-03-28 10:15
  验证通过

## 日志写入时机

必须写入日志的情况：

开始执行 task
产生代码修改
发现问题
task 状态变化
task 完成/失败
其他特殊情况

## 禁止事项

禁止：

在日志中复制完整代码
记录无关讨论
记录 prompt 内容
记录重复信息
改变日志格式
写入 logs 目录之外
同一个任务出现多份日志

## 目标效果

记录任意任务的执行状态(关键修改、问题、解决方式、完成状态)
人类与 Agent 均可快速理解执行轨迹。