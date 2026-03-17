# Learning Intent Collection Skill

## Purpose

Collect human-in-the-loop decisions before work starts, and again when entering a new stage.

## Input Schema

```json
{
  "questions": [
    {
      "header": "string",
      "question": "string",
      "options": [
        { "label": "string", "description": "string" }
      ],
      "multiSelect": false
    }
  ]
}
```

## Output Schema

```json
{
  "answers": [
    {
      "header": "string",
      "selectedLabels": ["string"],
      "otherText": "string"
    }
  ],
  "stage": "TaskXX-Phase"
}
```

## Required Behavior

1. Ask 1-4 questions only.
2. Each question must have:
   - clear `header`
   - specific `question`
   - 2-4 options with `label` + `description`
   - optional `multiSelect` (default false)
3. Always support `Other` custom text.
4. Accept shorthand answer form (example: `1A2B3C4AC`).
5. After answers:
   - output a compact decision summary
   - continue task execution immediately

## Stage Re-entry Rule

Re-run this skill when stage changes:
- new task (Task00 -> Task01)
- new phase (学习输入 -> 实践过程 -> 问题记录 -> 学习心得 -> 提交收口)

Do not re-ask if still in same stage.

## Default Question Set (Template)

1) `header`: 学习深度  
`question`: 本阶段你希望做到什么深度？  
Options:
- `快速过一遍`: 先推进进度，聚焦主线
- `标准完成`: 满足打卡要求，质量与速度平衡
- `深入掌握`: 多做习题和反思，追求理解深度

2) `header`: 交付优先级  
`question`: 本阶段优先产出什么？  
Options:
- `打卡记录`: 先完善 ToStudyList 与截图
- `习题答案`: 先形成题目分析与答案
- `实践改造`: 先做代码实验与验证

3) `header`: 时间预算  
`question`: 本阶段预计投入多长时间？  
Options:
- `30分钟`: 最小闭环
- `60分钟`: 标准闭环
- `90分钟`: 含复盘扩展

4) `header`: 聚焦模块  
`question`: 本阶段优先攻克哪些模块？  
`multiSelect`: true  
Options:
- `概念理解`: 定义、边界、类型
- `方法框架`: TAO、PEAS、Workflow vs Agent
- `实践落地`: 运行、调试、截图、记录

