# Study Companion · 学习伙伴

一个以章节 Markdown 文件保存学习状态、由 AI 灵活选择教学方式的个人学习 Skill。

**Keep learning state in Markdown; let the tutor adapt its explanations.**

适合持续学习一本书、一门课程或一个主题：记录学到哪里、还有什么疑问，下次接着学。核心指令不绑定某个模型或 Harness。

## 可以做什么

- 按章节和子章节保存学习目标、进度、必要上下文和下一步。
- 区分“已经讲解”“用户自述理解”“在提示后完成”和真实的独立表现。
- 接续同一知识点的再次提问，保留日期和反馈；按现有记录汇总知识列表及待解决问题。
- 按内容选择例子、对比、图示、推导、代码、互动 HTML、动画或视频。用户可以直接要求完整解释，不必先参加测验。
- 有实际需要时寻找合适的工具；HyperFrames、Remotion 等只是可选参考。

## 使用

将整个仓库目录作为 `study-companion` Skill 放到宿主支持的 Skill 目录中，保留 `assets/` 和 `references/`。

例如，在支持项目级 `.agents/skills/` 的 Harness 项目目录中：

```sh
mkdir -p .agents/skills
git clone https://github.com/ailiheizi/study-companion.git .agents/skills/study-companion
```

其他宿主按其 Skill 导入方式选择该文件夹或 `SKILL.md`。宿主尚不支持原生 Skill 时，也可以将主文件作为学习指令，提供当前章节记录；额外参考文件按需提供。

开始学习时可以说：

> 使用 study-companion，陪我学习计算机网络。学习记录保存在当前项目的 study 目录。先完整讲解三次握手，用你认为有帮助的形式呈现，不要先测验。

继续学习时：

> 使用 study-companion，接着上次的章节继续。先看我的学习记录。

查看整体情况时：

> 把已记录的知识点按章节列出来，看看哪些问题回答过、哪些还没解决，以及哪些反复讨论过。

实际的显式调用语法由宿主决定，例如 `$study-companion`、`@` 选择或其 Skill 菜单。

## 学习记录

优先使用用户指定或已有的学习目录。首次使用且能持久写入时，默认结构可以是：

```text
study/
└── chapters/
    ├── 网络基础.md
    └── 三次握手.md
```

每章保存当前目标、资料位置、学习进度、理解与疑问、继续所需的上下文和下一步。可使用[章节模板](assets/chapter-template.md)。实际学习数据与 Skill 安装目录分开保存；章节文件是状态来源，总览按需汇总。

同一章可以在同一个聊天中继续，也可以把最新文件交给另一个平台接续。

## 能力与边界

| 能力 | 需要什么 |
| --- | --- |
| 讲解、讨论、阅读用户提供的学习记录 | 能读取指令和文本的模型环境 |
| 自动保存和恢复章节文件 | 可访问的持久存储及实际读写工具 |
| 图示、互动 HTML、动画或视频 | 对应的生成、预览或渲染工具 |
| 搜索新的学习材料和工具 | 联网检索能力 |
| 电脑、手机或不同平台接续 | 最新章节文件可被新环境访问 |

无法持久写入时，Skill 会要求 AI 返回标为“待保存”的 Markdown，由用户保存后带到下一个环境。安装同一个 Skill 不会自动同步学习数据；手机远程访问、文件同步和视频渲染由宿主或外部工具提供。

Skill 是 AI 的工作指令，不能保证模型每次都准确执行，也不能仅凭一次回答测出长期掌握程度。当前已做格式、引用和续学／保存等情景检查，尚未逐一实测所有 Harness。使用时应检查记录是否实际更新。

## 文件

```text
study-companion/
├── SKILL.md                          # 教学、记录和续学规则
├── assets/chapter-template.md        # 新章节记录模板
└── references/presentation-tools.md  # 呈现方式和可选工具入口
```

## 参考

本 Skill 按个人学习需求独立编写，参考了 [tutor 的主题文件机制](https://github.com/adityakumar68/claude-study-skills/blob/main/tutor/SKILL.md)、[book-tutor 的按章学习方式](https://github.com/xixiaofinland/agent-skills/blob/main/skills/book-tutor/SKILL.md)、[Hammer 的学习状态维护](https://github.com/SebastianElvis/hammer/blob/main/skills/teach/SKILL.md)和 [OpenMAIC 的针对性帮助与独立复核](https://github.com/THU-MAIC/OpenMAIC/blob/main/skills/agent-runtime/zone-of-proximal-development/SKILL.md)。

可选呈现项目及入口见[工具参考](references/presentation-tools.md)。这些项目没有随本仓库捆绑，使用时按其当前说明、运行条件和许可处理。
