---
title: "How to write a good prompt"
date: 2026-03-15T17:00:00+08:00
lastmod: 2026-03-15T17:00:00+08:00
draft: false
keywords: [AI, prompt]
description: ""
tags: [AI, prompt]
categories: [experience sharing]
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

## Resources

### prompt

| Project | Description | Links |
| :---: | :---: | :---: |
| **f/prompts.chat** | A community-driven prompt collection, plus free-access books | [Repository](https://github.com/f/prompts.chat)<br>[Community](https://prompts.chat/)<br>[Book](https://cloud.tsinghua.edu.cn/f/b613e3bf9f2942719d18/) |
| **dair-ai/Prompt-Engineering-Guide** | A comprehensive prompt engineering guide covering techniques from beginner to advanced levels | [Repository](https://github.com/dair-ai/Prompt-Engineering-Guide)<br>[Website](https://www.promptingguide.ai/zh) |
| **x1xhlol/system-prompts-and-models** | A collection of built-in system prompts from AI tools such as Cursor, Claude Code, and Gemini | [Repository](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools) |

### skills

| Project | Description | Links |
| :---: | :---: | :---: |
| **anthropics/skills** | Anthropic's official Agent Skills library, including professional capabilities such as document processing and code generation | [Repository](https://github.com/anthropics/skills) |
| **openai/skills** | OpenAI's skill catalog for Codex and GitHub Copilot, focused on standardized workflows for programming tasks | [Repository](https://github.com/openai/skills) |
| **VoltAgent/awesome-agent-skills** | A collection of 500+ skills from official and community sources, spanning web crawling, data analysis, cybersecurity, and more | [Repository](https://github.com/VoltAgent/awesome-agent-skills) |
| **K-Dense-AI/scientific-skills** | Designed for researchers, with specialized skill packs for paper interpretation, data modeling, academic visualization, and more | [Repository](https://github.com/K-Dense-AI/claude-scientific-skills) |



## How to Write Better Prompts
Most of this section is based on the book *The Interactive Book of Prompting: A Guide to Crafting Clear and Effective Prompts*.

### What Makes a Good Prompt

1. Role
    ```
    "You are a [profession] with [X years] of experience in [specialty]"
    "Act as a [role] who is [characteristic]"
    "You are an expert [field] helping a [audience type]"
    ```
2. Context: provide background information
    ```
    I'm building a Node.js REST API using Express.js. The API handles user authentication with JWT tokens. When a user tries to access a protected route, they're getting a 403 error even with a valid token. Here's the relevant code: [code]
    ```
3. Task: state the objective clearly
    ```
    Edit this essay for grammar and clarity, maintaining the original tone but reducing wordiness by 20%
    ```
4. Constraints: length, content, style, scope, etc.
    ```
    "Keep your response under 200 words"
    "Do not include any code examples"
    "Use a formal, academic tone"
    "Only consider options available in Python 3.10+"
    ```
5. Format: specify output format such as list, Markdown, JSON, etc.
    ```
    "Return as JSON with keys: title, description, priority"
    "Format as a markdown table with columns: Feature, Pros, Cons"
    ```
6. Examples: provide reference examples for the model
    ```
    Classify these support tickets by urgency.

    Examples:
    "My account was hacked" → Critical
    "How do I change my password?" → Low
    "Payment failed but I was charged" → High

    Classify: "The app crashes when I open settings"
    ```

### Practical Techniques

**Role-Based Prompting**

Omitted.

**Chain of Thought**

Chain-of-thought (CoT) prompting can significantly improve an AI model's performance on complex reasoning tasks by explicitly providing reasoning steps.

Common usage patterns include:
1. Simple trigger phrases
    ```
    "Let's think step by step."
    "Think through this carefully."
    ```
2. Provide explicit reasoning steps
    ```
    Before giving your final answer:
    1. Identify what information is given
    2. Determine what we need to find
    3. Plan your approach
    4. Execute each step, showing work
    5. Verify your answer
    ```
3. Provide worked examples
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

**Few-Shot Learning**

| Method | Number of Examples |
|:---:|:---:|
| Zero-shot | 0 |
| One-shot | 1 |
| Few-shot | 2~5 |
| Many-shot | 5+ |

A typical template:
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

For everyday code generation and optimization tasks, you can first provide existing code and ask the model to generate code with a similar style and the same interface.

**Structured Output**

Basic formatting techniques:
1. Lists
    ```
    Format: Numbered list with a brief explanation for each.
    ```
2. Tables
    ```
    Format as a markdown table with columns:
    | Framework | Best For | Learning Curve | Performance |
    ```
3. Headings and sections
    ```
    Structure your response with these sections:
    ## Executive Summary
    ## Strengths
    ## Weaknesses
    ## Recommendations
    ## Risk Assessment
    ```
4. Use ALL CAPS for emphasis
    ```
    IMPORTANT: Keep the summary under 100 words.
    NEVER add information not present in the original.
    ALWAYS maintain the original tone and perspective.
    DO NOT include your own opinions or analysis.
    ```

You can also choose other machine-readable formats such as JSON, YAML, and XML.

JSON is suitable for programmatic parsing:
1. API responses
2. Strict type requirements
3. JavaScript/Web integration
4. Compact representation

YAML is suitable for human readability:
1. Configuration files
2. Cases where comments are needed
3. DevOps/infrastructure scenarios
4. Deeply nested structures

You can also freely define your own structure using delimiters like `===`, `---`, and `[SECTION]`, and even assign different formats to different parts. For example:
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

**Iterative Improvement**

Observe the model output, identify shortcomings in your prompt, revise it, and repeat.

You can also use a meta technique: ask the model itself to improve your prompt. For example:
```
I used this prompt:
"[your prompt]"

And got this output:
"[model output]"

I wanted something more [describe gap]. How should I modify my prompt to get better results?
```
For convenience, you can also paste the prompt directly and write a meta-prompt based on the methods above, asking the model to optimize it.

**Agents & Skills**

An agent is an AI system that can plan, execute, and iterate autonomously. Its core components usually include planning, execution, observation, and adjustment. Accordingly, prompts can be categorized as:
1. System prompts: the agent's identity
2. Planning prompts: how to think
3. Tool prompts: how to act
4. Recovery prompts: how to handle failures

A Skill is essentially a packaged set of prompts for solving a specific domain problem or task, forming a standardized, reusable, and autonomously callable capability package. It typically includes SKILL.md, reference docs, scripts and tools, configuration, etc.

In SKILL.md, you usually include the skill name, description, implementation details, reference materials, and so on.

## Summary

1. Be clear and specific

    Avoid vague expressions like `Make this better` or `Write about climate change`. Describe your requirements or question as clearly as possible.

2. Provide context

    Give the model information that helps it solve the problem.

3. Guide, don't just ask

    Guide the model like a teacher. For complex tasks, for example, guide its reasoning process: `Think through this using the following steps: 1. xxx 2. xxx 3. xxx`

4. Control output structure

    Specify the format you want the model to return.

5. Iterate and refine

    The first prompt is often not the best one. Review the output and revise the prompt. You can also ask the model to refine your prompt.

6. Use reusable Skills

    For high-quality prompts, you can formalize them in documentation so they can be reused directly each time.

7. Verify and validate

    Do not blindly trust model outputs. You can verify them by:
    1. Asking for the model's reasoning process
    2. Requiring the model to examine the issue from multiple perspectives
    3. Specifying what the model must check


In my view, writing a good prompt is somewhat like PUA[^1]:
1. Establish a clear role for the other party to adopt
2. Express your requirements clearly
3. Guide the other party toward the answer you want
4. Explicitly state what is not allowed

[^1]: In the Chinese context, PUA refers to a situation in which one party in a relationship emotionally manipulates and mentally controls the other through verbal abuse, belittling behavior, and psychological pressure. Source: [BaiduWiki](https://baike.baidu.com/item/PUA/5999185).

In other words, when communicating with a model, you should keep the interaction under your direction.