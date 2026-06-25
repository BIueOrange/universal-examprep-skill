# 🎓 通用期末考试 1天极速备考智能教练 (Universal Exam Cram Coach - LLM Wiki V2.0)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Agent: Antigravity](https://img.shields.io/badge/Agent-Antigravity-orange.svg)](#)
[![Version: 2.0](https://img.shields.io/badge/Version-2.0--LLM--Wiki-brightgreen.svg)](#)

这是一个**基于 LLM Wiki 架构重构**、**全科通用**的期末考试极速备考 AI 智能体技能（Agent Skill）V2.0 版本。

只要将本技能导入支持的智能体（如 VS Code 智能体插件、Cursor 或网页版 GPTs/Gemini），并提供你想要复习的科目资料，智能体就会化身你的**物理防幻觉私人专属备考教练**，带你在 1 天内突击通关。

---

## 🚀 V2.0 重大更新特性 (What's New)

* **⚡ LLM Wiki 目录结构化加载**：丢弃了原先庞大且容易撑爆上下文的单个 Markdown 答案文件。升级为按章节/阶段的 Wiki 物理切片（`references/wiki/`），Agent 会根据复习进度 **Lazy Load (惰性加载)** 对应章节，**Token 消耗直降 90%**，长对话不再卡顿。
* **🛠️ scripts/ingest.py 一键冷启动**：告别了手动建立题库与 Markdown 文件的繁琐操作。学生只需提供大纲或真题，由 Agent 或本地 Python 脚本一键解析，自动在后台分割好 Wiki 章节、题库并初始化进度表，实现“零摩擦”启动。
* **🎯 标准真题库 quiz_bank.json 抽题**：测试题由“AI 即兴编造”升级为“标准真题库抽测”，规避了 AI 出无解错题、弱智题的毛病。
* **🏃 测试逃生通道 (Hint & Skip)**：针对测试关卡设计了“查看提示”与“2次答错跳过并归档”机制，防止学生因主观题表述差异或卡壳而被死锁在当前阶段。

---

## 📂 技能包目录结构

```text
universal-examprep-skill/
  ├── SKILL.md            # 技能定义核心文件（含惰性加载指令与物理防幻觉协议）
  ├── README.md           # 本使用说明
  ├── scripts/
  │     └── ingest.py     # 一键大纲解析与本地 Wiki 切片脚本
  └── templates/          # 初始化模板
        ├── study_plan_template.md        # 阶段备考突击表模板
        ├── study_progress_template.md    # 进度打卡自测追踪表模板
        └── quiz_bank_template.json       # 结构化真题库 JSON 模板
```

---

## 🛠️ 如何导入并使用本技能

### 方式 1：导入本地 AI 编辑器/插件（如 VS Code、Cursor 等）- 【推荐】
1. 下载或克隆本技能文件夹 `universal-examprep-skill` 到你的电脑。
2. 将其放入你的智能体自定义技能目录下（例如工作区根目录下的 `.agents/skills/` 文件夹中）。
3. 开启新对话，上传你的考试大纲（PDF/图片/文档均可）。
4. 对 AI 说：“*教练，这是我的复习大纲，请在后台帮我解析并调用 `ingest.py` 初始化我的备考 LLM Wiki 空间。*”
5. 脚本运行完成后，AI 将根据生成的 `study_plan.md` 引导你开始按章节复习。

> **手动运行脚本方法**：
> 如果你想在本地命令行手动执行初始化，只需将解析好的大纲 JSON 传给脚本即可：
> ```bash
> python scripts/ingest.py --input raw_input.json --output-dir .
> ```

### 方式 2：网页端 AI 适配使用（如 ChatGPT, Claude, Gemini Advanced）
1. 复制 `SKILL.md` 的全部内容，粘贴到 AI 的**系统指令（System/Custom Instructions）**中。
2. 按照 `SKILL.md` 尾部的 `网页端运行适配指南 (Web Portability)`，将生成的 `quiz_bank.json` 或 `study_plan.md` 手动上传到当前的网页会话作为挂载知识库。
3. 对 AI 说：“*你好教练，请读取我挂载的进度，并开始对应阶段的复习。*”

---

## 📝 开源协议
本项目基于 **MIT License** 协议开源。欢迎大家提交 Pull Request 贡献更多科目的复习模板或辅助脚本！

**祝所有临考冲刺的学生考神附体，高分通关！🎓🔥**
