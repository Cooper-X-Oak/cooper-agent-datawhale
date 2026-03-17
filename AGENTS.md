# Repository Working Rules

Scope: entire repository.

## Primary Collaboration Goal

This repo is a personal learning repo (not a public template repo).  
Always prioritize progress tracking, reflection notes, screenshots, and stage-based learning support.

## Mandatory Human-in-the-Loop (HITL) Decision Collection

For every learning run, the assistant must collect learning intent decisions before execution.

Trigger points:
1. Before starting a new learning session/day.
2. Before entering a new stage (for example: new TaskXX, or phase switch like input -> practice -> review -> submission).

Execution rules:
1. Ask 1-4 concise decision questions.
2. Each question must include:
   - `header`: short label for UI/readability
   - `question`: specific question sentence
   - `options`: 2-4 options, each with `label` and `description`
   - `multiSelect`: default false
3. Always include an `Other` path for custom text input.
4. After user answers, summarize decisions in one short block, then continue execution.

## Interaction Style for Decision Prompts

When native selectable UI is unavailable, use compact numbered choices, e.g.:
- `Q1 目标深度: A/B/C`
- `Q2 产出优先: A/B/C`
- `Q3 时间预算: A/B/C`
- `Q4 重点模块(可多选): A/C/D`

Allow shorthand answers like `1A2B3C4AC`.

## Stage Awareness

Define stage as `Task + Phase`.
- Task examples: `Task00`, `Task01`, ...
- Phase examples: `学习输入`, `实践过程`, `问题记录`, `学习心得`, `提交收口`

If stage changes, re-run HITL prompts before continuing.
If stage does not change, do not repeatedly ask the same questions.

## Skill File

Use and follow: `.codex/skills/learning-intent/SKILL.md`

