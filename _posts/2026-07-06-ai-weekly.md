---
layout: post
title: "AI 週報精選｜2026 年第 27 週（06/30–07/06）：Claude Sonnet 5 登場、Karpathy Software 3.0 論述、Anthropic 超越 OpenAI 成最高營收 AI 公司"
date: 2026-07-06 08:00:00 +0800
categories: weekly
tags: [AI, workflow, tools, weekly]
excerpt: "本週亮點：Claude Sonnet 5（6/30）帶來 1M Token 視窗與全新 Tokenizer，Claude Code 四大更新推出 /dataviz Skill 與 Background Agents 自動開 PR；Karpathy 在 Sequoia Ascent 2026 演講深度剖析 Vibe Coding vs Agentic Engineering；Anthropic 以 $47B 年化營收超越 OpenAI，Gemini 3.5 Pro 成唯一無限制前沿模型，addyosmani 提出 AI Agent 規格撰寫六大要素。"
---

本週 AI 領域多點開花：模型層有 Claude Sonnet 5 與 Gemini 3.5 Pro 雙雄競豔，工具層有 Claude Code 連續四版更新，思想層有 Karpathy 的 Software 3.0 論述震盪業界。以下 15 則精選，每則都可立即取用。

---

## 1｜Claude Sonnet 5 正式發布

**帳號：** @AnthropicAI
**類型：** 🚀 新工具

**核心方法：**
- 1M Token 上下文視窗、128K 最大輸出 Token
- Adaptive Thinking 預設開啟（自動決定是否進入深度推理）
- 全新 Tokenizer：英文約多 1.4 倍 Token（成本增加）、中文基本持平
- 導入期特惠定價 $2/$10 per MTok，有效至 2026/08/31

**為什麼有用：**
Adaptive Thinking 讓同一個模型既能快速回應日常問題、也能深度推理複雜任務，無需手動切換版本。導入期定價仍具競爭力。

**編輯觀點：**
Tokenizer 更換是這次最需要注意的隱性成本。英文 prompt 越長，費用差距越大；中文使用者暫時不受影響。建議先在非生產環境測試 Token 用量再切換。

**創意延伸：**
利用 128K 輸出上限，嘗試一次生成完整模組文件或長篇報告，取代過去需要多次接力的工作流。

> "Claude Sonnet 5 is our most intelligent model to date, and sets a new bar for coding, reasoning, and agentic tasks."

🔗 [https://www.anthropic.com/news/claude-sonnet-5](https://www.anthropic.com/news/claude-sonnet-5)

---

## 2｜Simon Willison：Sonnet 5 Tokenizer 深度解析

**帳號：** @simonw
**類型：** 📝 提示技巧

**核心方法：**
- 實測英文 prompt Token 數比 Sonnet 3.7 多約 1.4 倍
- 中文、日文、代碼 Token 數大致持平
- 新 Tokenizer 移除了 `temperature`、`top_p`、`top_k` 參數支援
- 提供 Python 測試腳本，可自行驗算任意 prompt 的 Token 差異

**為什麼有用：**
在切換 Sonnet 5 前，可用 Simon 的腳本實測自己常用 prompt 的 Token 差，避免帳單驚嚇。

**編輯觀點：**
這是本週最「省錢」的一篇技術分析。系統提示詞長的用戶（如有大量 CLAUDE.md 指令的工程師）受影響最大，建議先測再換。

**創意延伸：**
為不同業務場景的 prompt 建立「Token 成本基準表」，方便未來每次模型更換時快速評估影響。

> "The new tokenizer splits English text differently — my test showed a 1.4x token increase for the same English sentence."

🔗 [https://simonwillison.net/2026/Jun/30/claude-sonnet-5/](https://simonwillison.net/2026/Jun/30/claude-sonnet-5/)

---

## 3｜Claude Code 本週四大更新（v2.1.197–2.1.201）

**帳號：** @AnthropicAI
**類型：** 🛠️ 可複用方法

**核心方法：**
1. **Sonnet 5 設為預設模型**（v2.1.197）
2. **Claude in Chrome GA**（v2.1.198）：瀏覽器 Agent 正式版，可操控 Chrome 執行完整任務
3. **Background Agents 自動開 Draft PR**（v2.1.199）：後台 Agent 完成任務後自動 commit、push、開 Draft PR，不再需要手動觸發
4. **Manual 改為預設權限模式**（v2.1.200）：每次工具呼叫需明確確認，安全性提升
5. **`/dataviz` Skill 上線**（v2.1.201）：內建圖表設計指引與可執行的色盤驗證器

**為什麼有用：**
Background Agents 自動 Draft PR 大幅縮短「Agent 完成任務 → 人工審查」的循環，特別適合夜間或長跑任務。Manual 預設模式則強迫開發者對 Agent 行為保持意識。

**編輯觀點：**
這四版更新加在一起，幾乎重塑了 Claude Code 的日常使用體驗。Manual 模式從 opt-in 變為 opt-out，是值得注意的行為改變。

**創意延伸：**
搭配 Background Agents + Draft PR，可設計「每日凌晨自動執行代碼審查，早上醒來直接看 PR」的自動化循環。

> "Background agents now automatically commit, push, and open draft PRs when they complete a task."

🔗 [https://releasebot.io/updates/anthropic/claude-code](https://releasebot.io/updates/anthropic/claude-code)

---

## 4｜Karpathy：Software 3.0 與 Agentic Engineering

**帳號：** @karpathy
**類型：** 💡 工作流優化

**核心方法：**
- **Software 1.0**（手寫代碼）→ **2.0**（神經網路訓練）→ **3.0**（自然語言指揮 AI 生成代碼）
- **Vibe Coding**：告訴 AI「我要什麼」，AI 全部完成，適合原型與個人工具
- **Agentic Engineering**：設計 Agent 架構、驗證邏輯、管理長跑任務，適合生產系統
- **MenuGen 案例**：用 Software 3.0 方式重建餐廳菜單生成系統，效率提升數倍
- **代理人原生基礎設施**：Markdown 文件、CLI 工具、結構化日誌、MCP Server、可複製貼上的指令

**為什麼有用：**
這份論述幫助釐清「Vibe Coding 到底適合什麼」的邊界。知道邊界，才不會把 Vibe Coding 用在錯誤的場景並陷入維護噩夢。

**編輯觀點：**
Karpathy 最有洞見的一點：Software 3.0 不是讓工程師消失，而是讓工程師的工作從「寫代碼」轉移到「設計可被 AI 理解和驗證的系統」。

**創意延伸：**
對照自己的工作清單，標記哪些屬於 Vibe Coding 適用範圍（快速原型、個人工具），哪些需要 Agentic Engineering（生產 API、複雜業務邏輯）。

> "You can outsource thinking, but you cannot outsource understanding."

🔗 [https://karpathy.bearblog.dev/sequoia-ascent-2026/](https://karpathy.bearblog.dev/sequoia-ascent-2026/)

---

## 5｜Karpathy：「可以外包思考，但無法外包理解」

**帳號：** @karpathy
**類型：** 💡 工作流優化

**核心方法：**
- 用 LLM 建立領域知識庫以輔助理解，而非取代理解
- 設計「可驗證性框架」：只接受能被自己驗證正確性的 AI 輸出
- 識別「理解邊界」：哪些工作需要你真正理解，哪些可以放心外包

**為什麼有用：**
這個框架解決了「我到底能相信 AI 輸出到什麼程度」的核心焦慮，提供具操作性的判斷標準。

**編輯觀點：**
結合第 4 則的 Agentic Engineering 概念，這是 Karpathy 本週論述的核心：AI 工具放大能力，但理解力必須自己保留。不懂的東西，不能讓 AI 替你負責。

**創意延伸：**
為自己的工作建立「理解邊界清單」：列出 3-5 個即使 AI 能完成、但你必須真正理解才能審查結果的關鍵領域。

> "LLMs are great for building knowledge bases, not for replacing the understanding you need to verify their outputs."

🔗 [https://x.com/karpathy/status/2049903821095354523](https://x.com/karpathy/status/2049903821095354523)

---

## 6｜Claude Code /dataviz Skill 上線

**帳號：** @AnthropicAI（via @dani_avila7）
**類型：** 🛠️ 可複用方法

**核心方法：**
- 內建圖表設計指引（選色、對比、可讀性標準）
- **可執行的色盤驗證器**：直接在 Claude Code 中執行，檢查色盤的無障礙對比度
- 覆蓋常見圖表類型：折線圖、長條圖、散點圖、熱力圖的最佳實踐

**為什麼有用：**
不需要離開 Claude Code 去外部工具檢查色彩無障礙（WCAG 標準），降低製作「視覺上好看但色盲不友善」的 Dashboard 機率。

**編輯觀點：**
Skill 架構讓 Claude Code 能把特定領域的知識模組化。/dataviz 是個好例子：把散落在各設計部落格的最佳實踐，打包成一個可直接呼叫的工具。

**創意延伸：**
參考 /dataviz Skill 的架構，製作自己組織的客製化 Skill：把公司品牌色盤、報告格式標準寫入 Skill，讓每個 Claude Code 輸出都符合品牌規範。

> "The /dataviz skill includes a runnable color-palette validator — just run it and it checks WCAG contrast ratios automatically."

🔗 [https://x.com/dani_avila7/status/2072460033896419478](https://x.com/dani_avila7/status/2072460033896419478)

---

## 7｜addyosmani：如何為 AI Agent 撰寫好規格

**帳號：** @addyosmani
**類型：** 📝 提示技巧

**核心方法：**
六大規格撰寫要素（the "curse of instructions" 對策）：
1. **指令（Commands）**：明確 Agent 可用的動作與禁止動作
2. **測試標準（Testing）**：定義「任務完成」的可驗證條件
3. **結構（Structure）**：檔案組織與命名規則
4. **代碼風格（Code Style）**：語言、格式、模式偏好
5. **版本控制（Git）**：commit 訊息格式、branch 命名
6. **邊界（Boundaries）**：哪些東西 Agent 不能碰

**規格文件的作用**：錨定每次 Agent Session，避免每次都要重新解釋背景。

**為什麼有用：**
「詛咒of instructions」是指：沒有規格，Agent 胡亂發揮；規格太多，Agent 淹沒在矛盾指令中。這六個維度提供平衡點。

**編輯觀點：**
這份指南可直接轉化為 CLAUDE.md 或 AGENTS.md 的撰寫框架。建議從「邊界」開始寫：先定義 Agent 不能做什麼，再定義它應該做什麼。

**創意延伸：**
用這六個維度審視現有的 CLAUDE.md，找出缺失的維度並補全，觀察 Agent 行為品質是否提升。

> "A spec anchors every session. Without it, each conversation starts from zero."

🔗 [https://addyosmani.com/blog/good-spec/](https://addyosmani.com/blog/good-spec/)

---

## 8｜danshipper：Proof — Agent 原生協作文件編輯器

**帳號：** @danshipper
**類型：** 🚀 新工具

**核心方法：**
- **來源追蹤（Provenance Tracking）**：文字顯示顏色標記來源——🟢 綠色 = 人類撰寫、🟣 紫色 = AI 生成
- **Agent 原生設計**：文件本身就是 Agent 的輸入/輸出介面
- **免費開源**：MIT 授權，可自行部署

**為什麼有用：**
在 AI 協作寫作日益普遍的環境下，「這句話是誰寫的」變成重要資訊。Proof 讓人-AI 協作的責任邊界清晰可見。

**編輯觀點：**
來源追蹤不只是透明度工具，也是品質控制工具：看到紫色區塊，就知道那是需要人工審查的部分。這個設計理念值得在其他工作流中借鑒。

**創意延伸：**
對需要審核 AI 生成內容的工作流（如法律文件初稿、公告草稿），引入類似的顏色標記機制，即使不用 Proof，也可以用 Google Doc 的建議模式模擬。

> "Green text = human, purple text = AI. Every word's origin is visible at a glance."

🔗 [https://x.com/danshipper/status/2031794701221736529](https://x.com/danshipper/status/2031794701221736529)

---

## 9｜op7418：CodePilot — 多模型 AI Agent 桌面客戶端

**帳號：** @op7418
**類型：** 🚀 新工具

**核心方法：**
- 單一介面整合 **17+ AI 提供商**（Claude、GPT、Gemini、Qwen、DeepSeek 等）
- **Remote Bridge**：透過 Telegram、WeChat、Discord、QQ、飛書 遠端操控 Agent
- 支援 **MCP + Skills** 雙層擴充機制
- 目前 **5.7k GitHub Stars**，進行中的大規模重構（refactor 分支）

**為什麼有用：**
不想被單一 AI 廠商綁定，又需要跨模型協作的用戶，CodePilot 提供統一的操作介面，並透過即時通訊 App 實現行動辦公。

**編輯觀點：**
Remote Bridge 是差異化功能：在 Telegram 群組裡直接觸發 Agent 任務，回到桌面看結果，這種工作流設計在中文用戶中特別實用。目前正在重構，等穩定版再評估生產使用。

**創意延伸：**
測試 CodePilot 的 Remote Bridge，設計「用 LINE/Telegram 傳送指令 → Agent 執行 → 結果回傳到聊天室」的輕量自動化工作流。

> "17+ providers, MCP support, and a remote bridge via Telegram/WeChat — all in one desktop client."

🔗 [https://github.com/op7418/CodePilot](https://github.com/op7418/CodePilot)

---

## 10｜Gemini 3.5 Pro 正式發布

**帳號：** @GoogleDeepMind
**類型：** 🚀 新工具

**核心方法：**
- **2M Token 上下文視窗**（目前最大）
- **唯一未受美國政府出口管制的前沿模型**（Fable 5/Mythos 5 被限制後）
- 深度整合 Google Workspace（Docs、Sheets、Gmail 原生 Agent）
- 多模態能力涵蓋圖片、影片、音訊、文件

**為什麼有用：**
2M Token 視窗讓整個大型代碼庫或完整書稿可以一次性放入 context，對需要跨文件分析的任務特別有利。作為目前唯一不受出口管制的前沿模型，全球可用性是競爭優勢。

**編輯觀點：**
Gemini 3.5 Pro 最大的商業護城河不是技術規格，而是「在法規環境改變後仍可全球部署」。對跨境企業而言，這一點的重要性超過 benchmark 分數。

**創意延伸：**
用 2M Token 視窗做一次「整個專案代碼庫全文脈絡分析」，讓 AI 生成一份完整的架構說明文件，而非逐檔查看。

> "Gemini 3.5 Pro with 2M context is currently the only unrestricted frontier model available globally."

🔗 [https://codersera.com/blog/gemini-3-5-complete-guide-2026/](https://codersera.com/blog/gemini-3-5-complete-guide-2026/)

---

## 11｜Zuckerberg 坦承：Meta AI Agent 進展不如預期

**帳號：** @zuck
**類型：** 💡 工作流優化

**核心方法：**
- 原訂 Q1 2026 完成的 AI Agent 里程碑推遲 4 個月
- $145B 年度資本支出持續燃燒中
- 新時間預測：3-6 個月後（約 Q3-Q4 2026）
- 核心瓶頸：Agent 在複雜多步驟任務中的可靠性

**為什麼有用：**
即使是資源最充裕的公司之一，也在 Agent 可靠性上遭遇挫折。這提醒我們：在選擇要以 Agent 自動化的任務時，應優先選擇「失敗代價低」且「可人工介入」的任務。

**編輯觀點：**
Meta 的案例是一個寶貴的參照點。企業在規劃 AI Agent 導入時，應預留 3-6 個月的「可靠性磨合期」，而非假設 Agent 部署即可用。

**創意延伸：**
用「失敗代價矩陣」評估工作流中哪些步驟可以委派給 Agent（低失敗代價 × 高重複度），哪些必須保留人工（高失敗代價 × 低可回溯性）。

> "The agent capabilities haven't progressed as quickly as I'd hoped. We're looking at another 3-6 months."

🔗 [https://techcrunch.com/2026/07/02/mark-zuckerberg-tells-staff-that-ai-agents-havent-progressed-as-quickly-as-hed-hoped/](https://techcrunch.com/2026/07/02/mark-zuckerberg-tells-staff-that-ai-agents-havent-progressed-as-quickly-as-hed-hoped/)

---

## 12｜Anthropic 超越 OpenAI：成為最高年化營收 AI 公司

**帳號：** @AnthropicAI
**類型：** 💡 工作流優化

**核心方法：**
- Anthropic 年化營收達 **$47B**，超越 OpenAI 的 $25–33B
- **1,000+ 企業客戶年付費超過 $1M**
- 成長動力：企業 Agent 部署（Claude Code、Claude Security）
- 戰略意涵：企業端 B2B 市場是 AI 公司最穩定的護城河

**為什麼有用：**
這個數字說明一件事：大量企業客戶願意在「AI 寫代碼 + AI 資安」這兩個垂直領域投入七位數年費。這也是開發者和企業評估 AI 工具優先級時的重要訊號。

**編輯觀點：**
Anthropic 的成功路徑是「做開發者喜歡的工具，開發者帶進企業，企業簽大合約」。這條路比 OpenAI 的消費者策略更可預測，但也更慢。

**創意延伸：**
對比 Claude Code 與 Copilot Enterprise 的定價與功能，評估自己所在組織在 AI 編程工具上的最佳配置。

> "Anthropic's annualized revenue has crossed $47B, driven by 1,000+ enterprise customers each paying over $1M annually."

🔗 [https://aitoolsrecap.com/Blog/ai-news-july-3-2026](https://aitoolsrecap.com/Blog/ai-news-july-3-2026)

---

## 13｜白宮草擬自願 AI 發布標準

**帳號：** 產業新聞
**類型：** 💡 工作流優化

**核心方法：**
- 美國白宮正式化 **自願性 AI 發布標準框架**
- 包含：網路安全基準門檻、發布前審查時間線、風險分級評估
- 對象：在美國上市或準備 IPO 的 AI 公司
- 與 Anthropic/Google 等主要廠商協商制定

**為什麼有用：**
雖為「自願」，但與 IPO 掛鉤的隱性壓力讓這份框架接近事實上的行業標準。企業在評估 AI 工具供應商時，未來「是否符合白宮標準」可能成為採購條件之一。

**編輯觀點：**
這是 AI 監管從「規範 AI 的危害」轉向「規範 AI 的發布流程」的重要里程碑。對 IT 採購決策者而言，現在是建立 AI 供應商合規評估標準的好時機。

**創意延伸：**
參考白宮框架的網路安全基準，建立組織內部的 AI 工具採購安全清單（如：供應商是否有漏洞揭露政策？模型訓練數據是否可稽核？）

> "The White House's voluntary framework formalizes cybersecurity benchmark thresholds and review timelines for AI releases."

🔗 [https://aitoolsrecap.com/Blog/ai-news-july-3-2026](https://aitoolsrecap.com/Blog/ai-news-july-3-2026)

---

## 14｜ruanyf 科技愛好者週刊 #402：「我在智念 AI 的日子（小說）」

**帳號：** @ruanyf
**類型：** 🛠️ 可複用方法

**核心方法：**
本期封面文章以小說形式描寫 AI 公司工作日常（作者匿名投稿）；工具精選包含：
- **figviz.com**：互動式概念圖視覺化工具，適合知識整理
- **Arc**：輕量級網頁版 Postman API 測試工具
- **SharkTTY**：美化終端機工具（主題+字體+佈局）
- **yaohe**：開源推廣 Agent Skill（自動生成社群媒體推廣文案）

**為什麼有用：**
figviz 適合視覺化 Claude Code 的系統架構討論結果；yaohe Skill 直接可用於自動化工具推廣工作流。

**編輯觀點：**
ruanyf 以小說包裝 AI 職場觀察，是少見的「通過敘事理解技術文化」的嘗試。figviz 值得收藏，用於整理複雜概念間的關聯。

**創意延伸：**
嘗試用 figviz 視覺化自己當前最複雜的工作流或知識地圖，分享給團隊作為討論起點。

> "本期工具精選裡的 figviz，是目前最輕量的概念圖工具之一，開啟即用不需安裝。"

🔗 [https://www.ruanyifeng.com/blog/2026/07/weekly-issue-402.html](https://www.ruanyifeng.com/blog/2026/07/weekly-issue-402.html)

---

## 15｜Karpathy：代理人原生基礎設施十大要素

**帳號：** @karpathy
**類型：** 🛠️ 可複用方法

**核心方法：**
在 Sequoia Ascent 2026 演講中，Karpathy 列出「對 AI Agent 友善的系統」應具備的要素：
1. **Markdown 文件**（非 PDF/Word）
2. **CLI 工具**（比 GUI 更易被 Agent 操控）
3. **REST/GraphQL API**（不依賴人工介面）
4. **MCP Servers**（Agent 可直接呼叫的工具介面）
5. **結構化日誌**（Agent 可解析的機器可讀格式）
6. **可複製貼上的指令**（含參數的完整命令）
7. **版本化配置**（YAML/JSON，而非 GUI 點擊設定）
8. **沙盒環境**（讓 Agent 可安全試驗）
9. **冪等操作**（重複執行不產生副作用）
10. **明確的狀態輸出**（成功/失敗有明確訊號）

**為什麼有用：**
這是評估「我的基礎設施是否 Agent 就緒」的具體清單。缺少哪幾條，就知道要優先改造哪裡。

**編輯觀點：**
Karpathy 的清單本質上是「讓 Agent 能可靠工作」的必要條件，也是「讓人類工程師更有效率」的良好實踐。這兩個目標恰好高度重疊。

**創意延伸：**
對照這十項，審視自己最常使用的 3 個工作系統（如 CRM、監控、部署工具），標記哪些已「Agent 就緒」，哪些需要改造。

> "Agent-native infrastructure is just good engineering practice — it's good for humans and great for agents."

🔗 [https://karpathy.bearblog.dev/sequoia-ascent-2026/](https://karpathy.bearblog.dev/sequoia-ascent-2026/)

---

*本週報由 AI 輔助掃描生成，Wayne 審閱後發布。如有任何內容錯誤或建議，歡迎回報。*
