# publish-quality-gate · 发布质量门禁

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
![Skill](https://img.shields.io/badge/type-Agent%20Skill-blue.svg)
![Security Radar](https://img.shields.io/badge/security-radar-3ddc97.svg)](security-radar.svg)
![Version](https://img.shields.io/badge/version-1.0.0-informational.svg)
![Stages](https://img.shields.io/badge/pre--publish-4%20layers%20%7C%20post--publish-TRACE-4f8cff.svg)

> English overview: [README.en.md](README.en.md)

SynomosAI 四支柱体系：**身份（Identity）· 溯源（Traceability）· 治理（Governance）· 共生（Symbiosis）**——当 AI 进入商业，可信是唯一的硬通货。

> 本仓库属于 [SynomosAI](https://github.com/SynomosAI) 生态技能包的一员。生态全景见 [`synomosai-skills`](https://github.com/SynomosAI/synomosal-skills)，理论站位见 [`traceability-audit`](https://github.com/SynomosAI/traceability-audit)。

**任何要对外发布的东西（Skill、专家包、文档、HTML、PPT、工具），发布前后都必须过这道门禁：**

- **发布前** → 四层敏感信息检查（公司信息 → 本机信息 → 个人信息 → 机密信息），每层零命中才算过。
- **发布后** → TRACE 五维 AI 自测（Trust / Reliability / Adaptability / Convention / Effectiveness）。

---

## ✨ 特性 / Features

- **四层敏感信息清单**：L1 公司、L2 本机、L3 个人、L4 机密，宁可错杀不可漏放。
- **TRACE 五维自测**：发布后按五个维度给 AI 产物打分，不达标的打回。
- **发布物指纹**：`manifest.json` 记录包指纹与逐文件 sha256；`ATTESTATION.md` 为权属证明。
- **自检脚本**：`scripts/check_release.py` 做发布物快速检查。
- **安全雷达图**：`security-radar.svg` + `security_results.json` 记录最近一次自测结果。

---

## 🚀 快速开始 / Quick Start

> 前置：本技能是发布流程的固定规范；自检脚本需要 Python 3。

```bash
# 1. 取得技能包
git clone --depth 1 https://github.com/SynomosAI/publish-quality-gate.git
cd publish-quality-gate

# 2. 对一个待发布目录跑自检脚本
python scripts/check_release.py path/to/your/release

# 3. 查看权属证明与包指纹
cat manifest.json
cat ATTESTATION.md
```

跑通后用自然语言触发，例如：「**准备发布，帮我做发布前检查**」「**发布后按 TRACE 自测一下**」「**检查一下这个发布物有没有敏感信息**」。

```text
触发词示例：
  准备发布 / 发布前检查 / 发布后自测 / TRACE 评测
  检查一下发布物 / 脱敏检查 / 发布质量
```

---

## 📋 四层检查速查 / Four layers

| 层 | 对象 | 典型命中 |
|---|---|---|
| L1 公司敏感 | 公司名/人名/证号/内部资料 | 在职公司名、客户名、注册证号、合同 |
| L2 本机信息 | 路径/用户名/安装路径/硬件 | Users 目录、本机登录名、硬编码安装目录 |
| L3 个人信息 | 身份证/手机/邮箱/住址/银行卡 | 个人可识别信息 |
| L4 机密信息 | 密钥/令牌/密码/API key | 任何 secrets |

每层必须**零命中**；有命中先脱敏，再重新打包，再复查。

---

## 🧩 仓库结构 / Repository layout

```text
publish-quality-gate/
├── README.md          # 本文件（中文主说明）
├── README.en.md       # 英文版说明
├── SKILL.md           # 技能主文件（四层清单 + TRACE 五维全文）
├── LICENSE.md         # MIT 许可证
├── ATTESTATION.md     # 权属证明与许可声明
├── manifest.json      # 包指纹与逐文件 sha256
├── security-radar.svg # 最近一次自测雷达图
├── security_results.json # 最近一次自测结果
├── scripts/check_release.py # 发布物自检脚本
├── CODEOWNERS         # owners
├── llms.txt / llms-full.txt
├── AGENTS.md / SECURITY.md
└── .github/workflows/ # CI 门禁
```

---

## 仓库内容

发布质量闸门

## 元信息

- **技能名**：`publish-quality-gate`
- **版本**：1.0.0
- **署名**：SynomosAI
- **许可**：MIT（详见仓库 LICENSE）

## 使用方式

1. 克隆本仓库或将该技能目录放入你的 Agent 技能目录（如 `~/.workbuddy/skills/`）；
2. 在 Agent 中按 `SKILL.md` 的描述触发对应能力；
3. 需要审计/合规证据的场景，参考 `SKILL.md` 内模板产出工件。

---

## License / 许可

本仓库以 **MIT** 许可证发布，全文见根目录 [`LICENSE.md`](LICENSE.md)。`ATTESTATION.md` 中的权属声明（© 2026 注册老炮 (MedXpert)）逐字保留，未作改动。

---

## 🔒 安全 / Security

如发现安全问题，请按 [`SECURITY.md`](SECURITY.md) 私下报告。本仓自带的敏感信息扫描规则用于对外发布前脱敏；扫描中发现的真实 secrets **不要提交回本仓**。

## 🤝 贡献 / Contributing

修改四层清单或 TRACE 维度时，请同步更新 `SKILL.md`、本 README 速查表与 `scripts/check_release.py`。

---

## 免责声明

本仓库内容为 SynomosAI 的**理论站位与工具化探索**，不代表任何已获认证、已商业化交付或已服务特定客户的声明；文中涉及的 ISO/IEC 42001、NIST AI RMF、GB/Z 185 等外部标准与条款信息为公开资料转述，正式引用前请**独立核实**。API、授权码与形象大使等为路线图（roadmap）事项，尚未上线。
