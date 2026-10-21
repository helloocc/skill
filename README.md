# indie-project

面向独立开发者的 Codex Skill：将产品想法落为最小可运行、可验证的用户流程，并按需维护项目计划与架构。

适用于初始化早期项目、规划 MVP，以及按已有计划继续开发。已有项目沿用原技术栈；Monorepo、后端和数据库按需求创建。纯问答和局部修改无需启动完整初始化流程。

## 安装

需要 Git 和支持本地 Skills 的 Codex。本技能由 Markdown 文档组成，无需安装应用依赖或配置 API 密钥。

先将仓库克隆到本机固定目录：

```bash
mkdir -p ~/Developer
git clone https://github.com/helloocc/skill.git ~/Developer/indie-project
```

已克隆本仓库时，跳过这一步，并将以下命令中的 `~/Developer/indie-project` 替换为实际绝对路径。

以下两种安装范围任选其一。若目标位置已有同名技能，先检查其来源，不要直接覆盖。

### 本机所有项目可用

```bash
mkdir -p ~/.agents/skills
ln -s ~/Developer/indie-project ~/.agents/skills/indie-project
```

### 仅当前项目可用

在目标项目根目录执行：

```bash
mkdir -p .agents/skills
ln -s ~/Developer/indie-project .agents/skills/indie-project
```

软链接指向本机目录，适合个人使用。团队共享时，可将 `SKILL.md`、`docs/init-project.md` 和 `docs/indiehacking-project.md` 复制到目标项目的 `.agents/skills/indie-project/`，保持相对目录结构，并提交到目标项目仓库。无需复制本仓库的 `AGENTS.md` 或工作计划。

Codex 通常会自动发现技能；未出现时重启 Codex。安装目录和软链接支持详见 [OpenAI 官方 Skills 文档](https://developers.openai.com/codex/skills/)。

## 使用

在目标项目中打开 Codex，通过技能名显式调用：

```text
使用 $indie-project 初始化这个项目：面向独立开发者的活动报名工具，先交付创建活动和提交报名的最小流程。
```

继续已有项目：

```text
使用 $indie-project，读取现有计划，继续下一项任务。沿用当前技术栈和项目约定。
```

也可描述需求，由 Codex 根据技能描述按需选择。技能会按任务读取相关参考文档，在必要时验证结果并更新目标项目状态。

## Skill 与 AGENTS.md

| 文件 | 职责 |
| --- | --- |
| 本技能的 `SKILL.md` | 技能触发描述、执行流程及参考文档路由 |
| 本仓库的 `AGENTS.md` | 维护这个技能仓库时的协作规则 |
| 目标项目的 `AGENTS.md` | 目标项目自身的长期协作约定 |

安装本技能不会自动把本仓库的协作规则应用到其他项目，也不会自动生成目标项目的 `AGENTS.md`。技能遵循目标项目已有约定；明确要求同步规则时，只增量合并适用且缺失的内容。

## 更新

软链接安装使用本机源目录的最新内容。更新源目录：

```bash
git -C ~/Developer/indie-project pull --ff-only
```

更新前先处理源目录中自己的修改；复制安装需手动同步上述三个技能文件。

## 文档入口

- [技能说明](SKILL.md)：执行流程、按需读取和文档维护规则。
- [独立开发原则](docs/indiehacking-project.md)：范围、优先级和技术投入取舍。
- [初始化指南](docs/init-project.md)：默认技术栈、实施步骤与验收要求。

本技能目录保存参考资料，目标项目目录保存业务代码与该项目的工作文档，两者应分别维护。
