# Agent学习

## ReACT

### Motivation

现有思维链方法的局限性：基于模型内部知识，缺乏外界知识。

“However, this “chain-of-thought” reasoning is a static black box, in that the model uses its own internal representations to generate thoughts and is not grounded in the external world, which limits its ability to reason reactively or update its knowledge. This can lead to issues like fact hallucination and error propagation over the reasoning process”

然而，这种“链式思考”的推理是一个静态的黑箱，模型使用其自身的内部表示生成想法，并未扎根于外部世界，这限制了其进行反应性推理或更新知识的能力。这可能会导致事实幻觉和推理过程中的错误传播等问题。

现有现有交互环境进行规划和执行方法的局限性：没有将模型自身推理与执行结合。

“However, they do not employ language models to reason abstractly about high-level goals or maintain a working memory to support acting, barring Huang et al. (2022b) who perform a limited form of verbal reasoning to reiterate spatial facts about the current state. Beyond such simple embodied tasks to interact with a few blocks, there have not been studies on how reasoning and acting can be combined in a synergistic manner for general task solving, and if such a combination can bring systematic benefits compared to reasoning or acting alone.”

然而，它们并未使用语言模型进行高层次目标的抽象推理或维护工作记忆以支持行动（Huang等，2022b 除外），Huang等人为重新阐述当前状态下的空间事实进行了有限形式的口头推理。除了与几个方块互动的简单物理任务之外，目前还没有研究探讨推理和行动如何以协同的方式结合起来解决一般任务，以及这种结合是否能比单独的推理或行动带来系统性的益处。

==“In this work, we present ReAct, a general paradigm to combine reasoning and acting with language models for solving diverse language reasoning and decision making tasks (Figure 1).”==

==ReAct，这是一种通用范式，用于将推理和执行与语言模型结合以解决各种语言推理和决策任务。==

### Method

![image-20260402215944893](/Users/des1re/Pictures/笔记图片/react.png)

将agent的执行空间扩展为了language，语言空间非常大难以学习，需要强大的语言先验。

因此，主要关注冻结的预训练语言模型PaLM-540B，通过少量上下文示例进行提示，以生成特定领域的动作和自由形式的语言思考来完成任务。

“Since decision making and reasoning capabilities are integrated into a large language model, ReAct enjoys several unique features:A) Intuitive and easy to design；B) General and flexible；C) Performant and robust；Human aligned and controllable:”

由于决策能力和推理能力被集成到大型语言模型中，ReAct 具有一些独特的特性：

- 直观且易于设计
- 通用且灵活
- 高性能且鲁棒
- 与人类一致且可控