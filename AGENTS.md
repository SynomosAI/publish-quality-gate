# AGENTS.md — 给 AI Agent 的工作指引

本文件面向自动化 AI Agent。人类读者请看 [README.md](README.md)。

## 这个仓库是什么

`publish-quality-gate` 是一个 **Agent Skill 发布包**，是发布流程的固定门禁。核心资产是 `SKILL.md`（四层敏感信息清单 + TRACE 五维自测全文），辅以 `scripts/check_release.py` 自检脚本、`manifest.json` 包指纹、`ATTESTATION.md` 权属证明。

## 可用的工作命令

```bash
# 查看技能元数据
head -15 SKILL.md

# 对一个待发布目录跑自检
python scripts/check_release.py path/to/your/release

# 查看包指纹与权属
cat manifest.json
cat ATTESTATION.md
```

前置依赖：Python 3（跑 check_release.py）。

## 约定（Do）

- 修改前先读 `SKILL.md` frontmatter，保持 `name`/`version`/`author`/`license` 兼容。
- 修改四层清单或 TRACE 维度时，同步更新 `SKILL.md`、`scripts/check_release.py` 与 README 速查表。
- 修改文件清单后重算 `manifest.json` 的逐文件 sha256 与包指纹。

## 禁止（Don't）

- 不要改动 `SKILL.md` 的 `author`/`license` 字段、`LICENSE.md` 版权主体与 `ATTESTATION.md` 权属声明——**权属字段只由维护者变更**。
- 不要把扫描中发现的真实 secrets / 客户数据 / 本机路径提交回本仓。
- 不要声称本仓「已认证 / 已商用交付 / 已服务特定客户」。
- 不要跳过任何一层敏感信息检查就放行发布物。

## 边界

本仓专注**发布物脱敏检查与发布后 TRACE 自测**；不替代真实安全审计或合规认证。
