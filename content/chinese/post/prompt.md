---
title: "如何写好 prompt"
date: 2026-03-15T17:00:00+08:00
lastmod: 2026-03-15T17:00:00+08:00
draft: false
keywords: [AI, 提示词]
description: ""
tags: [AI, 提示词]
categories: [经验分享]
author: "Jinhao Xu"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: true
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

<!--more-->

<style>
.post-content .table-wrapper > table {
  table-layout: fixed !important;
  width: 100% !important;
}
.post-content .table-wrapper > table td,
.post-content .table-wrapper > table th {
  word-break: break-word !important;
  white-space: normal !important;
}
.post-content .table-wrapper > table th:nth-child(1), .post-content .table-wrapper > table td:nth-child(1) { width: 30% !important; }
.post-content .table-wrapper > table th:nth-child(2), .post-content .table-wrapper > table td:nth-child(2) { width: 50% !important; }
.post-content .table-wrapper > table th:nth-child(3), .post-content .table-wrapper > table td:nth-child(3) { width: 20% !important; }
</style>

## 资源

### prompt

| 项目名 | 简介 | 链接 |
| :---: | :---: | :---: |
| **f/prompts.chat** | 社区驱动的prompt集合，以及可免费获取的书籍 | [仓库](https://github.com/f/prompts.chat)<br>[社区](https://prompts.chat/)<br>[书籍](https://cloud.tsinghua.edu.cn/f/b613e3bf9f2942719d18/) |
| **dair-ai/Prompt-Engineering-Guide** | 全面的提示工程理论指南，涵盖从基础到高级的技术 | [仓库](https://github.com/dair-ai/Prompt-Engineering-Guide)<br>[网址](https://www.promptingguide.ai/zh) |
| **x1xhlol/system-prompts-and-models** | 收录了 Cursor, Claude Code, Gemini 等AI工具的内置系统提示词 | [仓库](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools) |

### skills

| 项目名 | 简介 | 链接 |
| :---: | :---: | :---: |
| **anthropics/skills** | Anthropic 发布的 Agent Skills 标准库，包含文档处理、代码生成等专业技能。 | [仓库](https://github.com/anthropics/skills) |
| **openai/skills** | OpenAI 为 Codex 和 GitHub Copilot 准备的技能目录，侧重于编程任务的标准化流程。 | [仓库](https://github.com/openai/skills) |
| **VoltAgent/awesome-agent-skills** | 收录了超过 500 个来自官方和社区的技能，涵盖从爬虫、数据分析到网络安全的各领域。 | [仓库](https://github.com/VoltAgent/awesome-agent-skills) |
| **K-Dense-AI/scientific-skills** | 专为科研人员设计，包含论文解读、数据建模、学术绘图等专业学术技能包。 | [仓库](https://github.com/K-Dense-AI/claude-scientific-skills) |



## 如何写好 prompt
本节内容主要来自于书籍 *The Interactive Book of Prompting: A Guide to Crafting Clear and Effective Prompts*。

### 好的 prompt 由什么组成

1. 角色
    ```
    "You are a [profession] with [X years] of experience in [specialty]"
    "Act as a [role] who is [characteristic]"
    "You are an expert [field] helping a [audience type]"
    ```
2. 上下文：提供背景信息
    ```
    I'm building a Node.js REST API using Express.js. The API handles user authentication with JWT tokens. When a user tries to access a protected route, they're getting a 403 error even with a valid token. Here's the relevant code: [code]
    ```
3. 任务：明确要达到的目的
    ```
    Edit this essay for grammar and clarity, maintaining the original tone but reducing wordiness by 20%
    ```
4. 约束：长度、内容、风格、范围等
    ```
    "Keep your response under 200 words"
    "Do not include any code examples"
    "Use a formal, academic tone"
    "Only consider options available in Python 3.10+"
    ```
5. 格式：指定输出列表、MD、JSON等
    ```
    "Return as JSON with keys: title, description, priority"
    "Format as a markdown table with columns: Feature, Pros, Cons"
    ```
6. 示例：给出示例供模型参考
    ```
    Classify these support tickets by urgency.

    Examples:
    "My account was hacked" → Critical
    "How do I change my password?" → Low
    "Payment failed but I was charged" → High

    Classify: "The app crashes when I open settings"
    ```

### 具体技巧

**基于角色的提示**

略

**思维链**

思维链（Chain of Thought, CoT）提示通过给出解决问题的步骤，可以显著提高AI在复杂推理任务上的能力。

其使用方式主要如下：
1. 简单的触发短语
    ```
    "Let's think step by step."
    "Think through this carefully."
    ```
2. 给出思考步骤
    ```
    Before giving your final answer:
    1. Identify what information is given
    2. Determine what we need to find
    3. Plan your approach
    4. Execute each step, showing work
    5. Verify your answer
    ```
3. 给出样本
    ```
    Example:
    Q: A baker has 24 cupcakes. She puts them equally into 4 boxes. Then she eats 2 cupcakes from one box. How many cupcakes total remain?
    A: Let's work through this:
    - Total cupcakes: 24
    - Cupcakes per box: 24 ÷ 4 = 6
    - After eating 2 from one box: 6 - 2 = 4 cupcakes in that box
    - Total remaining: (3 boxes × 6) + 4 = 18 + 4 = 22 cupcakes

    Now solve:
    xxx
    ```

**少样本学习**

| 方法 | 样本 |
|:---:|:---:|
| Zero-shot | 0 |
| One-shot | 1 |
| Few-shot | 2~5 |
| Many-shot | 5+ |

典型例子：
```
[Example 1]
Input: [input 1]
Output: [output 1]

[Example 2]
Input: [input 2]
Output: [output 2]

[Example 3]
Input: [input 3]
Output: [output 3]

Now do this one:
Input: [new input]
Output:
```

对于平常的代码生成、优化任务，可以先附上已有的代码，要求模型生成与之风格类似、接口相同的代码。

**结构化输出**

基本格式技巧：
1. 列表
    ```
    Format: Numbered list with a brief explanation for each.
    ```
2. 表格
    ```
    Format as a markdown table with columns:
    | Framework | Best For | Learning Curve | Performance |
    ```
3. 标题和节
    ```
    Structure your response with these sections:
    ## Executive Summary
    ## Strengths
    ## Weaknesses
    ## Recommendations
    ## Risk Assessment
    ```
4. 使用大写进行强调
    ```
    IMPORTANT: Keep the summary under 100 words.
    NEVER add information not present in the original.
    ALWAYS maintain the original tone and perspective.
    DO NOT include your own opinions or analysis.
    ```

此外，可以选择其他机器可读的数据格式，如JSON、YAML、XML等。

JSON适用于程序解析：
1. API响应
2. 严格的类型要求
3. JavaScript/Web集成
4. 紧凑表示

YAML适用于人类可读：
1. 配置文件
2. 需要添加注释
3. 开发运维/基础建设
4. 深嵌套结构

当然，也可以利用分隔符如`===`, `---`, `[SECTION]`等自由构建你想要的格式，并且可以在不同部分指定不同的格式。例如：
```
Research this topic and provide:

### PART 1: EXECUTIVE SUMMARY
[2-3 sentence overview]

### PART 2: KEY FINDINGS
[Exactly 5 bullet points]

### PART 3: DATA TABLE
| Metric | Value | Source |
|--------|-------|--------|
[Include 5 rows minimum]

### PART 4: RECOMMENDATIONS
[Numbered list of 3 actionable recommendations]

### PART 5: FURTHER READING
[3 suggested resources with brief descriptions]
```

**迭代优化**

通过观察模型输出，找出prompt里的不足之处并修改，重复这个过程。

此外，还可以使用元技术：使用模型本身来帮助改进提示。例如：
```
I used this prompt:
"[your prompt]"

And got this output:
"[model output]"

I wanted something more [describe gap]. How should I modify my prompt to get better results?
```
或者为了简便起见，直接将需要优化的prompt粘贴给模型，然后按照之前介绍的方法，写一个元prompt，让模型对prompt进行优化。

**智能体 & 技能**

智能体是一个能自动规划、执行、迭代的AI系统。它主要包括几个部分：规划、执行、观测、调整。相应地，提示词可分为：
1. 系统提示词：智能体的身份
2. 规划提示词：如何思考
3. 工具提示词：如何行动
4. 恢复提示词：如何处理失败

Skill实质上是将解决特定领域或任务的prompt封装在一起，形成标准化、可复用、可自主调用的技能包。它通常包括SKILL.md、参考文档、脚本&工具、配置等。

在SKILL.md里，通常包括这个skill的名字、描述、实施细节、参考材料等。

## 总结

1. 描述清晰、具体

    避免模糊的表达如`Make this better` 、`Write about climate change`。尽量说清楚自己的要求或问题。

2. 提供上下文

    给模型提供对解决问题有帮助的信息。

3. 引导而非提问

    像老师一样对模型循循善诱。例如，对于复杂任务，引导它的推理过程：`Think through this using the following steps: 1. xxx 2. xxx 3. xxx`

4. 控制输出结构

    指定模型输出的格式。

5. 迭代并优化

    第一次写的prompt往往不是最好的，观察输出并修改prompt。此外，也可以让模型来优化你的prompt。

6. 使用可复用的Skill

    对于一些优秀的提示词，我们可以将其固化在文档中，每一次使用都可以直接调用。

7. 验证和确认

    不要轻信模型的输出，可以通过以下几点来进行确认：
    1. 请求模型的推理过程
    2. 要求模型从多角度看待问题
    3. 指定模型要检查的对象


个人认为，写一个好的prompt就类似PUA[^1]：
1. 强制对方接受一个自我认同
2. 清晰地表达自己的意见
3. 引导对方以得到自己想要的答案
4. 明确指出禁止对方做的事

[^1]: 在中文语境中，PUA指在一段关系中一方通过言语打压、行为否定、精神打压的方式对另一方进行情感操纵和精神控制。来源：[百度百科](https://baike.baidu.com/item/PUA/5999185)。

也就是说，在与模型沟通中，要让自己占据主导地位。