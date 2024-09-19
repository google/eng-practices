# 写好 CL 描述

CL 描述是进行了**哪些更改**以及**为何更改**的公开记录。CL 将作为版本控制系统中的永久记录，可能会在长时期内被除审查者之外的数百人阅读。

开发者将来会根据描述搜索您的 CL。有人可能会仅凭有关联性的微弱印象，但没有更多具体细节的情况下，来查找你的改动。。如果所有重要信息都在代码而不是描述中，那么会让他们更加难以找到你的 CL 。

## 首行 {#firstline}

* 正在做什么的简短摘要。
* 完整的句子，使用祈使句。
* 后面跟一个空行。

CL 描述的**第一行**应该是关于这个 CL 是**做什么**的简短摘要，后面跟一个空白行。

这会是版本控制历史记录摘要中显示的内容，因此第一行应该提供足够的信息，以便将来的代码搜索者不必阅读您的 CL或其全部描述即可了解您的 CL 的**实际功能**或与其他 CL 的区别。也就是说，第一行应该独立存在，从而使读者可以更快地浏览代码历史记录。

尝试让第一行保持简短，专注且切题的。清晰度和实用性对于读者而言应该是最重要的事。

按照传统，CL 描述的第一行应该是一个完整的句子，就好像是一个命令（一个命令句）。例如，“**Delete** the FizzBuzz RPC and **replace** it with the new system.”而不是“**Deleting** the FizzBuzz RPC and **replacing** it with the new system.“ 但是，您不必把其余的描述写成祈使句。

## Body 是信息丰富的 {#informative}

其余描述应该是提供信息的。可以包括对正在解决的问题的简要描述，以及为什么这是最好的方法。如果这个方法有任何缺点，应该提到它们。如果有其他相关信息，请将有关的背景信息例如 bug numbers, 测试结果，设计文档的链接写在 CL 描述里面.

如果你的描述里有指向外部资源的链接，请考虑到这些链接有可能有时效性和访问限制，有些读者可能打不开这些链接。因此请尽可能可能包含足够的上下文，以供审阅者和将来的读者理解你的 CL。

即使是小型 CL 也需要注意细节。在 CL 描述中提供上下文以供参照。

## 糟糕的 CL 描述 {#bad}

“Fix bug ”是一个不充分的 CL 描述。什么 bug？你做了什么修复？其他类似的不良描述包括：

- "Fix build."
- "Add patch."
- "Moving code from A to B."
- "Phase 1."
- "Add convenience functions."
- "kill weird URLs."

其中一些是真正的 CL 描述。儘管简短，却并没有提供足够有用的信息。

## 好的 CL 描述 {#good}

以下是一些很好的描述示例。

### 功能更新

示例:
> rpc：删除 RPC 服务器消息 freelist 上的大小限制。
>
> 像 FIzzBuzz 这样的服务器有非常大的消息，并且可以从重用中受益。增大 freelist，添加一个 goroutine，缓慢释放 freelist 条目，以便空闲服务器最终释放所有 freelist 条目。

前几个词描述了CL实际上做了什么。其余的描述讨论了正在解决的问题，为什么这是一个很好的解决方案，以及有关具体实现的更多信息。

### 重构

示例:
> Construct a Task with a TimeKeeper to use its TimeStr and Now methods.
>
> Add a Now method to Task, so the borglet() getter method can be removed (which was only used by OOMCandidate to call borglet's Now method). This replaces the methods on Borglet that delegate to a TimeKeeper.
> 
> Allowing Tasks to supply Now is a step toward eliminating the dependency on Borglet. Eventually, collaborators that depend on getting Now from the Task should be changed to use a TimeKeeper directly, but this has been an accommodation to refactoring in small steps.
>
> Continuing the long-range goal of refactoring the Borglet Hierarchy.

第一行描述了 CL 的作用以及改变。其余的描述讨论了具体的实现，CL 的背景，解决方案并不理想，以及未来的可能方向。它还解释了为什么正在进行此更改。

### 需要上下文的小 CL

示例:
> Create a Python3 build rule for status.py.
>
> This allows consumers who are already using this as in Python3 to depend on a rule that is next to the original status build rule instead of somewhere in their own tree. It encourages new consumers to use Python3 if they can, instead of Python2, and significantly simplifies some automated build file refactoring tools being worked on currently.

第一句话描述实际做了什么。其余的描述解释了为什么正在进行更改并为审查者提供了大量背景信息。

## 自动生成的 CL 描述

部分 CL 是由工具生成。有可能的话，它们的描述也应遵循此处的建议。也就是说，他们的第一行应该简短，专注且切题的，独立存在，并且 CL 描述正文应包括足够充足详细信息，以帮助审阅者和将来的代码搜索者了解每个 CL 的作用。

## 在提交 CL 前审查描述

CL 在审查期间可能会发生重大变更。在提交 CL 之前检查 CL 描述是必要的，以确保描述仍然反映了 CL 的作用。

下一篇：[小型 CL](small-cls.md)
