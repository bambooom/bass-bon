Brief overview of chapters:

- Basics: Introduction to prompt engineering and fundamental techniques
- Basic Applications: Simple, practical applications of prompt engineering
- Intermediate: Research-based PE techniques with moderate complexity
- Applied Prompting: Comprehensive PE process walkthroughs contributed by community members
- Advanced Applications: Powerful, and more complex applications of prompt engineering
- Reliability: Enhancing the reliability of large language models (LLMs)
- Images: Prompt engineering for text-to-image models, such as DALLE and Stable Diffusion
- Prompt Injection: Hacking, but for prompt engineering
- Tooling: A review of various prompt engineering tools and IDEs
- Prompt Tuning: Refining prompts using gradient-based techniques
- Miscellaneous: A collection of additional topics and techniques related to prompt engineering

no need to follow the order to read, only need to learn basics first.

## Basics ✅

- `确保答案完全正确` `确保输入正确数量的零`
- 给 AI 分配一个角色: `你是一名医生` `你是一名律师`
- few shot prompting: more examples
- 包括上下文、指令式的提示词和多个输入-输出的示例
- 问题则是简单的单一问题
- components: 角色 + 指令/任务 + 问题 + 上下文 + 示例(few shot)
- QA 格式的标准提示
- 使用风格输入提示将大大提高回答的质量：`以拥有20多年经验和多个博士学位的[领域]专家的风格和水平写作。在回答中优先考虑有建设性的、不太知名的建议。使用详细的例子进行解释，尽量少离题和耍幽默。`
- 描述符（discriminator）: `有趣的`、`简短的`、`不友好的`、`学术语法`
- setting:
  - 高热度生成更难预料及富有创造性的结果，低热度则更保守。例如热度为 0.5 时模型生成内容将比 1.0 更容易预测且创造性更少
  - top p: 选择累积概率超过该阈值的最佳词汇
  - 较高的热度或 top p 会生成更不可预测且有趣的结果，但同时也增加了错误或无意义文本的可能性。相反较低的热度或 top p 则生成更保守和可预测的结果，但也可能导致重复或乏味。

## Basic Applications ✅

- `生成包含此信息的表格`，将信息表格化展示
- [writing emails](https://learnprompting.org/docs/basic_applications/writing_emails)
  - `Generate a summary of this and a list of action items`
- blog: 列提纲，然后让GPT简化，再利用提纲让GPT填充写成全文
- code assistance:
  - Simulating a Web Server:
  ```
  Act as an Apache web server. How would you respond to these HTTP headers?

  GET /example HTTP/1.1
  Host: www.example.com
  ```
  - Simulating a Command Line:
  ```
  Act as Debian Linux command shell. Please respond to my commands as the terminal would, with as little explanation as possible.
  My first command is: ls -l
  ```
- 指定写作风格或指定某位著名的作者
- 假设我是一名 5 岁的孩童，请为我总结这个：[在此处粘贴文本]

## Intermediate

- [chain of thoughts](https://learnprompting.org/zh-Hans/docs/intermediate/chain_of_thought), 鼓励大语言模型解释其推理过程，在样例中解释推理过程，大语言模型在回答提示时也会显示推理过程。这种推理的解释往往会引导出更准确的结果。
- 零样本思维链：结尾附加“让我们一步步思考。”
- Self-consistency：生成多个思路链，然后取多数答案作为最终答案
- 最少到最多提示过程: 首先将问题分解为子问题，然后逐个解决，每一步都引入了上一步连接的结果
- 关键要素:
  - “基本事实的重要性不大”
  - 标签空间很重要 (all the possible labels for a given task)
  - 格式很重要: 因为它指示大语言格式如何正确地格式化其对提示的答案。

## Applied Prompting
- 多项选择题:
  - “让我们一步一步地解释”
  - 将选项分类，`Identify each choice as strengthens, weakens or doesn't impact the argument.`
  - `Give the expression as answer, not a number` to disable computation.
- 讨论性问题
  - `写一篇高度详细的论文，包括引言、正文和结论段，回答以下问题:`
  - 开放问题改写成明确的定义问题：`写一篇高度详细的讨论回答，按照论文结构回答以下提示: 解释内战的原因以及扩张是否在冲突中起了作用。附上支持您论点的证据。`
  - `我正在撰写一篇详细的短文，回答以下提示:`... `这是我目前的情况:`... `写下我文章的下一段。`
  - 逐步地写作并在每个步骤上进行迭代
- [simple chatbot](https://gist.github.com/jayo78/79d8834e6e31bf942c7b604e1611b68d)

## Advanced Application
- LLMs Using Tools: MRKL Systems1 (Modular Reasoning, Knowledge and Language, pronounced "miracle"): 结合了LLMs（神经计算）和像计算器（符号计算）这样的外部工具，用于解决复杂问题。
  - 一个简单的MRKL系统示例是一个可以使用计算器应用程序的 LLM
  - [dust.tt](https://dust.tt/w/ddebdfcdde/a/98bdd65cb7) 的一个例子
  - more examples:
    - [使用LangChain构建](https://api.python.langchain.com/en/latest/modules/agents.html#langchain.agents.MRKLChain)
    - 最初由[ai21](https://www.ai21.com/)开发
- 具有推理和行动能力的LLMs：ReAct（reason & act)，被视为具有推理和行动能力的MRKL系统
  - HotPotQA：思想，行动，观察循环
- 代码推理：是另一个MRKL系统的例子
  - [解决数学问题的例子](https://github.com/trigaten/Learn_Prompting/blob/main/docs/code_examples/PAL.ipynb)
