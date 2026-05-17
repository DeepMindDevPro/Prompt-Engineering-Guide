# DAIR.AI 提示词工程学习指南 (中文版)

> 基于 DAIR.AI Prompt Engineering Guide 项目全部核心文件的逐章深度核对与重构。
> 涵盖 `guides/`、`pages/introduction/`、`pages/techniques/`、`pages/applications/`、`pages/risks/`、`pages/agents/`、`pages/models/`、`pages/research/`、`pages/guides/`、`pages/prompts/` 等全部目录内容。

---

## 一、核心模块设计

| 模块名称 | 核心思想 | 关键技术点 |
| :--- | :--- | :--- |
| 模块一：基础范式 | 理解提示词的基本构成与交互原理，掌握与 LLM 沟通的最小单元 | 提示四元素（指令/上下文/输入数据/输出指示器）、LLM 参数（Temperature/Top-p/Max Length/Stop Sequences/Frequency Penalty/Presence Penalty）、Zero-shot / Few-shot、角色对话模式（system/user/assistant）、提示设计原则（明确具体/结构化输入输出/分隔符/任务分解） |
| 模块二：进阶推理 | 通过结构化推理策略引导模型"慢思考"，突破简单问答的局限 | CoT（Few-shot CoT + Zero-shot CoT "Let's think step by step" + Auto-CoT）、Self-Consistency、Tree of Thoughts、Generated Knowledge、Meta Prompting（结构导向 vs 内容导向） |
| 模块三：工具增强与智能体 | 将 LLM 与外部工具、检索系统协同，使其从"纯语言模型"进化为"能行动的系统" | RAG（Naive/Advanced/Modular 三代演进）、ReAct、ART、Prompt Chaining、Function Calling、AI Agents（规划/记忆/工具三组件）、Context Engineering、Deep Agents、AI Workflows vs Agents、Reasoning LLMs（推理时计算扩展/混合推理） |
| 模块四：自动优化与自我反思 | 利用算法自动搜索最优提示，并通过反思机制让智能体从错误中学习 | APE、Active-Prompt、Directional Stimulus Prompting、PAL、Reflexion（Actor/Evaluator/Self-Reflection 三角色） |
| 模块五：应用实践与前沿工具 | 将提示工程技术落地到真实业务场景，并掌握最新产品化工具 | 数据生成、代码生成、合成 RAG 数据集、合成数据多样性、职场分类案例、上下文缓存、微调、Prompt Function、4o 图像生成、Deep Research（o3 驱动的多步研究智能体） |
| 模块六：风险与安全 | 认识提示词的攻击面与模型固有缺陷，建立安全防线 | 对抗性提示（注入/越狱/泄漏）、防御策略（指令防御/参数化/格式化/对抗检测器/模型选择）、事实性幻觉、偏见（示例分布偏差/示例顺序偏差）、推理模型的过度思考/欠思考问题 |

---

## 二、7天循序渐进学习计划

| 天数 | 学习主题 | 重点目标 |
| :--- | :--- | :--- |
| Day 1 | 基础范式（上） | 理解提示词工程的定义与价值；掌握提示词四元素（指令、上下文、输入数据、输出指示器）；了解 LLM 全部可调参数（Temperature、Top-p、Max Length、Stop Sequences、Frequency/Presence Penalty）；掌握提示设计核心原则（明确具体、结构化输入输出、分隔符、任务分解） |
| Day 2 | 基础范式（下）+ 进阶推理（上） | 掌握 Zero-shot 与 Few-shot 的区别与适用场景；理解 Few-shot 中示例分布、格式与顺序的重要性；深入理解 CoT 的三种形态——Few-shot CoT、Zero-shot CoT（"Let's think step by step"）、Auto-CoT（问题聚类+示范采样） |
| Day 3 | 进阶推理（下） | 掌握 Self-Consistency（多路径投票）的采样与多数投票机制；理解 Tree of Thoughts 的树状搜索与回溯（BFS/DFS）；掌握 Generated Knowledge Prompting（先生成知识再推理）；认识 Meta Prompting（结构导向 vs 内容导向）的差异与优势 |
| Day 4 | 工具增强与智能体 | 理解 RAG 三代演进（Naive→Advanced→Modular）及优化手段（混合搜索/HyDE/重排序）；掌握 ReAct 的 Thought-Action-Observation 循环；了解 ART 自动化推理+工具调用；理解 Prompt Chaining 如何拆解复杂任务；认识 AI Agents 三组件（规划/记忆/工具）与 AI Workflows 的区别；理解 Context Engineering 对智能体可靠性的关键作用；了解 Reasoning LLMs（推理时计算扩展、混合推理模式、避免手动 CoT） |
| Day 5 | 自动优化与自我反思 | 理解 APE 如何自动搜索最优提示词（含发现超越"Let's think step by step"的提示）；了解 Active-Prompt 的不确定性驱动选择策略；掌握 PAL 的思路（自然语言→程序→解释器执行）；认识 Directional Stimulus Prompting（策略 LM 生成提示/暗示）；深入理解 Reflexion 框架——Actor/Evaluator/Self-Reflection 三角色如何让智能体从试错中自我改进 |
| Day 6 | 应用实践与前沿工具 | 掌握 Function Calling 的完整流程（工具定义→模型决策→代码执行→观察回传→最终响应）；了解数据生成与合成 RAG 数据集的方法（含领域特定生成与迭代式层级生成）；学习合成数据多样性技术（随机词注入+特征随机组合）；理解上下文缓存与微调的优化手段；认识 Prompt Function、4o 图像生成、Deep Research（o3 多步研究智能体，含使用技巧与局限） |
| Day 7 | 风险与安全 | 识别三种对抗性攻击：Prompt Injection、Jailbreaking、Prompt Leaking；掌握五种防御策略（指令防御、参数化组件、引号/格式化、对抗提示检测器、模型类型选择）；理解事实性幻觉的缓解方法（提供事实依据/降低概率参数/已知+未知示例）；认识偏见来源（示例分布偏差/示例顺序偏差）；了解推理模型的特殊风险（过度思考/欠思考/成本延迟/工具调用不稳定）；回顾全周知识体系，查漏补缺 |

---

## 三、核心概念速查表

**模块一 · 基础范式**
- **Zero-shot Prompting**：不提供任何示例，仅凭指令让模型完成任务——依赖指令微调与 RLHF 训练带来的泛化能力
- **Few-shot Prompting**：在提示中给出若干输入-输出示例，让模型通过上下文学习（In-context Learning）推断期望行为；注意示例的标签分布、格式一致性及顺序都会影响结果
- **Prompt Elements**：构成有效提示的四大组件——指令（做什么）、上下文（背景信息）、输入数据（待处理内容）、输出指示器（返回结构/格式）
- **提示设计原则**：明确具体（避免模糊指令）、结构化输入输出（JSON/XML/分隔符）、任务分解（复杂任务拆子任务）、迭代优化

**模块二 · 进阶推理**
- **Chain-of-Thought (CoT)**：三种形态——Few-shot CoT（提供推理步骤示范）、Zero-shot CoT（追加"Let's think step by step"）、Auto-CoT（问题聚类→自动生成推理链→构建示范）；是大模型的涌现能力
- **Self-Consistency**：对同一问题多次采样推理路径，再通过多数投票选出最一致的答案，替代 CoT 的贪心解码
- **Tree of Thoughts (ToT)**：将推理组织为树结构，模型可自我评估中间步骤（sure/maybe/impossible），结合 BFS/DFS 进行回溯与搜索，适用于需要战略前瞻的复杂决策
- **Meta Prompting**：结构导向而非内容导向的提示方法，关注问题的语法模式而非具体内容，比 Few-shot 更高效（Token 效率、零样本效能）

**模块三 · 工具增强与智能体**
- **RAG（检索增强生成）**：三代演进——Naive RAG（基础索引-检索-生成，存在精度/召回不足）、Advanced RAG（优化预检索/检索/后检索，含重排序与提示压缩）、Modular RAG（模块化可插拔，含混合搜索/HyDE/子查询等）；可微调检索器，知识可动态更新无需重训模型
- **ReAct**：交替执行 Thought（推理）→ Action（行动）→ Observation（观察），让模型能调用外部工具并基于观察结果继续推理；与 CoT 结合效果最佳
- **AI Agents**：LLM 驱动的自主系统，三大核心组件——规划（任务分解，含 CoT/ToT/Reflexion）、记忆（短期/长期/混合，含向量存储）、工具使用（Function Calling/MRKL/Toolformer/HuggingGPT）；区分 AI Workflows（预定义路径，高可控性）vs AI Agents（动态自主决策，高灵活性）
- **Context Engineering**：对智能体的系统提示、指令、用户输入、结构化输入输出、工具定义、RAG/记忆、状态/历史上下文进行系统性设计、测试与迭代；是构建可靠智能体的关键实践，比 Prompt Engineering 更广
- **Reasoning LLMs**：原生具备思维链推理能力的大模型（如 o3、Gemini 2.5 Pro、Claude 3.7 Sonnet）；核心特性包括推理时计算扩展（thinking effort: low/medium/high）、混合推理模式、避免手动 CoT（反而降低指令遵循能力）；设计模式涵盖 Agentic RAG、LLM-as-a-Judge、视觉推理

**模块四 · 自动优化与自我反思**
- **APE（自动提示工程师）**：用 LLM 生成候选指令→在目标模型上执行→按评估分数筛选最优提示；发现了超越人工设计的"Let's work this out in a step by step way to be sure we have the right answer."
- **PAL（程序辅助语言模型）**：让模型生成程序代码（如 Python），由解释器执行并返回精确结果，确保数值/逻辑推理的准确性
- **Reflexion**：三角色框架——Actor（执行动作，基于 CoT/ReAct）、Evaluator（评分轨迹）、Self-Reflection（语言反馈存入长期记忆）；将环境反馈转化为"自我反思"，使智能体在后续尝试中避免重复犯错；适用于试错学习、决策、编程等场景

**模块五 · 应用实践与前沿工具**
- **Function Calling**：LLM 检测何时需调用函数→输出结构化 JSON 参数→开发者代码执行实际函数→结果回传模型→生成最终响应；是智能体与外部 API 交互的核心机制；工具定义（名称/描述/参数）是决定调用质量的关键
- **合成数据多样性**：通过随机词注入（名词/动词/形容词随机组合）+ 随机特征选择 + 迭代式层级生成，解决 LLM 生成数据重复性高的问题
- **Deep Agents**：具备结构化规划、编排器-子智能体架构、外部持久记忆与上下文工程能力的高级智能体，能处理长周期复杂任务；核心特征——规划优于即兴推理、编排器委派子智能体、混合记忆检索（语义+智能体搜索）、验证机制
- **Deep Research**：OpenAI 基于 o3 的多步研究智能体，核心流程为 Search + Analyze + Synthesize；提示技巧包括清晰指令、关键词提供、动词引导、输出格式指定、文件上传；局限包括幻觉、技术领域综合能力不足
- **4o 图像生成**：GPT-4o 的原生图像生成能力（自回归架构），支持文本生图、图像编辑（Inpainting）、风格迁移、透明背景、图像文字渲染

**模块六 · 风险与安全**
- **Prompt Injection**：通过恶意输入覆盖原始指令，使模型执行攻击者意图的操作——防御手段包括指令防御、参数化组件、引号/格式化隔离、对抗提示检测器
- **Jailbreaking**：通过精心构造的提示绕过模型安全限制（如角色扮演模拟器/DAN）；ChatGPT 等已加护栏但仍可被新型攻击突破
- **示例偏见**：Few-shot 示例的类别分布不均会导致模型偏向多数类别；示例的排列顺序也会影响输出——建议使用平衡分布与随机排序
- **推理模型风险**：过度思考（overthinking）导致不必要的冗余输出；欠思考（underthinking）导致浅层响应；成本与延迟显著高于标准模型；工具调用能力不稳定（尤其并行调用）

---

## 四、项目目录与学习资源映射

| 项目目录 | 内容定位 | 对应学习模块 |
| :--- | :--- | :--- |
| `guides/` | 传统指南（intro→basic→advanced→applications→chatgpt→adversarial→reliability→miscellaneous） | 模块一、二、四、六 |
| `pages/introduction/` | 基础教程（basics/settings/elements/tips/examples） | 模块一 |
| `pages/techniques/` | 提示技术详解（zeroshot/fewshot/cot/consistency/tot/knowledge/ape/activeprompt/dsp/pal/react/rag/art/prompt_chaining/multimodalcot/graph/reflexion/meta-prompting） | 模块二、三、四 |
| `pages/applications/` | 应用场景（function_calling/generating/coding/synthetic_rag/generating_textbooks/workplace_casestudy/context-caching/finetuning-gpt4o/pf） | 模块五 |
| `pages/risks/` | 风险与安全（adversarial/factuality/biases） | 模块六 |
| `pages/agents/` | AI 智能体（introduction/components/function-calling/context-engineering/context-engineering-deep-dive/deep-agents/ai-workflows-vs-ai-agents） | 模块三 |
| `pages/models/` | 模型专档（chatgpt/gemini/gpt-4/llama/mistral/mixtral/code-llama/flan/olmo/phi-2/collection 等） | 全模块参考 |
| `pages/prompts/` | 提示词模板库（classification/coding/creativity/evaluation/information-extraction/image-generation/mathematics/question-answering/reasoning/text-summarization/truthfulness/adversarial-prompting） | 全模块实践 |
| `pages/research/` | 研究综述（rag/llm-agents/llm-reasoning/llm-recall/llm-tokenization/groq/guided-cot/infini-attention/trustworthiness-in-llms/synthetic_data/thoughtsculpt/rag_hallucinations/rag-faithfulness） | 模块三、六 |
| `pages/guides/` | 进阶独立指南（context-engineering-guide/reasoning-llms/deep-research/4o-image-generation/optimizing-prompts） | 模块三、五 |
| `notebooks/` | 实践笔记本（chatgpt-intro/chatgpt-adversarial/chatgpt-langchain/code-llama/function-calling/lecture/litellm-intro/mixtral/pal/rag/react/gemini-context-caching） | 全模块实践 |