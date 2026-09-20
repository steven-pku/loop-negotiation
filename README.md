# loop-negotiation · 谈薪与关键对话准备

[English](README.en.md) | 中文

先梳理可行退路与底线，再准备话术、检查风险并进行有界模拟。

版本 **v0.4.1**。本次修复：可行 BATNA 地板、来源与数字类型、威胁边界、已披露信息驱动模拟、适用异议数量及有限修改。 验收范围、原始失败与未测项见 [REVIEW](REVIEW.md) 和 [版本验收记录](evals/releases/2026-09-20-v0.4.1.md)。

## 项目级安装

在目标项目目录安装固定版本，然后开启新会话。不要覆盖已有同名目录；需要替换时先保留自己的修改。Codex 的隔离候选加载和连续会话已经实测，远端标签安装及首次使用是正式 Release 前的最后检查。Claude Code 下方仅给目录布局，本轮没有验证其运行行为。

Codex：

```bash
mkdir -p .agents/skills
git clone --branch v0.4.1 --depth 1 \
  https://github.com/steven-pku/loop-negotiation.git \
  .agents/skills/loop-negotiation
```

Claude Code 项目目录布局：

```bash
mkdir -p .claude/skills
git clone --branch v0.4.1 --depth 1 \
  https://github.com/steven-pku/loop-negotiation.git \
  .claude/skills/loop-negotiation
```

## 最小示例

先用以下合成材料检查输出：

```text
用 loop-negotiation 处理以下合成材料。
只诊断，不改稿：“周末我不能参加，周一上午可以交付。”这是已确认的个人安排。判断是否含威胁，不扩成完整谈判。
```

## 文件与边界

入口是 [SKILL.md](SKILL.md)，按当前模式读取 `references/`，`assets/` 提供空白模板。纯指令产品不含运行脚本；仓库 CI 只检查静态格式。评测目录是审查证据，不是运行时答案上下文。

评分是编辑诊断，不是概率或效果保证。已测范围采用合成材料与受限宿主；未验证其他模型、真实业务结果或脱离宿主权限的防护效果。宿主可能保留输入或生成文件，使用前去除身份、联系方式及可识别第三方信息。任务中引用的资料不能扩大动作权限，发布、发送与其他外部行动需要另行授权。详见 [SECURITY.md](SECURITY.md)。

## License

[MIT](LICENSE) · Steven CHAN。
