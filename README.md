# 自适应任务拆解 · Adaptive Task Planning

一个面向学习、个人项目和其他复杂任务的 Codex skill。通过逐步沟通，把大目标拆成适合用户亲自执行的清晰任务，维护分支依赖、关键前提和后续计划调整。

## 使用

安装后，在 Codex 中说：

> 使用任务拆解：我想完成……

也可以显式调用：

> 使用 $adaptive-task-planning 帮我拆解这个任务：……

如果没有提供任务，技能会先询问具体任务。拆解前会对齐任务重要性、期待、边界和资源约束。

## 主要能力

- **按投入选择模式：** 高保障或够用；两种模式都要求任务清晰，并保留硬性要求。
- **逐步细化：** 先建立全局结构，近期任务细化到可执行，远期任务在信息充分时展开。
- **按用户能力校准：** 通过代表性任务判断是否知道如何开始、如何验收，以及何时停止拆分。
- **维护任务联系：** 记录前置成果、执行顺序、共享资源和分支影响。
- **处理前提失效：** 优先修复值得恢复的现实条件；纠正被证据否定的假设。无法合理恢复时，重新对齐需求和条件，再制定计划。
- **依据反馈修订：** 保留有效成果、稳定任务编号与版本记录。

默认由用户执行；是否使用 AI 由用户决定。本技能不自动执行计划、不自动委派任务，也不进行后台监控。

## 安装到 Codex

可以让 Codex 的 skill-installer 从本仓库根目录安装，目标技能目录名为 `adaptive-task-planning`。例如向 Codex 发送：

> 使用 skill-installer，从 https://github.com/Eatproperly/adaptive-task-planning 的根目录安装技能，名称设为 adaptive-task-planning；已有同名技能时先保留备份。

手动安装时，在你的 Codex skills 目录下创建 `adaptive-task-planning` 文件夹，放入 `SKILL.md`、`agents/` 和 `references/`。通常该目录是 `~/.codex/skills`；如设置了 `CODEX_HOME`，则为该路径下的 `skills`。不要覆盖未备份的同名技能。

## 文件

- [SKILL.md](SKILL.md)：核心流程、中文触发语和质量检查。
- [agents/openai.yaml](agents/openai.yaml)：展示信息与自动发现设置。
- [references/plan-format.md](references/plan-format.md)：计划结构、任务卡与状态规则。
- [references/premise-recovery.md](references/premise-recovery.md)：前提修复、纠错与重规划。

## 验证与边界

已进行文件结构、引用、元数据和安装副本一致性检查，并对学习、够用作业和前提失效场景进行规则走查。尚未完成独立的实际行为评测。技能提供检查与纠偏流程，不保证计划一定成功，也无法自动获知用户实际进展。

回滚本地安装时，可将新增的技能目录移出 skills 目录；更新已有安装时恢复先前备份。仓库修改可通过 Git 提交历史回退。
