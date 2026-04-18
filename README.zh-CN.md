[English](./README.md) | **简体中文**

# 荣格.skill

用有明确边界的荣格视角探索人格面具、阴影、投射、个体化与象征模式。它帮助反思，不宣称复刻荣格的心智，也不把解释当成已发现的隐秘心理事实。

[示例](#示例) · [安装](#安装) · [操作路由](#操作路由) · [来源](#来源) · [维护](#维护) · [致谢](#致谢与许可)

回答默认使用英文。明确请求中文时使用简体中文，除非指定其他变体。面向整个对话的语言选择持续生效，直到再次修改；仅针对一次回答或一个产物的要求只在该范围内生效，也尊重其他明确指定的语言。中文提问或切换本说明文档本身，不会改变回答语言。

## 示例

以下是本项目编写的示例回答提纲，不是历史人物原话、历史重演或临床结论。

### 为什么同事抢走我的工作功劳，会让我这么生气？

先看发生了什么：抢功可能是实际的不公平。荣格式提问可以探索这件事为何格外触动你，但不能先认定这是投射。即使没有发现内在联想，也可以处理功劳归属和边界。

### 一直扮演可靠的人让我很累，这是假自我吗？

主动选择的角色也能表达真实价值。先区分可靠和随时待命，再找出具体造成压力的要求。如果希望改变，可以尝试可行的边界，不必认定整个角色都需要抛弃。

### 反复做同一个梦，是不是意味着坏事将发生？

梦不能确立预言。先了解个人联想与近期情境，对比象征性和普通的解释，也允许意义保持不确定。不能仅凭梦中图像推断隐藏的创伤或作出诊断。

### 我可以既想独立，也想亲密吗？

可以借个体化的视角承认两种需要。探索实际取舍以及你希望保留的承诺。回答可以停在更清晰的区分上，不必强行安排练习。

## 安装

```bash
npx skills add justinhuangai/carl-jung-skill
```

使用 Skill 不需要 Python 维护工具。可以请求以荣格的视角分析问题，或显式调用 `carl-jung-skill`。如需切换中文，可明确说：“本次对话接下来请使用简体中文回答。”

## 操作路由

[SKILL.md](SKILL.md) 定义语言、证据与路由规则。先读取一个相关操作参考，按需补充研究材料。

| 路由 | 用途 |
|---|---|
| [阴影与投射](references/shadow-and-projection.md) | 探索强烈反应，但不预设投射 |
| [人格面具与自我](references/persona-and-self-split.md) | 角色要求与身份压力 |
| [个体化](references/individuation-navigation.md) | 相互冲突的需要与整合 |
| [原型与象征](references/archetypal-pattern-reading.md) | 对意象和叙事进行可选择的解读 |
| [自我探索边界](references/self-exploration-with-boundaries.md) | 不确定性、自主选择与适当停止 |

## 来源

目前有 **3 条独立来源记录**：一份不完整的大英百科传记和两份图书馆目录。仓库没有收录荣格著作的正文。目录对应《心理类型》和《原型与集体无意识》，可以支持版本及目录信息，不能支持引文或细致理论论断。此前标成 IEP 和《分析心理学的两篇论文》的记录实际上重复了同一大英百科网址，已移除。

[六份研究笔记](references/research/README.md) 是明确标记证据缺口的编辑性指南，不是完整文献综述。引用著作前请查看[来源清单](references/sources/README.md)。精确引文、有争议的历史论断及当前科学结论需要核对恰当来源。

## 边界

- 心理解释是可能性，不是他人隐秘动机的事实。
- 先考虑普通解释与实际伤害，再考虑内在心理解释。
- 尊重用户的目标、限制、自主选择及纠正；不同意不构成理论正确的证据。
- 不作诊断、不提供治疗、不推断所谓恢复的记忆，也不替代适当的专业支持。
- 不借助象征、历史权威或不可检验的解释向人施压或进行操控。

## 仓库结构

- [SKILL.md](SKILL.md)：精简的运行指令；版本保留为 `1.0.0`。
- [references/](references/)：五条操作路由和提炼框架。
- [references/research/](references/research/README.md)：六份主题研究笔记。
- [references/sources/](references/sources/README.md)：保存的来源内容与溯源信息。
- [scripts/](scripts/) 和 [tests/](tests/)：维护工具与回归测试。
- [README.md](README.md)：英文说明。

## 维护

在仓库根目录使用 Python 3.10 或更新版本运行：

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

核心检查与测试只依赖标准库。安装 Beautiful Soup 后，还会运行可选的 HTML 采集测试。网页/PDF 采集按需使用 `requirements.txt` 中的 requests、Beautiful Soup、pypdf，可通过 `python3 -m pip install -r requirements.txt` 安装。

`capture_web_source.py` 必须通过 `--language` 指定原文实际语言（`en`、`zh-CN`、其他语言标签，或不确定时用 `und`），保留原文而不翻译。`srt_to_transcript.py` 转换 SRT/VTT 文件。字幕下载需要可选的 `yt-dlp`，默认英文，先人工字幕再自动字幕。`--language zh-CN` 只选择明确标注的简体中文字幕；两种模式都不会回退到其他语言。命令行提示保持英文。

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

检查涵盖链接、元数据、重复文本与脚本行为，不证明历史论断、来源完整性、版权许可或临床有效性。修改时同步两份 README，并遵循[提炼框架](references/extraction-framework.md)。

## 致谢与许可

本项目由 Jackson Huang 维护，使用 [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill) 辅助构建。感谢 Nuwa 作者与贡献者提供工具。

项目原创内容使用 [MIT 许可证](LICENSE)。第三方原文、译文与目录记录保留各自的权利与条款，收录到仓库不表示改为 MIT 授权。
