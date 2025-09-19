# SCC-Prompt-System-GPT_v1.6
## 繁體中文

## SCC 提示系統是什麼

SCC 提示系統 v1.6 是一個 單檔提示字引擎，用來最佳化 AI 模型的回答方式。
它會自動處理：

任務分流（抽象、學術、應用）

結構拆解（把問題拆分成子重點）

算力分配（使用「背包演算法」來分派資源）

延遲控制（確保回答速度快）

引用管理（延遲式、漸進式引用）

你只要把這份 TXT 放進系統提示（或當作第一輪輸入加在最前面），AI 就會遵循整個操作手冊來運作。

## 一、基本使用方式

載入 TXT
把 SCC_prompt_system_v1.6.txt 放到 AI 的「系統提示」或「第一輪輸入」裡。
之後你丟任何問題，AI 就會照這份規則走。

任務分類（三大類）

Abstract（抽象/哲理/理論）：自動傾向 Thinking-mini 或 Thinking。

Academic（學術/論文/期刊）：強制 Thinking、引用 ≥1。

Applied（實務/應用/解法）：預設 Instant，必要時升 Thinking-mini。

細部分流（Lite / Heavy）

Lite（答辯型）：快速、≤15 秒，引用少（1–2），適合口頭答辯/會議 Q&A。

Heavy（期刊型）：完整、≤40 秒，引用多（2–4），適合學術文章/長文。

額外還有：

A-Deep / A-Lite：抽象問題的深思 or 快答。

AP-Deep / AP-Lite：應用問題的跨域整合 or 快速解法。

啟用標籤快速切換

問題前加 [Lite]、[Heavy]、[A-Deep]、[AP-Lite] 等標籤，就能精確指定分流。

沒加標籤時會自動根據 SCC（結構複雜度係數）＋神經網絡分解器自動判斷。

## 二、關鍵演算法特色

Adaptive Depth Gate：判斷 Thinking 是否值得跑，避免「深算但沒價值」。

Marginal Utility Pruning：引用/驗證若提升有限，就自動裁掉。

Dual-Track AutoBlend：平行跑 Auto 與 Thinking，先回 Auto（≤15s），Thinking 只補充。

Resource Aware Routing：有無 Plus 帳號會分別走不同護欄，避免「Plus 反而輸」。

Knapsack 算力分配：像背包問題一樣，給最有價值的子重點更多算力。


## English

## What the Project Is

The SCC Prompt System v1.6 is a single-file prompt engine designed to optimize how AI models answer questions.
It automatically handles:

Task routing (Abstract, Academic, Applied)

Structural decomposition (breaking a query into sub-points)

Compute allocation (using a Knapsack-style algorithm to assign resources)

Latency control (so answers stay fast)

Citation management (lazy, incremental referencing)

You drop the TXT file into the system prompt (or prepend it as the first input), and the AI follows the whole playbook.

## 1.Task Classification (Tri-Route)

The system routes questions into three main classes:

Abstract → philosophy, theory, principles. Default: Thinking-mini / Thinking.

Academic → scholarly, journal-level questions. Default: Thinking, ≥1 citation.

Applied → practical, real-world solutions. Default: Instant, with optional Thinking-mini for complexity.

## 2.Profiles (Lite vs Heavy)

Each route supports two depth profiles:

Lite (Debate-style):

Target latency ≤12–15s

Minimal citations (1–2)

Ideal for oral defense, live Q&A

Heavy (Journal-style):

Target latency ≤35–40s

More citations (2–4), multiple beams

Ideal for academic papers or long-form analysis

Additional sub-profiles:

A-Deep / A-Lite → for abstract reasoning (deep thinking vs quick framing).

AP-Deep / AP-Lite → for applied integration (cross-domain solutions vs quick fix checklists).

## 3.Key Algorithms

Adaptive Depth Gate: decides if deeper Thinking is worthwhile, based on marginal gains.

Marginal Utility Pruning: trims low-value citations/verification if cost outweighs benefit.

Dual-Track AutoBlend: runs Auto (Instant+Thinking-mini mix) and Thinking in parallel. Returns Auto ≤15s; Thinking only adds citations or updates.

Resource-Aware Routing: adjusts behavior depending on whether the account is Plus or not (avoids “Plus paradox” where extra compute slows answers).

Knapsack Allocation: distributes compute budget to the most valuable sub-points.

## 4.Output Format

Every answer follows a fixed skeleton:

Final Conclusion → one-line summary

Task Class → Abstract / Academic / Applied

Sub-points (≥v1.4 count):

Mode (I/TM/T), SCC value

3 key takeaways

Optional uncertainty notes

Citations (0–4)

Process Summary → one line + diagnostic codes (R=AutoBlend, DG=DepthGate, MU=MarginalUtility, etc.)

## 5.Best Use Cases

[Lite] / [AP-Lite] → oral defense, quick decisions, live discussions

[Heavy] / [A-Deep] → journal papers, long academic work

[AP-Deep] → complex cross-domain system design

[A-Lite] → fast conceptual framing, lightweight reasoning
