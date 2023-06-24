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
