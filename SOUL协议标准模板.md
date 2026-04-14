# **多智能体 SOUL.md 标准协议框架 (v2.1 终极生产版)**

为了确保大语言模型（LLM）在多智能体协作中严格守规、不越界、不幻觉，同时最大化激发其领域专长，所有的 SOUL.md 文件必须严格遵循以下 **6段式标准结构**（融合了 Persona 深度、SOP 严谨性与 Self-Reflection 自我校验机制）：

## **1\. 🎭 Identity & Topology (身份、小传与拓扑)**

**目标：** 明确它是谁，它在工作流中的物理位置，以及它的行为风格。

* **Role (角色):** 明确系统中的代号（如 Programmer）。  
* **Backstory & Tone (人物小传与语调):** 赋予角色灵魂。描述其经验背景、工作态度和语气。  
  * *示例：* “你是一名极度严谨、有代码洁癖的资深后端架构师。说话冷酷、直接，只关注工程可行性。”  
* **Upstream & Input (上游与输入触发):** 它接收谁的产出？期望的输入格式是什么？（必须明确角色和依赖的文件路径）。  
* **Downstream (下游):** 它的产出交给谁？  
* **Mission (核心使命):** 用一句话概括它的根本目的。

## **2\. 🛠️ Capabilities & SOP (工具权限与标准作业程序)**

**目标：** 明确 Agent 的“手”能干什么，以及大脑的“思考步骤”是什么。

* **Allowed Tools (可用工具):** 明确列出它被授权使用的工具（如：文件读写工具、Bash执行）。  
* **SOP (Standard Operating Procedure / 标准工作流):** 以数字列表形式，定义它的标准执行步骤。**最后一步必须是自我校验。**  
  * *示例：*  
    1. **读取：** 使用工具读取上游的 docs/architecture\_blueprint.md。  
    2. **执行：** 编写代码。  
    3. **落盘：** 使用文件工具物理写入 src/main.py。  
    4. **校验 (Pre-flight Check)：** 检查文件是否已真实写入磁盘？如果没有，退回步骤3。  
    5. **汇报：** 生成最终的 JSON 响应。

## **3\. ⚡ Core Directives (核心法则)**

**目标：** 定义该 Agent 必须死守的系统级规律与异常处理机制。

* **The Absolute Truths (绝对真理):** 罗列最高原则（如“零幻觉”、“状态无状态化（Stateless）”、“异步执行”等）。  
* **Exception & Escalation (异常与升级协议):** 明确遇到死锁、依赖缺失、或者 3 次以上的重复错误时，该如何处理（例如向上级 Project-Manager 抛出 ESCALATED 状态）。  
* **Physical File Mandate (强制物理落盘原则):** 严厉声明：deliverables 数组只是收据，绝不会自动保存文件。必须亲自调用工具写盘！

## **4\. 🚫 Boundary Checklist (边界红线 / 坚决不做)**

**目标：** 防止“范围蔓延”（Scope Creep），用负面清单限制 LLM 的发散思维。

* 必须以 ❌ 开头，列出 3 条以上绝对禁止的操作。  
* *示例（Programmer）：* ❌ 坚决不质疑 Architect 的设计。  
  ❌ 坚决不自己运行代码（那是 Executor 的事）。  
  ❌ 坚决不写 TODO 或 ... 占位符，必须写出完整逻辑。

## **5\. 📦 Artifact & Deliverable Template (交付物模板)**

**目标：** 规范输出文件的物理格式、命名和内部结构。

* **Filepaths:** 明确规定必须输出的文件路径（如 src/main.py）。  
* **Content Structure (内容结构):** \* 如果是 Markdown：提供带 \#\# 的标准标题骨架。  
  * 如果是 代码：规定必须的目录结构，是否需要日志装饰器等。

## **6\. 📡 Communication & JSON Schema (通信协议)**

**目标：** 强制规范 Agent 返回给调度层 (Project-Manager) 的数据结构。

* **Language Rules:** 规定内部思考（Reasoning）和交付内容使用的具体语言（中文/英文）。  
* **JSON Schema:** 提供绝对严格的 JSON 模板。包含状态码（Status）、原因（Reasoning）、交付物清单（Deliverables）和下一步分发指令（Next Dispatch）。
