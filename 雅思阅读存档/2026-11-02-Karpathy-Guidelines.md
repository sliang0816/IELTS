# Karpathy Guidelines

- 导入日期：2026-11-02
- 类型：粘贴 / 原文

## 原文 / 译文

# Karpathy Guidelines

> 卡帕西准则

Behavioral guidelines to reduce common LLM coding mistakes, derived from Andrej Karpathy's observations on LLM coding pitfalls.

> 这些行为准则旨在减少大语言模型在编程中常见的错误，源自安德烈·卡帕西对大语言模型编程陷阱的观察。

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

> **权衡：**这些准则偏向谨慎而非速度。对于琐碎的任务，请自行判断。

## 1. Think Before Coding

> 1. 编码之前先思考

**Don't assume. Don't hide confusion. Surface tradeoffs.**

> **不要臆断。不要掩饰困惑。要摆明权衡取舍。**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

> 在动手实现之前：
> - 明确说明你的假设。如果不确定，就提问。
> - 如果存在多种解读，把它们列出来，不要悄悄选一种。
> - 如果存在更简单的方法，请说出来。有正当理由时要提出异议。
> - 如果有不清楚的地方，先停下来。指出让你困惑的地方，然后提问。

## 2. Simplicity First

> 2. 简洁优先

**Minimum code that solves the problem. Nothing speculative.**

> **用最少的代码解决问题。不做任何推测性的设计。**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

> - 不添加被要求之外的功能。
> - 不为只用一次的代码创建抽象。
> - 不添加没有被要求的“灵活性”或“可配置性”。
> - 不为不可能发生的场景编写错误处理。
> - 如果你写了200行而它本可以只有50行，就重写它。

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

> 问问自己：“资深工程师会认为这过于复杂吗？”如果会，就简化。

## 3. Surgical Changes

> 3. 精准修改

**Touch only what you must. Clean up only your own mess.**

> **只改你必须改的。只清理你自己造成的混乱。**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

> 在编辑现有代码时：
> - 不要“改进”相邻的代码、注释或格式。
> - 不要重构没有出问题的东西。
> - 与现有风格保持一致，即使你会用不同的方式去做。
> - 如果你注意到无关的死代码，可以提一下，但不要删除它。

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

> 当你的改动产生了遗留项时：
> - 删除因你的改动而不再被使用的导入、变量和函数。
> - 除非被要求，否则不要删除原本就存在的死代码。

The test: Every changed line should trace directly to the user's request.

> 检验标准：每一行被修改的代码都应能直接追溯到用户的请求。

## 4. Goal-Driven Execution

> 4. 目标驱动的执行

**Define success criteria. Loop until verified.**

> **定义成功标准。循环迭代直到验证通过。**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

> 把任务转化为可验证的目标：
> - “添加验证”→“为无效输入编写测试，然后让测试通过”
> - “修复这个缺陷”→“编写一个能复现它的测试，然后让测试通过”
> - “重构X”→“确保重构前后测试都能通过”

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

> 对于多步骤任务，请说明一个简要计划：

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

> 1. [步骤] → 验证：[检查项]
> 2. [步骤] → 验证：[检查项]
> 3. [步骤] → 验证：[检查项]

## 生词

| 单词 | 音标 | 词性 | 释义 | 例句 |
|---|---|---|---|---|
| derive | /dɪˈraɪv/ | v. | 源自，由…得出 | Many English words are derived from Latin. |
| pitfall | /ˈpɪtfɔːl/ | n. | 陷阱，隐患 | Students should be aware of the common pitfalls in the exam. |
| bias | /ˈbaɪəs/ | v. | 使偏向 | Personal experience can bias our judgment. |
| caution | /ˈkɔːʃn/ | n. | 谨慎 | Investors are advised to act with caution. |
| trivial | /ˈtrɪviəl/ | adj. | 琐碎的，不重要的 | They argued over a trivial matter. |
| explicitly | /ɪkˈsplɪsɪtli/ | adv. | 明确地 | The rules explicitly forbid the use of phones. |
| interpretation | /ɪnˌtɜːrprɪˈteɪʃn/ | n. | 解释，解读 | The data allows several different interpretations. |
| warrant | /ˈwɔːrənt/ | v. | 使有必要，证明…有理由 | The situation does not warrant such a drastic response. |
| speculative | /ˈspekjələtɪv/ | adj. | 推测性的，投机的 | The report was based on speculative claims rather than facts. |
| abstraction | /æbˈstrækʃn/ | n. | 抽象，抽象概念 | Mathematics relies heavily on abstraction. |
| adjacent | /əˈdʒeɪsnt/ | adj. | 相邻的 | The library is adjacent to the main building. |
| simplify | /ˈsɪmplɪfaɪ/ | v. | 简化 | The new system will simplify the application process. |
| verify | /ˈverɪfaɪ/ | v. | 验证，核实 | Researchers must verify their results before publication. |
| criteria | /kraɪˈtɪriə/ | n. | 标准（criterion的复数） | The selection criteria are clearly stated. |
| clarification | /ˌklærəfɪˈkeɪʃn/ | n. | 澄清，说明 | The students asked the teacher for clarification. |
| behavioral | /bɪˈheɪvjərəl/ | adj. | 行为的;关于行为规范的 | # Karpathy Guidelines

Behavioral guidelines to reduce common LLM coding mistakes, derived from Andrej Karpathy's observations on LLM coding pitfalls. |
| tradeoff | /ˈtreɪdˌɔf/ | n. | 权衡;取舍(为得到某物而不得不放弃另一物) | **Tradeoff:** These guidelines bias toward caution over speed. |
| scenario | /səˈnɛriˌoʊ/ | n. | 情景;设想的情况 | - No error handling for impossible scenarios. |
| surgical | /ˈsɜːrdʒɪkəl/ | adj. | 精准的、外科手术式的(只改动必要之处,不波及其他) | Surgical Changes

**Touch only what you must. |
| verifiable | /ˈvɛrɪˌfaɪəbəl/ | adj. | 可验证的;可核实的(指目标能通过测试等方式客观检验是否达成) | Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. |
