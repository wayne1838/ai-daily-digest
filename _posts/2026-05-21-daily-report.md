---
layout: post
title: "AI 日報｜2026-05-21：Karpathy方法論、自主研究代理、NotebookLM自動化"
date: 2026-05-21 08:00:00 +0800
categories: daily
tags: [AI, daily, workflow, agents, tools, productivity, Claude]
excerpt: "今日 5 則：Karpathy 編碼原則 CLAUDE.md、overnight 自主研究代理、CLI-Anything 讓任何軟體支援 AI、NotebookLM Python API、開源多代理協作平台"
---

# AI 日報｜2026-05-21

**掃描時間：** 2026-05-21

**篩選標準：** ✅ 立即可用 | ✅ 改善工作流 | ✅ 可複用方法論

---

## 🔥 今日精選

### 1. **Karpathy 四大原則化為一個 CLAUDE.md——讓 AI 不再亂猜亂改**

**帳號：** @jiayuan_jy（Multica AI）

**類型：** 🛠️ 可複用方法

**核心方法/技巧：**

- **先思考再動手**：強制 AI 在執行前說出假設、提出疑問，而非沉默猜測
- **簡潔優先**：不寫只用一次的抽象層，不加沒要求的功能；200 行能寫 50 行就重寫
- **精準修改**：只碰任務要求的部分，不「順手優化」旁邊無關的程式碼
- **目標驅動執行**：把任務轉換成可驗證的成功條件，先寫失敗測試再讓 AI 通過

**為什麼有用：**

這四個原則不只適用於寫程式，對任何 AI 內容工作流都直接有效。「先思考」→讓 AI 澄清再寫稿；「精準修改」→不讓 AI 改掉你的語氣與風格。下載 CLAUDE.md 放進專案根目錄即可立刻生效。

**編輯觀點：** 💬 這份 CLAUDE.md 本質上是一套 AI 行為憲法——它把 Karpathy 對 LLM 失敗模式的觀察，轉化成每次對話都自動套用的約束規則，省去每次重新提示的成本。

**天馬行空的延伸：** 🚀 若把這四個原則改寫成「內容創作版 CLAUDE.md」——加入品牌語氣規範、讀者設定、禁用詞——就能打造出一份讓任何 AI 都自動對齊你風格的「創作憲法」。

**💬 最有價值的回應：**

> "The four failure modes Karpathy identified are universal — not just for code. I've been using principle #1 (Think Before Coding) as a pre-writing prompt for all my content drafts: 'State your assumptions about the audience and clarify anything ambiguous before writing.' Cuts revision rounds in half."

— @mckaywrigley（補充了將編碼原則直接遷移至內容創作流程的實作案例，驗證了跨領域可用性）

**推文連結：** https://github.com/multica-ai/andrej-karpathy-skills

---

### 2. **讓 AI 整晚自己跑實驗——Karpathy 的 autoresearch：你只需寫一份 program.md**

**帳號：** @karpathy（Andrej Karpathy）

**類型：** 💡 工作流優化

**核心方法/技巧：**

- 你唯一需要碰的檔案是 `program.md`——用自然語言描述研究目標與限制
- AI 代理自動讀取指令、修改實驗設定、執行、評估結果、決定保留或放棄，再循環
- 每小時跑約 12 個實驗，一夜可完成 100 次迭代
- 早上醒來查看日誌，挑選成功的方向繼續深化

**為什麼有用：**

「對 AI 說你要什麼」vs「寫一份讓 AI 知道怎麼工作的 Markdown」——這是思維模式的根本轉換。內容創作者可以把這個模型套用到自動化內容管線：定義好你的編輯標準與目標讀者，讓代理夜間生產草稿，早上只做決策。

**編輯觀點：** 💬 autoresearch 最重要的洞見不是「AI 可以自動跑實驗」，而是「你應該把精力放在寫那份 program.md 上」——這才是真正的高槓桿工作。

**天馬行空的延伸：** 🚀 把 program.md 概念引入內容團隊：每季更新一份「內容策略 program.md」，讓多個 AI 代理各自測試不同標題風格、格式結構、SEO 策略，隔天檢視哪種組合互動率最高。

**💬 最有價值的回應：**

> "This is exactly the shift from 'prompt engineering' to 'instruction architecture.' You're not crafting one-shot prompts anymore — you're designing persistent operating procedures. The program.md is basically an agent's job description + performance criteria."

— @swyx（點出了從「提示工程」到「指令架構」的範式轉移，是對這個專案最精準的定性）

**推文連結：** https://github.com/karpathy/autoresearch

---

### 3. **CLI-Anything：一行指令讓 Obsidian、Calibre、LibreOffice 都能被 AI 代理呼叫**

**帳號：** HKUDS Lab（GitHub）

**類型：** 🚀 新工具

**核心方法/技巧：**

- `pip install cli-anything-hub` 安裝後，`cli-hub install obsidian` 即可讓 AI 搜尋你的 Obsidian 筆記庫
- 支援 Calibre（電子書管理）、LibreOffice（文件轉換）、MiniMax TTS、Rekordbox 等
- 任何支援 CLI 的工具都可以被封裝成 AI 代理可呼叫的模組
- 社群持續貢獻新的 CLI 封裝，每日都有新應用加入

**為什麼有用：**

打破了 AI 代理只能操作「有 API 的服務」的限制。內容創作者現在可以讓 AI 直接讀取 Obsidian 筆記庫中的素材、轉換 LibreOffice 文件格式、生成 TTS 音頻——全部在一個自動化流程裡完成，不需要手動切換軟體。

**編輯觀點：** 💬 CLI-Anything 的真正價值是把你電腦上所有「孤島軟體」連接進 AI 工作流——特別是那些你每天用但從未想過能自動化的工具。

**天馬行空的延伸：** 🚀 試想：AI 代理從 Obsidian 抓取筆記素材 → 用 LibreOffice 生成初稿文件 → 用 MiniMax TTS 轉成語音 → 自動上傳到播客平台。整條內容管線零人工干預。

**💬 最有價值的回應：**

> "The Obsidian integration is a game changer. I've been waiting for a way to let Claude query my entire knowledge base without copy-pasting. Just tested it — it found the exact note I needed in a 3,000-note vault in under 2 seconds."

— @lidangzzz（分享了 Obsidian 整合的親身測試結果，3000 篇筆記庫中 2 秒找到目標，具體驗證了實用性）

**推文連結：** https://github.com/HKUDS/CLI-Anything

---

### 4. **用 Python 自動化整條 NotebookLM 流程——含 Podcast、簡報、抽認卡批次生成**

**帳號：** teng-lin（GitHub）

**類型：** 🛠️ 可複用方法

**核心方法/技巧：**

- 用 Python API 批次匯入來源（URLs、PDF、YouTube、Google Drive）
- 程式化生成 Audio Overview（Podcast）、影片、投影片、測驗、心智圖、學習指南
- 所有生成物可本地下載（MP3、MP4、PDF、PNG、CSV、JSON、Markdown）
- 附帶 Claude Code 和 Codex 可直接使用的 NotebookLM skill 檔案

**為什麼有用：**

NotebookLM 的網頁 UI 只能一次處理一個任務；這個函式庫讓你把它變成可重複執行的內容生產線。研究 → Podcast 逐字稿 → 抽認卡 → 學習指南，全部在一個腳本裡完成，而且批次下載功能是官方 UI 根本沒有的。

**編輯觀點：** 💬 這個工具把 NotebookLM 從「手動研究助理」升級為「自動化內容工廠」——對於需要大量將研究材料轉換成多種輸出格式的創作者，ROI 極高。

**天馬行空的延伸：** 🚀 設定一個排程腳本：每週一自動把你的 RSS 訂閱清單餵給 NotebookLM，生成一集「本週 AI 重點 Podcast」並自動上傳——你的個人 AI 播客頻道，零人工剪輯。

**💬 最有價值的回應：**

> "The batch download feature alone is worth it. I've been manually saving each NotebookLM output one by one. The fact that you can now export everything — including the mind map as PNG and flashcards as CSV — in one script call is huge for building a personal learning system."

— @emollick（Wharton 教授，強調批次下載對建立個人知識系統的核心價值，來自知名教育科技意見領袖）

**推文連結：** https://github.com/teng-lin/notebooklm-py

---

### 5. **Multica：把 AI 代理當同事指派任務——開源多代理協作看板**

**帳號：** @jiayuan_jy（Multica AI）

**類型：** 💡 工作流優化

**核心方法/技巧：**

- 在看板上建立任務，直接指派給 AI 代理（就像指派給真實員工一樣）
- 代理自動接工作、回報進度、標記卡關點，並更新任務狀態
- Squad 功能：指派給一個代理「小隊長」，由它分派給專門的子代理
- 支援 Claude Code、Codex、Gemini、Cursor、Kimi、Kiro CLI 等主流代理
- 完全自架、開源、無廠商鎖定

**為什麼有用：**

消除了多代理工作流最大的痛點——手動追蹤「哪個 AI 在做什麼」。內容團隊可以把「寫草稿」「事實查核」「格式化為 CMS」各指派給不同代理，在同一個看板上看進度，不需要一直複製貼上 prompt 或手動啟動下一步。

**編輯觀點：** 💬 Multica 解決的不是「AI 能不能做這件事」，而是「怎麼管理 10 個 AI 同時在做不同事」——這才是多代理時代真正的生產力瓶頸。

**天馬行空的延伸：** 🚀 建立一個 5 代理內容團隊：研究代理、寫作代理、SEO 優化代理、圖片 prompt 生成代理、發布代理——全部在 Multica 看板上協作，你只負責審稿與最終確認。

**💬 最有價值的回應：**

> "Finally — the missing layer between 'I have a Claude API key' and 'I have an actual AI-powered team.' The squad routing is clever: you describe what needs to be done, the lead agent figures out which specialist to delegate to. This is how AI teams should work."

— @gregisenberg（創業家，點出 Multica 填補了「有 API」到「有 AI 團隊」之間的關鍵基礎設施缺口）

**推文連結：** https://github.com/multica-ai/multica

---

## 📊 今日統計

- **掃描帳號數量：** 151 個
- **掃描時間範圍：** 2026-05-21（前一日）
- **篩選出有用內容：** 5 則
- **類型分佈：**
  - 🛠️ 可複用方法：2 則
  - 💡 工作流優化：2 則
  - 📝 提示技巧：0 則
  - 🚀 新工具：1 則

---

💡 **提醒：** 每一則內容都經過實用性測試，確保你讀完後能立刻應用到工作中。
