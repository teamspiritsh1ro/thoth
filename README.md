# Thoth

**专业文献检索与阅读 · Literature Search & Reading for Codex**

一个将课程检索与阅读方法转化为可执行步骤的 Codex 技能：实际寻找中英文文献，核实来源与访问路径，完成有证据定位的初读。

A Codex skill for finding Chinese and English scholarly literature, verifying sources and access routes, and producing evidence-grounded preliminary readings.

`thoth` 是仓库名称；技能名称保留为“专业文献检索与阅读”，调用名为 `literature-search-reading`。

## 安装到 agent

在 agent 中发送：

```text
请使用 $skill-installer，安装这个仓库里的技能：
https://github.com/teamspiritsh1ro/thoth/tree/main/skills/literature-search-reading
```

如果提示同名技能已存在，先备份已有版本，再明确选择是否更新；不要盲目覆盖个人改动。安装方式参考 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 调用示例

检索并初读：

```text
请使用 $literature-search-reading，围绕“数字技术与乡村空间重构”
检索中英文文献并完成初读。给出核实后的访问路径、实际检索记录、
逐篇论证梳理、阅读范围和待解决的问题。篇数与深度按我的时间预算确定。
```

只读指定论文：

```text
请使用 $literature-search-reading，初读我提供的论文，
梳理研究问题、既有解释、论证证据和结论边界，不额外开展主题检索。
```

只要检索方案：

```text
请使用 $literature-search-reading，只制定检索方案，暂不执行搜索或阅读。
```

## 新增：我自己检索，技能提供查询内容和网页

把含研究主题的一段话发给技能，即可得到简明中英文概念词组、几组可复制查询式或高级检索行、对应检索网站、输入位置和调整顺序。原有实际检索、来源核验和初读功能全部保留；明确要自己检索时才启用这个指导模式。

```text
请使用 $literature-search-reading 的手动检索辅助模式。
我的研究想法是：【粘贴一段包含研究主题的话】
请按课件方法给我中英文概念词组、几组可直接使用的检索式或高级检索行、
对应的网站链接和操作顺序。我自己检索，暂时不要代查论文。
```

技能按照课件组织概念，区分同义、近义与相关概念，再进行组内扩展、组间组合；知网给逐行配置，WoS按适用界面给字段式，其他平台按各自支持的方式输入。网站优先来自课件，按任务选择，不要求全部使用。

未提交的查询标为“拟执行”，候选术语不冒充文献已确认。你可以回传实际检索式及少量结果，让技能迭代；随后要求初读时，仍执行原有阅读标准。

详见[手动检索辅助](skills/literature-search-reading/references/manual-search-guide.md)和[课件网站入口](skills/literature-search-reading/references/search-entrypoints.md)。

## 它怎样工作

1. **组织概念**：拆分对象、现象、结果和情境，以真实文献校准中英文词语，区分同义、近义及相关概念。
2. **执行查询**：落实组内扩展、组间组合和迭代，按实际入口支持的语法查询，保留真实查询与筛选记录。
3. **核实来源**：检查书目与版本，提供期刊、DOI、机构库或已有文件等访问路径；下载可选。
4. **追踪引文**：需要扩展领域认识时进行适量双向追踪，分别标记线索、核验、阅读和轮次状态。
5. **阅读论证**：梳理作者回应的争论、问题、主张、证据及其支持强度，区分定量、质性和综述文献。
6. **核对交付**：让最终声明对应来源、阅读范围和真实操作；缺口如实保留。

访问路径是检索产出的最低要求，**不能替代阅读**。全文可得、解析完成和实际读过是不同状态。默认执行检索与初读；只有明确要求方案时才以方案为终点。

## 环境与边界

- 需要可读取本地文件的 Codex 环境；联网检索还需要可用的搜索、网页或数据库工具。
- 不绑定某个搜索服务，不附账号或 API 密钥，不要求付费数据库、订阅、子智能体或下载每篇论文。
- 数据库受阻时使用公开替代渠道，同时保留概念组织与来源核验；普通网页关键词搜索不冒充专业数据库布尔检索。
- 能读到摘要时仅做摘要初读，不补写未提供的理论、样本或方法细节。
- 这是可检查的工作流程，不保证穷尽文献、自动准确或替代学术判断。

## 文件入口

| 文件 | 用途 |
|---|---|
| [SKILL.md](skills/literature-search-reading/SKILL.md) | 核心工作流和范围控制 |
| [检索工作流](skills/literature-search-reading/references/search-workflow.md) | 概念组、真实查询、入口检查与引文追踪 |
| [阅读工作流](skills/literature-search-reading/references/reading-workflow.md) | 阅读状态、论证梳理和证据边界 |
| [工作底稿](skills/literature-search-reading/assets/literature-workbench.md) | 按任务选用的简洁记录模板 |
| [方法来源](skills/literature-search-reading/references/source-notes.md) | 课程页码索引、方法与执行补充的区别 |
| [验证场景](skills/literature-search-reading/references/validation-scenarios.md) | 行为验证设计，不是已通过的测试日志 |

此前维护做过小规模真实检索、指定论文阅读、摘要限制和方案范围检查，并在发现查询变体落实不足后修正和复测。这些内部运行记录未随仓库发布，不能当作可公开复现的基准成绩。本次开源打包检查文件结构、相对链接和发布范围，没有重新运行完整文献任务。

## English Explanation

Thoth packages **literature-search-reading**, a Chinese-first Codex skill for actual literature retrieval and preliminary reading. It uses concept decomposition, source-confirmed terminology, within-group expansion, cross-group combinations, iterative searches, and task-appropriate citation tracing.

Install with `$skill-installer` using the skill-folder URL above. Then ask:

```text
Use $literature-search-reading to find and preliminarily read Chinese and English
papers on my research question. Provide verified access routes, actual queries,
argument-and-evidence summaries, reading coverage, and explicit limitations.
```

The skill supports topic searches, reading specified papers, and explicitly requested plan-only work. A verified access route is the minimum retrieval deliverable; downloading is optional, but reading still requires examining the relevant content. Access and reading states are tracked separately. It does not treat keyword strings as database Boolean searches, reference lists as completed citation tracing, or extracted text as fully read papers.

The instructions primarily use Chinese. Search tools and lawful source access must be supplied by the host environment. No paid database, API credential, subagent, or original course archive is required. The workflow does not guarantee exhaustive coverage or correct model behavior. The validation scenarios describe tests to run, not benchmark results.

## 许可证与材料来源 / License and provenance

本仓库原创的技能指令、模板与项目文档采用 [MIT License](LICENSE)。原始课件、论文、第三方平台及其内容不随仓库分发，也不受此许可证再授权。方法出处及边界见 [第三方材料说明](THIRD_PARTY_NOTICES.md)。

Original skill instructions, templates, and project documentation are available under the MIT License. Original course slides and article full texts are not included or relicensed. See the third-party notices for provenance and scope.
