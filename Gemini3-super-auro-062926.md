Aura-7 醫材合規追蹤平台：全面技術規格與架構白皮書 (v4.0.0-Enterprise)
1. 項目背景與願景：為什麼我們需要 Aura-7？
在現代醫療體系中，高風險醫療器材（如 Class-III 植入式起搏器、心臟瓣膜、人工關節等）的安全性、可追蹤性與合規管理是醫療品質的重中之重。中華民國台灣食品藥物管理署 (TFDA) 針對特定高風險醫療器材之來源與流向制定了極為嚴格的法律規範（依據《醫療器材管理法》第十九條第一項規定，公告「應建立與保存來源及流向資料之醫療器材」品項）。法規要求製造業、販賣業者及醫療機構必須精準記錄並保存每一件醫材從輸入、製造、流通至臨床使用的完整生命週期軌跡，以確保在發生不良反應或產品瑕疵時，能在數小時內啟動精準召回。
然而，現行業界在處理全球醫療器材召回 (Medical Device Recalls) 與流向稽核時，面臨三大核心痛點：
多源異質數據割裂：美國 FDA 召回公告、台灣 TFDA 法規公告、全球唯一醫療器材識別碼 (UDID)、許可證資料庫、企業內部供應鏈分銷 (Distribution) 與採購 (Purchase) 數據散落在不同的 JSON、CSV、PDF 與紙本表單中。
人工對帳與轉譯成本高昂：將非標準格式的第三方資料轉譯為合規結構化數據、手動撰寫複雜的資料庫查詢，耗費大量合規法務與資訊人員的時間。
缺乏空間感知與動態視覺化：傳統的表格無法呈現召回醫材在空間地理上的分佈擴散風險，無法直觀暴露出高風險「來源與流向」的受災節點。
Aura-7 平台 的誕生，正是為了解決上述痛點。我們建構了一個基於先進人工智慧（Generative AI）與空間地理拓撲網絡的企業級合規監控、追蹤與召回管理工作區，將繁瑣的法規轉化為自動化、視覺化且具備高度防錯機制的數位孿生平台。
核心願景：
端到端極致透明 (End-to-End Transparency)：每一件屬於「應建立與保存來源及流向資料之醫療器材」品項之醫材，從海關進口、盤點入庫、分銷物流到院所終端，皆具備毫秒級的追蹤能力。
主動式智能干預 (Proactive AI Intervention)：利用大語言模型 (LLM) 的跨域推理能力，將事後被動補救轉化為事前合規預測、自主對帳糾錯與自動化召回範圍劃定。
多維度空間感知 (Multidimensional Spatial Awareness)：將冰冷的供應鏈流水賬轉化為動態地理分佈圖與拓撲網路圖，讓決策者直觀理解召回危機的空間蔓延路徑。
2. 核心技術架構：企業級全棧工具箱與設計模式
為了確保平台的高效能、強型別安全與卓越的使用者體驗，Aura-7 Enterprise 採用了現代工業界最成熟且最具擴充性的技術棧。
code
Code
+-----------------------------------------------------------------------------------+
|                                  Aura-7 前端層                                     |
|  [React 18 / TS] -> [Tailwind CSS v4] -> [Motion] -> [Wow HTML / Canvas / SVG]   |
+-----------------------------------------------------------------------------------+
                                         |
                                         | RESTful API / JSON RPC
                                         v
+-----------------------------------------------------------------------------------+
|                                  Aura-7 後端層                                     |
|  [Node.js / Express] -> [tsx Engine] -> [SQLite / DuckDB In-Memory SQL Engine]   |
+-----------------------------------------------------------------------------------+
                                         |
                                         | Native API / SDK Call
                                         v
+-----------------------------------------------------------------------------------+
|                                AI 核心與大語言模型層                                |
|  [Google Gemini API] (gemini-3.1-flash-lite / gemini-1.5-pro / gemini-2.5-pro)     |
+-----------------------------------------------------------------------------------+
前端架構 (The Frontend Ecosystem)
React 18 & TypeScript (TS)：平台核心基座。React 18 的 Concurrent Mode（並發模式）確保了在處理上萬筆召回資料與複雜圖表切換時，介面依舊保持流暢。TypeScript 則透過嚴格的型別定義（Type Definitions），在編譯期阻斷因欄位缺失或型別污染導致的合規計算錯誤。
Vite：極速構建工具。利用原生 ESM 特性實現模組熱更新 (HMR)，確保開發階段的敏捷度與生產環境的代碼分割 (Code Splitting) 最佳化。
Tailwind CSS (v4)：採用全新的 CSS 變數引擎與組合式設計系統，提供極致流暢的微觀原子化樣式控制，全面支援企業級暗黑模式 (Dark Mode) 與語意化色彩配置。
Motion (framer-motion)：負責系統內複雜數據面板切換、彈窗動態、空間節點脈衝 (Pulse) 效果的物理特性動畫控制，提升操作者的專注度與視覺層次。
Recharts & Dynamic SVG/Canvas Engine：用於繪製常態合規趨勢圖表，並結合低階 Canvas/SVG 混合渲染技術，實現大規模高負載下的空間圖表繪製。
後端與資料庫引擎 (The Backend & Storage Infrastructure)
Node.js & Express (TypeScript Native Via tsx)：異步事件驅動的後端運行環境。利用 tsx 執行引擎實現無需手動 Webpack 編譯的 TypeScript 原生高效執行，處理大檔案上傳與串流 (Streaming) 反應。
In-Memory SQL Serverless 引擎 (SQLite / DuckDB)：系統內置的高效能、無伺服器嵌入式關聯型資料庫。前端或後端邊緣節點可動態建立記憶體資料庫，用於承載 LLM 轉譯後的標準 SQL 指令執行，支援複雜的多表聯查 (JOIN)。
人工智慧與大語言模型核心 (The AI Core Orchestration)
Google Gemini API Suite：
gemini-3.1-flash-lite (系統預設)：作為預設的高速、低延遲推理引擎，專門負責即時的非標準數據結構化轉換（Data Standardization）、自然語言轉 SQL 命令（NL-to-SQL）以及大批量的即時欄位比對。
gemini-1.5-pro / gemini-2.5-pro (用戶自選高級模型)：具備百萬級超長上下文視窗 (Long Context Window)，用於深度理解數萬字的 FDA/TFDA 法規原始文檔、執行極為複雜的多源跨表對帳 (Autonomous Reconciliation) 任務，以及產出高達數千字的綜合性合規分析報告。
3. 三大演進功能模組技術規格
3.1 異質醫材召回數據標準化、多模型 SQL 檢索與千字 Markdown 深度摘要模組
本模組提供一站式、高度自動化的醫材召回數據生命週期管理。使用者可任意上傳非標準格式的召回資料，由 AI 核心進行標準化清洗，並轉換為關聯型資料庫進行精準的自然語言檢索。
code
Code
+------------------+      +-------------------------+      +------------------------+
| 非標準 JSON 數據  | ---> |   Gemini Standardizer   | ---> | 統一標準化 JSON 資料結構 |
+------------------+      | (模型動態切換路由機制)   |      +------------------------+
                                                                        |
+------------------+      +-------------------------+                   | Import
| 自然語言查詢關鍵字| ---> |   NL-to-SQL Generator   |                   v
+------------------+      +-------------------------+      +------------------------+
                                         |                 | In-Memory SQL 資料庫   |
                                         +---------------> | (執行標準化安全 SQL)    |
                                           SQL Command     +------------------------+
                                                                        |
                                                                        v
+-----------------------------------------------------------------------------------+
|                              終端互動式展示與分析層                                 |
| 1. SQL 語法手動修改工作區                                                          |
| 2. 應建立與保存來源及流向資料之醫療器材 (TFDA 核心品項) -> 特效高亮 (高鮮明度脈衝外框)    |
| 3. Gemini 智能摘要生成器 -> 輸出 1000 - 2000 字合規分析報告 (Markdown 格式)         |
+-----------------------------------------------------------------------------------+
A. 異質數據導入、解析與生命週期控制
操作介面設計：提供多功能檔案拖曳上傳區 (Drag-and-Drop Zone) 與即時文字粘貼區 (Textarea Clipboard)。支援對單個或批量 JSON 檔案進行實時解析。
資料操作功能：介面完整整合「下載原始檔」、「上傳新配置」、「在線網格修改 (Inline Cell Editing)」功能。任何在介面上的變更皆具備雙向資料綁定 (Two-way Data Binding)，同步更新記憶體中的狀態機 (State Machine)。
AI 資料標準化引擎 (Data Standardization Engine)：
若使用者上傳之 JSON 資料不符合系統內置的標準 Schema（定義見下文），系統會自動觸發標準化流程。
模型路由機制：系統預設調用 gemini-3.1-flash-lite。使用者可透過 UI 下拉選單動態切換為高級模型。
提示詞工程 (Prompt Engineering)：AI 接收非標準 JSON 後，將執行精準的語義對齊與缺失欄位推論（例如：將 trade_name 映射至 device_name，將 recall_level 轉換為對應的 tfda_classification 邏輯）。
標準化醫材召回資料 Schema 定義 (JSON Schema Standard v4)：
code
JSON
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "title": { "type": "string", "description": "召回事件標題或公告名稱" },
    "recall_date": { "type": "string", "format": "date", "description": "國際或國內宣告召回之日期 (YYYY-MM-DD)" },
    "device_name": { "type": "string", "description": "醫療器材英文/中文商業名稱或型號" },
    "tfda_classification": { 
      "type": "string", 
      "enum": ["應建立與保存來源及流向資料之醫療器材", "第一等級", "第二等級", "第三等級", "非屬上述列管類別"],
      "description": "台灣 TFDA 醫療器材分類分級狀態" 
    },
    "fda_regulation": { "type": "string", "description": "美國 FDA 聯邦法規編號 (例如 21 CFR 870.3610)" },
    "fda_product_code": { "type": "string", "maxLength": 3, "description": "美國 FDA 三字碼產品代碼 (e.g., DTA, LWS)" },
    "reason_for_recall": { "type": "string", "description": "導致召回的詳細技術、安全性或品質瑕疵原因" },
    "udi": { "type": "string", "description": "唯一醫療器材識別碼 (Device Identifier + Production Identifier)" },
    "lot_no_sn": { "type": "string", "description": "受影響的特定批號 (Lot Number) 或序號 (Serial Number)" }
  },
  "required": ["title", "recall_date", "device_name", "tfda_classification", "reason_for_recall", "udi"]
}
B. 自然語言轉 SQL 檢索與安全執行機制
自然語言語義理解：使用者可在搜尋列輸入如：「幫我找出 2025 年後，因為軟體異常被召回的所有第三等級與應保存來源流向的高風險心臟導管」。
SQL 生成與手動修改工作區：
系統調用選定之 Gemini 模型，將上述自然語言翻譯為標準符合 ANSI SQL 規範之查詢指令。系統不直接黑箱執行，而是彈出一個 「AI SQL 語法編譯與覆核工作區」，允許具備資安或資料庫背景的合規工程師在執行前直接手動修改 SQL 語法。
code
SQL
-- AI 自動生成的範例查詢指令
SELECT * FROM medical_device_recalls 
WHERE recall_date >= '2025-01-01' 
  AND (tfda_classification = '應建立與保存來源及流向資料之醫療器材' OR tfda_classification = '第三等級')
  AND (reason_for_recall LIKE '%software%' OR reason_for_recall LIKE '%韌體%' OR reason_for_recall LIKE '%bug%')
  AND device_name LIKE '%catheter%';
資安防禦技術：為防止惡意使用者透過自然語言進行「提示詞注入 (Prompt Injection)」進而生成破壞性 SQL（例如 DROP TABLE、DELETE FROM），系統的 SQL 執行引擎限制為唯讀權限 (Read-Only Context)，且在執行前透過正則表達式與 AST (抽象語法樹) 解析器強制攔截任何包含非 SELECT 的非授權指令。
C. TFDA 法規感知的核心品項高亮機制
法規觸發邏輯：當資料庫執行的搜尋結果返回並在前端 Grid 渲染時，系統的狀態追蹤引擎會檢製每一條紀錄的 tfda_classification 欄位。
UI 特效高亮設計：若該記錄精準匹配字串 「應建立與保存來源及流向資料之醫療器材」，系統將透過 Tailwind CSS v4 與 Motion 觸發特殊樣式：該表格行 (Table Row) 背景更換為高飽和度的警示琥珀金變調色 (bg-amber-500/10，在暗黑模式下為 bg-amber-950/40)，邊框加上 border-amber-500。最左側附加一個具備持續發光脈衝動畫 (Pulse Loop Animation) 的紅色法規標籤，並帶有浮動工具提示 (Tooltip) 顯示：「此品項屬於《醫療器材管理法》法規強制列管來源流向之高風險醫材，必須於 24 小時內完成流向稽核。」
D. 1000 - 2000 字 Markdown 綜合性合規分析報告自動生成器
執行流程：當檢索結果產出後，系統自動將當前搜尋結果之全量數據子集、用戶的檢索意圖、當前的法規上下文打包，異步發送至用戶選定的 Gemini 模型（建議使用 gemini-1.5-pro 或 gemini-2.5-pro 以獲得最佳深度推理品質）。
報告結構與字數規格：AI 被嚴格限制輸出 1000 至 2000 字、具備完美工業級 Markdown 語法層次的「召回事件綜合性合規與風險評估報告」。報告必須包含以下固定結構：
執行摘要 (Executive Summary)：當前檢索事件的宏觀統計、受災規模評估。
核心技術風險源分析 (Technical Risk Root Cause Analysis)：深度拆解召回原因（如材料疲勞、軟體演算法崩潰、無菌包裝破損等）。
TFDA 法規遵循度與潛在法律責任 (Regulatory Compliance & Legal Liability)：針對高亮列管品項，評估未在法定期限內完成通報的罰則風險（引用醫療器材管理法相關條文）。
供應鏈隔離與預防性糾正措施 (CAPA 建議)：提供具體可執行的隔離引導、下架與臨床通知步驟。
3.2 跨域多源數據融合、Wow HTML 六大圖表視覺化與動態導出模組
本模組升級為企業級多源大數據融合中心，可同時吞吐並關聯五種完全不同的醫療器材生命週期核心資料集。
A. 五大異質資料集融合與標準化 Schema 設計
系統支援上傳、粘貼 CSV 及 JSON 格式。上傳後，若格式不符，自動經由選定的 Gemini 模型執行 Schema 轉譯與補全。
TUDID 資料集 (Taiwan Unique Medical Device Identification Database)：核心主檔。包含 UDI-DI、許可證字號、全球品類代碼、製造商資訊。
醫療器材許可證資料集 (Medical Device License Dataset)：包含 許可證字號、中文品名、英文品名、有效日期、通關簽審狀態、類別。
醫療器材召回資料集 (Medical Device Recall Dataset)：即 3.1 所定義之標準化召回事件檔。
醫療器材分銷流向資料集 (Medical Device Distribution Dataset)：包含 出庫單號、UDI-PI（批號/序號）、發貨方代碼、接收方（醫療機構）名稱、出庫時間、物流追蹤碼。
醫療器材採購資料集 (Medical Device Purchase Dataset)：包含 採購訂單號、採購品項 UDI、單價、採購數量、驗收狀態、入庫庫位。
B. 搜尋關鍵字與大數據多表聯查 (Advanced Multi-Table SQL JOIN)
當使用者輸入複雜查詢（例如：「全面盤點目前在各分院中，受到本次 FDA 召回批號影響的庫存數量、當初採購的總金額，以及受影響的醫院名單」），AI 會自動產生如下的高級 SQL 命令並在工作區展示：
code
SQL
SELECT 
    dist.receiver_name AS 醫療機構名稱,
    lic.zh_device_name AS 中文品名,
    recall.udi AS 唯一識別碼,
    recall.lot_no_sn AS 受影響批號_序號,
    purch.purchase_qty AS 採購數量,
    (purch.unit_price * purch.purchase_qty) AS 採購總金額,
    recall.reason_for_recall AS 召回原因
FROM medical_device_recalls recall
INNER JOIN tudid_master tud ON recall.udi = tud.udi_di
INNER JOIN device_licenses lic ON tud.license_no = lic.license_no
INNER JOIN device_distribution dist ON recall.lot_no_sn = dist.lot_no_sn
INNER JOIN device_purchase purch ON dist.purchase_order_id = purch.order_id
WHERE recall.tfda_classification = '應建立與保存來源及流向資料之醫療器材';
C. 「Wow HTML」極致數據視覺化引擎：六大核心圖表規格
檢索結果產出後，系統將在獨立的高級畫布面板中動態渲染六個極具視覺衝擊力、具備高度互動性與動態粒子濾鏡的 Wow Charts：
圖表編號	圖表名稱	核心底層技術	視覺與互動特性 (Wow Features)	業務合規價值
Chart 1	GIS 地理空間流向分佈圖 (Geospatial Distribution Map)	WGS-84 Leaflet / Mapbox GL 混合 SVG 繪製	台灣地圖上動態標註各醫療機構。受災嚴重的院所節點會呈現暗紅色發光光環（發光半徑與受影響醫材數量成正比）。	直觀標示召回醫材在全台地理空間的擴散嚴重程度。
Chart 2	供應鏈物流拓撲網絡圖 (Supply Chain Network Graph)	d3-force (力導向拓撲網絡圖)	核心節點為製造商，分支到物流中心，再擴散至各家醫院。召回醫材流向之線條呈現高亮螢光黃色的**「粒子流動動畫 (Particle Flow Animation)」**，流動速度代表分銷頻次。	追蹤高風險醫材從源頭到終端的全鏈路拓撲結構，揪出中介高危節點。
Chart 3	召回類別與風險暴露桑基圖 (Sankey Diagram)	SVG / D3 Sankey Layout	左側為不同的召回原因，中間為醫材品類，右側為受災醫院。流動條寬度代表受影響的總金額或總數量，懸停時流動條會產生色彩漸變與數值提示。	視覺化呈現風險源頭如何流向不同的終端，展示風險傳導機制。
Chart 4	合規時序變遷與違規預警趨勢圖 (Temporal Timeline Horizon)	Recharts / Canvas 雙軸圖	X 軸為時間軸，Y 軸左側為召回事件密度，右側為未通報違規天數。具備漸變區域陰影（Gradient Area）與臨界值警告紅線。	監控全公司或全區域合規健康度隨時間的演變趨勢。
Chart 5	醫材生命週期損耗與庫存漏斗圖 (Funnel Risk Analytics)	SVG CSS Clip-Path	呈現從「許可證核發 -> 採購進庫 -> 轉運分銷 -> 醫院驗收 -> 臨床消耗」的各階段留存率，危險流失階段（如未經驗收即進入臨床）會以紅色鋸齒狀切口特效顯示。	精準抓出合規數據鏈路在線下的斷裂點與損耗點。
Chart 6	法規分級風險暴露矩陣雷達圖 (Regulatory Radar Chart)	Recharts Radar Engine	呈現六個維度的安全指標：法規覆蓋率、批號可追蹤度、召回響應速度、供應鏈集中度、過期風險係數、來源明晰度。覆蓋區域採半透明極光色填充。	供高階主管一秒評估當前企業法規合規架構的整體防禦力與薄弱環節。
動態過濾器 (Interactive Filter Shell)：所有圖表與底層 Grid 數據共享同一個響應式狀態中心。使用者可利用右側懸浮的 Filter Panel（包含 滑桿式日期篩選、法規分級複選框、採購金額區間滑塊）進行實時過濾，所有六大圖表與 SQL 結果集將在 16ms 內同步完成 Motion 淡入淡出重新渲染。
D. Wow HTML 多格式一鍵打包導出引擎
平台建構了強大的邊緣端文件編譯器，允許使用者將當前包含六大圖表、SQL 數據、Markdown 摘要的整個工作區打包導出為以下格式：
JSON：完整匯出洗淨後的關聯化結構數據陣列，符合標準 REST 傳輸規範。
PDF：調用前端 window.print() 與預設的 CSS 分頁媒體查詢 (@media print)，自動將六大圖表與 Markdown 報告重新排列為適合 A4 紙張、帶有企業浮水印與頁碼的高級合規報告。
MD (Markdown)：純文字格式導出，完美保留完整的 Markdown 標題、表格與 AI 產出的風險評估。
HTML (Wow HTML 獨立運行檔)：此為本平台的殺手級功能。 系統會將當前所有的數據、視覺化圖表的輕量級渲染引擎、Tailwind 樣式庫以及當前的全量資料集，封裝並編譯成單個獨立的 .html 檔案。使用者下載後，在完全離線、無網路的環境下雙擊該檔案，依然可以在任何瀏覽器中流暢操作上述六大圖表、執行動態過濾與數據檢視。
3.3 先進 3 大全新「驚豔」AI 未來感擴展功能設計
本模組旨在解決「數據源頭碎片化」的問題，賦予系統將非結構化的各國官方原始公告文檔，轉化為生產級結構化合規數據的能力。
A. 原始文檔結構化提取與生成工作流
文檔吞吐能力：使用者可直接上傳或粘貼美國 FDA 或台灣 TFDA 的原始召回公告，支援 TXT, MD, PDF, JSON 等格式。
AI 智能特徵提取：系統固定調用 gemini-3.1-flash-lite 執行高速解析（或用戶自選其他高級模型），精準從萬字冗長的法律與技術公告中，抽取出 3.1 節所定義的標準 JSON Schema 欄位。
自適應標準化管道 (Pipeline)：若提取出的資料存在缺失值，AI 將啟動上下文推理（例如：根據 FDA Product Code 自動反查對應的常規醫療器材品名，或根據公告內容推估其在台灣 TFDA 規範下是否屬於「應建立與保存來源及流向資料之醫療器材」）。使用者可在介面中下載、再次上傳或直接在 Grid 中進行修改與人工校核。
B. 3 大全新「驚豔」AI 未來感擴展功能設計
1. AI 驅動的預測性風險熱圖與擴散動態模擬器 (Predictive Risk & Contagion Simulator)
技術實現：本功能超越傳統的靜態數據展示。當用戶導入一筆全新的 FDA 召回事件時，後端 AI 代理（調用 gemini-1.5-pro 或更高階模型）會立刻主動讀取企業內部當前的「分銷流向資料集」與「採購資料集」。
WOW 點與視覺特效：AI 會在 Chart 1 (GIS 地理空間流向分佈圖) 上啟動擴散粒子動畫。它會根據過去六個月該款醫材在各醫院間的調撥頻率與消耗速率，模擬預測未來 14 到 45 天內，這批召回醫材可能隨患者轉院、跨院物流而擴散至其他未登記院所的「潛在風險熱區」。在地圖上，這些預測危險區域會呈現橙色發光光環與動態漣漪效果 (Ripple Effect)。這能讓合規主管在危機發生前，提前下達預防性封存指令。
code
Code
[ 新導入召回事件 ] 
       │
       ▼
[ AI 預測引擎 (Gemini 1.5 Pro) ] ──(結合歷史採購/分銷流向數據)
       │
       ├──> 預測擴散概率、耗用速度與調撥路徑
       ▼
[ Chart 1 GIS 畫布 ] ──> 實時繪製「橙色發光漣漪熱區 (Predictive Hotspots)」
2. 自主多源法規對帳、語義去重與糾錯代理人 (Autonomous Semantic Reconciliation Agent)
技術實現：在實務操作中，人工輸入的 UDI、批號或序號經常會因為肉眼誤讀（例如將條碼中的字母 O 誤打為數字 0，將 B 誤打為 8）或者不同資料庫間的命名不一致（例如「台大醫院」與「國立臺灣大學醫學院附設醫院」），導致 SQL 精準查詢失效。
WOW 點與互動設計：本功能是一個常駐的 AI Agent。當異質資料導入時，它會自動進行多源語義對帳。如果發現分銷單與採購單存在 1 碼的序號差異，且物流時間完全吻合，系統不會直接報錯，而是會在介面右下角彈出一個極具質感的 AI 助手視窗：
💡 Aura-7 自主對帳提示：「我發現分銷資料集中的序號 SN-94830O7 與採購資料集中的 SN-9483007 存在 98.6% 的語義重合度。根據過去本院掃描槍的誤差模式，此處極可能為 O/0 誤判。我已自動將其關聯。點擊 [確認修正] 將自動更新底層關聯資料庫並同步更新六大 Wow 圖表。」
3. 語音互動式合規協同代理人 (Voice-Activated Compliance Co-Pilot via Web Audio)
技術實現：本功能專為雙手正在執行盤點、無菌操作或手套不便觸碰螢幕的倉儲與手術室管理員設計。整合 HTML5 Web Audio API 與 Gemini 的語音流處理技術。
WOW 點與互動設計：使用者點擊介面上的微型麥克風圖示（或使用喚醒詞 "Aura"），直接說出法規查詢意圖：「Aura，幫我高亮所有北部地區屬於來源流向管制的嚴重召回醫材，並切換到供應鏈拓撲網絡圖。」
系統的語音代理會即時完成語音轉文字 (STT)、意圖意圖解析、動態過濾器參數修改、觸發 Chart 2 全螢幕最大化切換，並以清晰流暢的語音合成 (TTS) 回報：
🎙️ Aura-7 語音回報：「已為您找到 3 筆符合《醫療器材管理法》法規強下列管之核心召回品項。目前已切換至供應鏈拓撲網絡圖，高危流向粒子通道已為您用黃色螢光標註，請查看中央顯現的物流斷裂點。」
3.4 LLM 執行配置與實時監控日誌模組
為了提供開發者與高階合規主管百分之百的掌控感，系統提供了完全透明的 LLM 調控台與實時日誌系統。
code
Code
+---------------------------------------------------------------------------------+
|                       Aura-7 LLM 執行配置與診斷中心                             |
+---------------------------------------------------------------------------------+
| [模型選擇] ⊙ gemini-3.1-flash-lite (預設)  ○ gemini-1.5-pro  ○ gemini-2.5-pro   |
| [系統提示詞 System Prompt]                                                      |
| ┌─────────────────────────────────────────────────────────────┐                |
| │ You are an expert TFDA medical device regulatory auditor... │                |
| └─────────────────────────────────────────────────────────────┘                |
| [溫度參數 Temperature] [ 0.2 ]  [最大 Token 輸出 Max Tokens] [ 4096 ]            |
|                                                                                 |
| ⚡ [實時神經診斷日誌 Live Terminal Log] (Auto-scrolling)                        |
| ┌─────────────────────────────────────────────────────────────┐                |
| │ 12:04:15 [SYS] System initialized under Traditional Chinese.│                |
| │ 12:04:16 [API] Calling gemini-3.1-flash-lite via JSON Schema│                |
| │ 12:04:18 [LLM] Token used: Input 1,204 | Output 542 (1.8s)  │                |
| │ 12:04:18 [DB] Loaded 12 records into In-Memory SQL database │                |
| └─────────────────────────────────────────────────────────────┘                |
+---------------------------------------------------------------------------------+
A. 多模型選擇與自定義 Prompt 編輯面板 (Control Center)
UI 配置：在設定抽屜面板 (Settings Drawer) 中，提供模型切換下拉選單。
Prompt 實時調整：暴露系統提示詞 (System Prompt) 及任務提示詞 (Task Prompt) 編輯區 (TextArea)，支援一鍵還原預設、參數調整（例如 Temperature 控制隨機度、Max Tokens 控制報告長度）。這允許使用者針對不同國家的法規嚴格程度調整 AI 的推論語氣。
B. 「Wow」LLM 執行狀態指示器與動畫特效
動態指示器 (LLM Spinning Core)：當系統向 Google Gemini API 發送數據並等待響應時，畫面上會浮現一個帶有 CSS 特效的**「神經突觸漫射發光動畫 (Glowing Synapse Animation)」**，伴隨著由 Motion 驅動的數據粒子向中心黑洞匯聚的 3D 視覺阻尼。這徹底消除了用戶等待數據處理時的焦躁感。
即時日誌終端 (Live Scrolling Log Terminal)：在工作區底部整合一個黑客帝國風格的復古命令行 Terminal 元件。它以串流 (Streaming) 形式將後端或 API 正在執行的底層指令即時輸出。例如：
[12:04:15] INFO: Initializing standard pipeline via gemini-3.1-flash-lite...
[12:04:16] API_CALL: Sending raw FDA markdown text to Google Endpoint...
[12:04:17] SCHEMA_OK: UDI structural alignment check 100% passed.
[12:04:18] SQL_EXEC: Successfully executed standard query on in-memory database.
C. 多語言與多色彩配置自適應
雙語體系：支援一鍵在「繁體中文」與「English」之間切換，所有圖表 Label、AI 生成報告、表格標題、系統狀態均會自適應翻譯。
Pantone 色彩美學：平台內置十種經典的 Pantone 品牌主題色彩配置（如經典藍、活珊瑚橘、極致灰等），全面支持亮色/暗色模式 (Light/Dark Contrast Modes)，所有面板、卡片與地圖均會進行細緻的重繪，確保極致的高級感。
4. 數據對接與庫存狀態機矩陣
本平台核心數據機制建立在對**「召回公告」與「採購/流向報表」**的精準關聯上。透過以下狀態機，系統將每一筆醫材條目歸入對應的合規風險狀態：
code
Code
+-----------------------------+
                    | 異質資料集導入：分銷、採購  |
                    +-----------------------------+
                                   │
                                   ▼
                   +───────────────────────────────+
                   |  雙向 UDI 條碼與批號交叉比對  |
                   +───────────────────────────────+
                                   │
         ┌─────────────────────────┼─────────────────────────┐
         ▼                         ▼                         ▼
  [ 兩端數據完美匹配 ]      [ 分銷有記錄，採購無記錄 ] [ 採購有記錄，分銷無記錄 ]
         │                         │                         │
         ▼                         ▼                         ▼
   ● 帳籍吻合 (Matched)     ● 出庫未登 (Unreported)     ● 幽靈帳籍 (Ghost Stock)
   (安全，綠色高亮)         (合規漏洞，黃色警告)       (非法侵入，紅色爆閃)
● 帳籍吻合 (Matched)：出貨方與接收方記錄完全對齊，且批號有效。
● 出庫未登 (Unreported Discrepancy)：發貨商資料庫顯示已將召回批次發出，但醫院端並無登記採購或入庫。此為嚴重的監管黑洞。
● 幽靈帳籍 (Ghost Stock Entry)：醫院端登記使用了該批次醫材，但進口商/發貨商的分銷記錄中完全缺失此條目。這代表可能存在平行輸入（俗稱水貨）或渠道登載失能。
● 效期告警 (Critical Lifecycle Warning)：該醫材（如植入式起搏器）已入庫，但其無菌消毒到期日剩餘不足 30 天，系統會標註為黃色閃爍状态，提示應即時執行重新分配。
5. 潛在 Bug 與邊緣情況防禦機制
5.1 React 19 渲染不匹配、閉包陷阱與 useEffect 依賴無限循環預防
問題根源：React 19 的 Concurrent 渲染與 D3.js/Leaflet 等直接操作 DOM 的第三方庫混用時，常會因為 DOM 被多次重新掛載 (Remount) 而導致 Canvas 閃爍或地圖圖層疊加。此外，不當的狀態依賴會導致 useEffect 觸發無限次的 API 請求與重繪。
預防機制：
所有地圖與拓撲圖的初始化均包裹在單次執行的 useRef 狀態保證中。
嚴格分離 「數據狀態 (React State)」 與 「繪圖實例 (DOM Refs)」。
任何 useEffect 依賴項均使用 Primitive 變數（如 JSON.stringify(filterState)），並加入 cleanup 函數，在元件解除掛載 (Unmount) 時顯式銷毀 D3 動態事件監聽與 Canvas 繪圖上下文。
5.2 記憶體洩漏 (Memory Leakage) 與垃圾回收機制
問題根源：Wow 視覺化引擎包含高頻渲染的 Web Audio API 節點與 D3 力導向模擬器 (Force Simulation)。如果不顯式銷毀，瀏覽器分頁在長時間運行後會迅速吃滿記憶體，最終導致崩潰。
預防機制：
在 Canvas 渲染器中，每次重繪前呼叫 context.clearRect()，並對緩衝區做釋放。
對於 Web Audio API，當用戶關閉語音助理時，顯式呼叫 audioContext.close() 釋放硬體音源。
5.3 SQL 注入防禦與 AST 語法樹校驗
問題根源：雖然 In-Memory SQL 引擎運行在沙箱中，但惡意使用者可能透過自然語言注入引導 AI 產生 DROP TABLE、UPDATE 等破壞性指令。
預防機制：
系統的 SQL 執行引擎限制為唯讀 (ReadOnly) 模式。
前端與後端設有攔截過濾器，透過正規表達式與輕量級 SQL AST (抽象語法樹) 解析器，強制校驗 SQL 指令首詞必須為 SELECT、WITH 或 EXPLAIN，任何包含分號 ; 串聯、UNION 或是 INSERT/UPDATE 的語句將直接被拒絕執行。
5.4 異質編碼衝突與 CSV Excel 巨集注入 (Excel Macro Injection) 防禦
問題根源：台灣 TFDA 的 CSV 常包含 Big5 編碼的繁體中文字元，直接讀取會產生亂碼。此外，導出 CSV 時，若欄位內容包含 =CMD('calc') 等惡意代碼，當合規官員在 Excel 打開時會觸發系統木馬。
預防機制：
後端解析器全面配置 iconv-lite 自動檢測並將 Big5/UTF-8 轉換為統一的 Unicode 字符串。
導出 CSV 時，對所有單元格字串首字元（如 =, +, -, @）進行強制單引號 ' 轉義。
6. 20 個全面性後續問題 (20 Comprehensive Follow-up Questions)
為進一步優化本平台的架構設計，並在後續的迭代中達到絕對完美的生產級表現，請與團隊深入評估以下 20 個覆蓋效能、安全、法規、演算法與架構的關鍵技術問題：
6.1 地圖渲染效能 (Geospatial Performance)
若平台導入的醫療機構節點從目前的數十家擴增至全台灣上千家診所與藥局，Chart 1 的 Leaflet/SVG 混合渲染會出現掉幀嗎？是否需要強制引入 WebGL 或是 Canvas 叢集 (Clustering) 技術？
6.2 離線 Web Worker 執行 (Offline Computing)
在 3.2 中提到的獨立 HTML 導出功能 (Wow HTML) 中，若用戶處於完全斷網環境，我們該如何將 Gemini 的標準化與對帳能力透過 Web Assembly (Wasm) 或輕量級本地端規則引擎在瀏覽器本地線程 (Web Worker) 中部分實現？
6.3 SQL 注入深度防禦 (SQLi Defense)
目前的唯讀 context 和正則攔截是否足以應付變形極為複雜的 SQL 注入提示詞（例如透過 Hex 編碼或是 Union 繞過）？是否需要引入更嚴格的 SQL 抽象語法樹 (AST) 沙箱解析器來徹底隔絕生成惡意 DDL/DML 的可能？
6.4 語義快取機制 (Semantic Cache)
頻繁將自然語言轉換為 SQL 指令會消耗大量的 Gemini API Token 並產生延遲。我們是否應該在後端架構中引入基於向量相似度 (Vector Similarity) 的 Redis 語義快取，來直接命中相似的歷史查詢？
6.5 異質資料關聯消歧義 (Entity Disambiguation)
當不同的用戶在上傳採購和分銷資料時，對同一家醫療機構的稱呼完全不同（例如「北榮」、「台北榮總」、「榮總」），AI Agent 在執行關聯對帳時，其消歧義 (Disambiguation) 的信心門檻值 (Confidence Threshold) 應如何設定，以避免錯誤合併？
6.6 應保存來源流向醫材的動態法規更新機制 (Dynamic Legislation Update)
TFDA 公告的「應建立與保存來源及流向資料之醫療器材」品項清單會隨時間滾動修正。當法規品項增加或移除時，平台如何實施動態法規庫更新，而不需要重新動到硬編碼 (Hard-coded) 的程式碼？
6.7 行動端響應式視覺化適配 (Mobile Responsiveness)
六大 Wow 圖表（特別是 D3 力導向網絡拓撲圖與桑基圖）在 6.1 吋手機螢幕上的視覺體驗極差。我們應該設計怎樣的斷點 (Breakpoints) 降級策略？是改為條列式卡片，還是提供局部的視窗縮放 (Viewport Panning)？
6.8 大檔案分片上傳與串流解析 (Chunked Uploads & Streaming)
若用戶導入高達 500MB 的歷史醫療器材採購 CSV 檔案，原生的 JSON.parse 或 Express body-parser 會導致 Node.js 記憶體溢出 (OOM)。後端架構該如何切換為 fs.createReadStream 結合 csv-parser 的流式架構？
6.9 AI 幻覺控制與 CAPA 法律責任免責 (Hallucination & Liability)
3.1 中 AI 生成的 2000 字 Markdown 風險報告若出現「品牌誤判」或「法規條文誤引用」之幻覺 (Hallucination)，在 UI 設計上應如何安插「人工覆核覆蓋機制」與醒目的法律免責聲明，以規避醫療法規法律責任？
6.10 唯一的 UDI 解析與校正演算法 (UDI Parsing)
國際 GS1 標準下的 UDI 包含 DI（產品識別）與 PI（生產識別，含批號、效期）。當用戶掃描條碼時常會帶入多餘的應用識別碼 (AI)。系統是否需要內置標準的 Regex UDI Parser 作為 AI 標準化前的第一道防線？
6.11 多模型並發與熔斷機制 (Model Fallback & Circuit Breaker)
當預設的 gemini-3.1-flash-lite 遭遇 Google 服務端 API 限流 (Rate Limit Exceeded) 或服務中斷時，後端的 AI 路由引擎該如何實作自動熔斷並降級切換至其他備用模型，以確保醫療現場的可用性？
6.12 Wow HTML 導出的資安與代碼注入防禦 (XSS & CSP)
3.2 支援將全量數據與引擎打包成單一 HTML。如何確保導出的 HTML 檔案不會被惡意第三方注入跨站腳本 (XSS)？在封裝過程中需要經過哪些嚴格的字串轉義 (Escaping) 與 CSP (內容安全策略) 宣告？
6.13 資料脫敏與患者隱私保護 (Data Masking & HIPAA/GDPR)
在分銷和採購資料集中，若部分醫療機構誤將患者的病歷號、姓名或手術登記資料與醫材序號綑綁上傳，系統的 AI 洗淨管道該如何實施自動化的 PII (個人身分識別資訊) 偵測與去識別化脫敏？
6.14 PDF 導出時的跨頁斷裂優化 (CSS Page-Break)
當 Markdown 報告長達 2000 字且帶有六大圖表時，普通的 PDF 導出經常會導致圖表被從中間切斷分頁。我們該如何利用 CSS 的 page-break-inside: avoid; 和 break-after 屬性來精確控制列印排版？
6.15 語音互動的環境噪音消除與 VAD 技術 (Voice Activity Detection)
在吵雜的醫院資材倉庫或手術室預備區，語音語意助理 (3.3) 容易受到背景雜音干擾。我們是否需要在前端引入 Web Audio API 的低通濾波器 (Low-pass Filter) 或 Voice Activity Detection (VAD) 演算法來精準切取人聲？
6.16 密鑰安全性與邊緣端部署 (Secrets Management)
若平台需要部署到個別醫院的私有雲環境 (On-Premise Kubernetes)，Google Gemini API Key 的存放與輪轉 (Rotation) 機制該如何與醫院內部的 HashiCorp Vault 或 K8s Secrets 整合，避免密鑰外洩？
6.17 多租戶資料隔離架構 (Multi-Tenant Isolation)
若本平台升級為 SaaS 雲端版本供多家不同的醫材代理商同時登入使用，在底層的 SQLite/DuckDB 記憶體資料庫路由上，該如何確保 A 廠商絕對無法透過精心設計的 SQL 語法跨界查詢到 B 廠商的採購與分銷機密數據？
6.18 CSV 注入攻擊全面防禦 (Excel Macro Injection)
在 3.2 的數據導出功能中，若某條召回原因或設備名稱中包含 =CMD('calc') 等惡意 Excel 公式字元，當合規人員下載 CSV 並在 Excel 中開啟時會觸發巨集攻擊。我們的導出引擎是否已對所有單元格字串首字元進行了強制單引號 ' 轉義？
6.19 Canvas 繪圖緩衝與記憶體洩漏防護 (Memory Leakage)
在頻繁進行多模型 SQL 檢索與動態過濾時，六大 Wow 圖表會不斷地銷毀與重新創建。如何確保 Canvas 畫布、D3 拓撲網絡圖的 Event Listeners、以及 Web Audio 的 AudioContext 在 React 元件解除掛載 (Unmount) 時被 1000% 釋放，防止瀏覽器分頁崩潰？
6.20 合規審計日誌與區塊鏈存證準備 (Audit Trail & Blockchain Readiness)
根據法規要求，召回數據的變更與通報歷程必須具備不可篡改性。我們是否應該在後端 Express 管道中為每一次的資料導入、修改與 SQL 查詢建立基於 SHA-256 的鏈式審計日誌 (Append-Only Audit Log)，以便未來無縫對接區塊鏈存證系統？
