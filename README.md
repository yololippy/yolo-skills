# yolo-skills

个人 Codex 技能仓库。仓库中的目录是技能源码的唯一来源，全局技能目录通过软链接引用这里，方便统一维护、版本管理和跨设备同步。

## 技能列表

| 技能 | 用途 |
| --- | --- |
| [`commit-workflow`](./commit-workflow/) | 检查真实改动、给出逻辑提交分组，并按依赖顺序完成 Git 提交和结果汇报。 |

## 目录结构

```text
yolo-skills/
├── commit-workflow/
│   ├── SKILL.md
│   └── agents/
│       └── openai.yaml
├── .gitignore
└── README.md
```

每个技能使用独立目录，至少包含 `SKILL.md`。需要界面名称、简介或调用策略时，可增加 `agents/openai.yaml`。


## commit-workflow

当用户要求 `commit`、提交改动或拆分提交时，该技能会：

1. 检查分支、工作区、暂存区和未跟踪文件。
2. 按目的、职责和依赖关系给出提交分组结论。
3. 在用户直接要求提交时依次暂存、检查并提交。
4. 汇报 commit hash、验证结果和剩余改动。

推送不会从提交请求中自动推断，只有用户明确要求 `push` 时才会执行。

## 维护约定

- 技能目录名与 `SKILL.md` 中的 `name` 保持一致。
- 修改技能时同步检查 `agents/openai.yaml` 的展示信息。
- 不提交本地环境文件、依赖目录、缓存和构建产物。
- 提交前检查差异、YAML 格式以及全局软链接是否仍然有效。
