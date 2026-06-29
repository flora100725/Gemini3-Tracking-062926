ura-7 Medical Device Recall and Compliance Intelligence Platform
全球醫材合規追蹤與主動式安全防護系統——企業級完整技術規格與架構白皮書 (v4.0.0-Enterprise)
1. 項目背景與系統願景 (Executive Summary & Project Vision)
1.1 背景背景與法規痛點
在高價值、高風險醫療器材（如 Class-II 與 Class-III 植入式心律調節器、冠狀動脈支架、人工水晶體等）的全球供應鏈管理中，數據的「真實性」、「即時性」與「流向追蹤完整性」直接關係到患者的生命安全。根據中華民國《醫療器材管理法》第 22 條、第 23 條（流向主動申報與登載）以及第 35 條（安全監視與主動通報義務），主管機關對於特定高風險醫材實施了極為嚴厲的流向管制政策。
然而，在跨國供應鏈與臨床實務的交匯點，往往存在以下四大核心痛點：
異質數據孤島： 來自美國 FDA 的召回公告、台灣 TFDA 的進口許可證、GS1 的 TUDID 唯一識別碼、WHO Medevis 的分類命名、以及醫療院所內部的採購庫存（QMS/ERP）系統，其格式、編碼、語系各不相同。
人工帳籍摩擦： 發貨商的「出庫單（Distribution Ledger）」與臨床醫療機構的「收貨單（Purchase Ledger）」時常因為手動登錄誤差、字元混淆，導致產生「出庫未登（Unreported）」或「幽靈庫存（Ghost Stock）」等合規黑洞。
過動能失效警報： 醫材的滅菌有效期限（Sterilization Expiry）或電池妥善率在在途儲運或庫存積壓中衰退，缺乏空間感知的動態調撥機制。
分析工具斷層： 傳統法規審查官與醫療管理人員面對百萬級條碼和公告文獻時，只能依靠人工比對，缺乏直觀的、具備神經推理能力的動態視覺化大屏。
1.2 Aura-7 系統願景
Aura-7 是一個專為食品藥物管理署 (TFDA) 官方稽核官員、臨床資產管理專家、以及跨國醫材供應商設計的**「代理型主動追蹤與合規空間智慧稽核平台」**。平台將傳統的靜態表格稽核，轉化為具備地理空間感知（WGS-84 Projection）、大語言模型（Generative LLM）神經推理能力、以及多源異質數據融合的動態智慧監控中心。
本規格書詳細定義了 Aura-7 v4.0.0 企業級版本的全局技術架構，包含：
基於 Frosted Glass (磨砂玻璃/冰極透鏡) 的極致美學 UI 系統與雙語/雙主題切換矩陣。
基於 Gemini-3.1-Flash-Lite 為預設核心、兼容多模型的「自然語言轉 SQL」與「文獻結構化提取」雙引擎沙盒。
六大 "Wow" 互動視覺化圖表與隨行動態日誌 (Live Stream Log)。
三大前瞻性 "Wow" AI 代理模組，將事後處置徹底轉化為全自動、智能化的事前防護。
2. 全球實體架構與多代理技術棧 (Global Architecture & Tech Stack)
Aura-7 採用了分散式微服務、嵌入式記憶體計算、與大型語言模型 (LLM) 多代理協作（Multi-Agent Orchestration）的混合架構。系統在保障高安全隔離度的同時，能提供極致流暢的前端交互。
code
Code
+--------------------------------------------------------------------------------------------------+
|                                    Aura-7 Frontend Workspace                                     |
|  +-----------------------------+  +-------------------------------+  +------------------------+  |
|  |     React 18 / TS Engine    |  |  Tailwind CSS v4 (Frosted)    |  | Motion Flow Transitions|  |
|  +-----------------------------+  +-------------------------------+  +------------------------+  |
|  |     D3 / SVG WebGL Map      |  |  Recharts Wow Dashboard       |  | Client SQL Executor    |  |
|  +-----------------------------+  +-------------------------------+  +------------------------+  |
+------------------------------------------------+-------------------------------------------------+
                                                 | HTTPS / Secure WebSockets
                                                 v
+--------------------------------------------------------------------------------------------------+
|                                    Aura-7 Express Gatekeeper                                     |
|  +-----------------------------+  +-------------------------------+  +------------------------+  |
|  |    Express API Middleware   |  |   DuckDB-Wasm Client Database |  |  Security Sanitization |  |
|  +-----------------------------+  +-------------------------------+  +------------------------+  |
+------------------------------------------------+-------------------------------------------------+
                                                 | Secure API Tunneling
                                                 v
+--------------------------------------------------------------------------------------------------+
|                                       Google GenAI Network                                       |
|  +--------------------------------------------------------------------------------------------+  |
|  |  Model Router (Default: gemini-3.1-flash-lite | gemini-1.5-pro | gemini-2.5-pro)            |  |
|  +--------------------------------------------------------------------------------------------+  |
|  |  RAG Vector Context (TFDA Legal Corpus) & Real-time Synthesis Piplines                     |  |
|  +--------------------------------------------------------------------------------------------+  |
+--------------------------------------------------------------------------------------------------+
2.1 前端核心技術與視覺引擎
React 18 & TypeScript (Strict Mode)： 利用 React 18 的 Concurrent 模式與 Transition API 來渲染大型合規數據集，並藉由 TypeScript 嚴格型別定義杜絕運行時崩潰。
Vite 伺服器建構引擎： 基於 Esbuild 的超高速熱更新 (HMR) 構建系統，提供毫秒級的開發反饋與高度優化的生產端代碼 Bundle。
Tailwind CSS v4： 採用最新原子化 CSS 引擎優化渲染效能，在不依賴外部庞大 CSS 檔案的前提下，利用自適應變數實現極致的視覺自定義。
Motion (Framer Motion) v12： 提供 60fps 的硬體加速動畫，用於動態警告脈衝、側邊欄無縫滑動與數據列重排。
Wow-Visualization Paint (D3 / Recharts)： 基於 HTML5 Canvas 與 D3 混合構建，優化在渲染上萬條地理軌跡與拓撲網絡時的幀率表現。
2.2 後端與嵌入式計算核心
Node.js & Express 運行環境： 採用非同步非阻塞 I/O 架構，提供高密度的 API 路由與大檔案串流上傳。
tsx (TypeScript Execute Runtime)： 免去冗長的編譯等待，提供原生高效的後端 TypeScript 直譯執行環境。
DuckDB-Wasm 局部沙盒： 在前端或伺服器端內嵌輕量級、極速的高性能關聯引擎，用以支撐由大語言模型動態生成的 SQL 指令進行即時多維分析。
2.3 人工智慧核心 (The AI Core Orchestration)
Google GenAI SDK (v2.4.0)： 採用最新 @google/genai 庫，徹底淘汰舊版代碼。預設採用 gemini-3.1-flash-lite 處理高吞吐量的數據清洗與 SQL 轉換，用戶可彈性切換至 gemini-2.5-pro 進行深度的召回原因因果推理與跨國法規交叉比對。
3. Frosted Glass 視覺風格與國際化設計 (Aesthetic & Internationalization)
Aura-7 v4.0.0 完美吸收了 Frosted Glass (磨砂玻璃/冰極透鏡) 的極致美學，在確保高度專業感與 Scannability (易讀性) 的同時，提供兼具未來科技感與眼力保護的介面。
code
Code
+------------------------------------------------------------------------------+
| [AURA-7 ENTERPRISE]                                                          |
|                                                                              |
|  +----------------------+  +----------------------------------------------+  |
|  | CONTROL TOWER        |  | MAIN WORKSPACE (Frosted Glass Canvas)        |  |
|  |                      |  |                                              |  |
|  |  [Model Selection]   |  |  +----------------------------------------+  |  |
|  |  - gemini-3.1-lite   |  |  | 6 WOW GRAPHS GRID (Glassmorphism Cards) |  |  |
|  |                      |  |  +----------------------------------------+  |  |
|  |  [Directives Editor] |  |                                              |  |
|  |  - Input prompt...   |  |  +----------------------------------------+  |  |
|  |                      |  |  | COMPLIANCE TRACKING GRID (Data Grid)     |  |  |
|  |  [Lang: 中文/EN]     |  |  +----------------------------------------+  |  |
|  |  [Theme: Light/Dark] |  |                                              |  |
|  +----------------------+  +----------------------------------------------+  |
+------------------------------------------------------------------------------+
3.1 磨砂玻璃設計語彙與 Tailwind CSS 實作
系統的主介面被設計成一個懸浮於動態漸變光暈（Background Mesh Gradients）之上的多層次玻璃面板。
背景光暈 (Ambient Backdrops)：
在畫面的左上角與右下角，分別佈置了 indigo-900/30 與 blue-900/20 的巨型模糊圓形（Blur [120px] 至 [150px]），這兩個光暈在背景中緩慢進行波浪狀位移，模擬宇宙星雲的呼吸感。
玻璃擬態屬性 (Glassmorphism Properties)：
主工作區卡片採用 bg-slate-900/40，並配合強大的 backdrop-blur-xl。
邊框採用細緻的高對比半透明描邊：border border-white/5 或 border-slate-800/50，形成晶瑩剔透的物理邊界。
陰影採用柔和的立體投影：shadow-[0_8px_32px_0_rgba(0,0,0,0.37)]。
3.2 雙主題色彩矩陣 (Light / Dark Mode Transition Matrix)
系統不單純提供深色調，更實作了基於「CSS 自定義變數（CSS Variable Injector）」的一鍵重構主題樣式表，確保在亮色模式下依舊保有完美的對比度：
語義化顏色變數 (Semantic Tokens)	深色科技模式 (Dark Mode - Default)	亮色無菌模式 (Light Mode)
--bg-base	#0b0f19 (深邃藍黑)	#f1f5f9 (極地灰白)
--bg-surface	#131a2c (磨砂夜色)	rgba(255, 255, 255, 0.6) (純白玻璃)
--bg-surface-elevated	#1e2942 (高亮藍灰)	#e2e8f0 (高亮灰白)
--border-main	rgba(255, 255, 255, 0.05)	rgba(15, 23, 42, 0.08)
--text-main	#f3f4f6 (極地雪白)	#0f172a (深邃板岩灰)
--text-muted	#9ca3af (霧藍灰)	#64748b (經典石板灰)
3.3 雙語切換網關 (🌐 Dual Language Integration)
為滿足跨國發貨商（如美國 Medtronic、Boston Scientific）、台灣代理商、與 TFDA 本地稽核官員的協同作業，系統內建**「中英切換網關 (Traditional Chinese / English)」**。
預設語系： 繁體中文 (Traditional Chinese)。
本地化對應：
所有介面控制項、動態事件日誌 (Log)、雷達圖提示、以及由 Gemini 神經生成的合規分析報告，均能在兩套語系字元集之間即時流暢切換，並保持語意精準度。
對於專有名詞（如 Class-I / 1級召回、UDI / 唯一醫療器材識別碼），在英文介面下採用標準 FDA 術語，在繁體中文介面下自動對標《醫療器材管理法》的法定中文名稱。
4. 多維數據融合與大模型管線 (Multi-Dataset Fusion & LLM Pipelines)
Aura-7 的核心運算威力，建立在對五大領域數據集的深度融合，以及由 Gemini 驅動的自適應清洗與轉換管線之上。
4.1 五大領域異質數據集規格
1. 醫療器材召回數據集 (Medical Device Recall Dataset)
特徵： 來自 FDA / TFDA 的召回通報，多為英文非結構化文本。
核心欄位：
title (召回標題，如 Class 1 Device Recall Abiomed Impella)
recall_date (召回發布日期，統一為 YYYY-MM-DD)
device_name (受影響之設備名稱)
tfda_classification (TFDA 法定級數，如 1級、2級、3級)
fda_regulation (FDA 法規條號，如 21 CFR 870.3610)
fda_product_code (三字產品代碼，如 DVE)
reason_for_recall (召回詳細原因)
udi (唯一產品識別 DI 碼)
lot_sn (受影響的特定生產批號或序號)
2. 醫材許可證資料集 (Medical Device License Dataset)
特徵： 台灣 TFDA 核發的進口或製造許可證資訊。
核心欄位：
license_number (許可證字號，如 衛部醫器輸字第000001號)
device_class (醫療器材級數，如 2、3)
chinese_name (中文品名)
sub_category (醫器次類別一)
applicant_name (申請商名稱)
manufacturer_country (製造廠國別)
valid_date (有效日期)
unified_id (申請商統一編號)
3. TUDID 資料集 (GS1 Unique Device Identification Database)
特徵： UDI 基礎發碼與對照資料。
核心欄位：
license_number_ref (許可證字號)
udi_agency (UDI 發碼機構，如 GS1, HIBCC)
basic_di (基本 DI)
model_number (型號)
brand_name (中文/英文品名)
status (註銷狀態)
4. WHO Medevis 資料集 (Global Medical Device Nomenclature)
特徵： 歐盟 EMDN 與全球 GMDN 命名代碼映射關係。
核心欄位：
device_name_generic (通用名稱)
emdn_code (EMDN 編碼)
emdn_term (EMDN 術語)
gmdn_code (GMDN 編碼)
gmdn_term (GMDN 術語定義)
5. 品質管理系統資料集 (QMS Dataset)
特徵： 製造廠核備函 (QSD) 與廠房合規稽核狀態。
核心欄位：
manufacturer_name (製造廠名稱)
manufacturer_country (製造廠國別)
qsd_number (QSD 證號，如 QSD16050)
valid_date (有效日期)
audit_status (案件狀況，如 准予核備、續予核備)
approved_scope (英文許可品項與製造範圍)
4.2 非標準數據自動洗淨與重組管線 (Self-Healing Sanitizer)
當用戶手動貼入或拖曳上傳不規範的 CSV / JSON 數據時，Aura-7 後端會自動攔截，並啟動由 Gemini-3.1-Flash-Lite 驅動的自適應重組管線 (Adaptive Restructuring Pipeline)。
code
Code
+------------------------+      +---------------------------+      +---------------------------+
| User Uploads Row Data  | ---> |   AI Schema Interceptor   | ---> | Structural JSON Matching  |
| (Messy JSON/CSV)       |      | (Gemini-3.1-Flash-Lite)   |      | (Validates via JS Schema) |
+------------------------+      +---------------------------+      +---------------------------+
                                                                                 |
                                                                                 v
                                                                   +---------------------------+
                                                                   | Standardized Import Table |
                                                                   | (Ready for DuckDB engine) |
                                                                   +---------------------------+
清洗機制與 Prompt 結構
型態偵測： 解析器自動識別副檔名與內容特徵（CSV 逗號分行、JSON 陣列、或混亂文字）。
LLM 語意映射： 若偵測到欄位名稱不合標準（例如，將 recall_date 寫成 date_of_issue，或 UDI 遺失部分前導零），系統會調用 Gemini，傳送以下結構化 Prompt：
code
Code
SYSTEM: You are the Aura-7 Structural Data Normalizer. Your job is to transform messy, unstandardized medical device data into a pristine JSON array that strictly matches the target schema.

Target Schema Fields:
- title (string)
- recall_date (string, format: YYYY-MM-DD)
- device_name (string)
- tfda_classification (string: '1', '2', '3')
- fda_regulation (string, e.g., '21 CFR 870.3610')
- fda_product_code (string, 3 letters uppercase)
- reason_for_recall (string)
- udi (string, normalized GS1 format)
- lot_sn (string)

Input Data to Clean:
[INSERT USER MESSY DATA]

Instructions:
1. Infer missing values if possible (e.g., if FDA Product Code is missing but Device Name is 'Impella CP', infer 'DVE').
2. Normalize all dates to 'YYYY-MM-DD'.
3. Output ONLY valid, parsable JSON matching the target schema. Do not include markdown code block syntax.
斷言校驗 (Schema Guard)： 接收到 LLM 回傳後，系統利用 JSON Schema 驗證器進行欄位完整性與格式強行檢查。通過後，將其寫入嵌入式 DuckDB 資料表。
5. 自然語言-SQL 雙向編譯沙盒與法規感知 (NLI to SQL Sandbox)
Aura-7 改變了傳統數據檢索的繁瑣過濾方式，允許用戶直接輸入自然語言（人話），並自動轉換為精準的高效能 SQL 指令，同時配備視覺化沙盒控制台與法規匹配高亮機制。
code
Code
+--------------------------------------------------------------------------------------------------+
| User inputs: "Find all Class-1 recalls in NTU Hospital containing battery issues"                 |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| AI NLI Translation (Default: gemini-3.1-flash-lite)                                              |
| Analyzes Table Schemas & Parameters                                                              |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| SQL Console Sandbox UI (User can inspect & modify code directly)                                 |
| SELECT * FROM recall_table WHERE class = 1 AND reason LIKE '%battery%' ...                       |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| DuckDB Sandbox Execution Engine                                                                  |
| Dynamic Highlight of TFDA "應建立與保存來源及流向資料之醫療器材" Articles                         |
+--------------------------------------------------------------------------------------------------+
5.1 NLI-SQL 翻譯核心與 Prompt 設計
當用戶在自然語言搜尋列輸入：「幫我找出 2025 年之後，台北榮總所有涉及電池失效的 Class-3 管制醫材召回紀錄。」
系統會自動將系統的 Table Schema 以及當前時空變數（如 2026-06-29）打包，調用 Gemini API：
code
Code
SYSTEM: You are a high-performance NL-to-SQL compiler for the Aura-7 Medical Database.
We run on an in-memory SQL database containing the following table:

Table: compliance_mega_table
Columns:
- udi (VARCHAR, Primary Key)
- title (VARCHAR)
- recall_date (DATE)
- device_name (VARCHAR)
- tfda_classification (VARCHAR, e.g., '1', '2', '3')
- fda_product_code (VARCHAR)
- reason_for_recall (VARCHAR)
- hospital_name (VARCHAR, e.g., '台北榮民總醫院', '國立臺灣大學醫學院附設醫院')
- stock_count (INTEGER)

User Query: [USER QUERY HERE]
Current Date: 2026-06-29

Task:
Convert the user query into a valid SQL query.
Return JSON format:
{
  "sql": "SELECT ...",
  "explanation": "Brief reasoning for this query structure in Traditional Chinese"
}
5.2 互動式 SQL 控制台 (The SQL Editor Sandbox)
為確保安全與可控，系統不會在後台直接執行生成的 SQL。
程式碼鏡像編輯器 (Monaco-like SQL Console)： 系統會在前端彈出一個精緻的半透明玻璃卡片控制台，展示生成的 SQL 代碼。
即時微調： 合規官可以直接在編輯器中修改 SQL 語意（例如，將 LIKE '%battery%' 手動修改為 LIKE '%lithium%'），隨後點擊 「執行安全查詢 (Execute Core)」。
5.3 TFDA 追蹤清單交叉感知高亮 (Regulatory Flow Matcher)
當 SQL 結果集返回至「合規追蹤網格 (Compliance Tracking Grid)」時，系統的法規判定引擎會即時進行交叉比對。
法規庫對應： 檢索結果中，若產品名稱或分類代碼（如 E.3610 植入式心律器之脈搏產生器、E.0001 心血管支架、M.3600 人工水晶體）命中了台灣 TFDA 所公告之 「應建立與保存來源及流向資料之醫療器材」 202 項管制目錄：
金色發光特效 (Golden Glow Highlight)：
該資料行會被賦予特殊的 CSS 屬性，在 Tailwind 中觸發：shadow-[0_0_15px_rgba(234,179,8,0.45)] 與邊框 border-l-4 border-l-yellow-500。
該行會高亮顯示一個帶有脈衝動畫的專屬勳章：「🚨 TFDA 流向管制器」，強烈警示稽核官必須立刻登載其流向發票、批號、與患者手術編碼。
5.4 召回結果巨量文本之 AI 深度摘要 (1000-2000字 Markdown)
若檢索結果命中了數十筆甚至上百筆召回紀錄，系統會自動在下方生成一個可折疊的優雅 Markdown 摘要視窗。由預設的 gemini-3.1-flash-lite 模型在 2 秒內彙整出一份 1500 字左右的深度報告：
報告大綱：
檢索結果總體態勢 (Overview)： 本次 SQL 命中的召回設備統計、管制比例、以及涉及的台灣代理商分佈。
核心失效因果鏈 (Root Cause Clustering)： AI 自動將 reason_for_recall 進行分類，歸納出是屬於「電路板氧化」、「包裝破損導致無菌性流失」還是「晶片韌體溢位」。
台灣臨床風險評估 (TFDA Flow Impact)： 針對高亮列出的管制醫材，分析目前庫存中受影響件數，並給出危害等級。
合規防範與緊急處置指令 (Actionable Directives)： 給出一線醫護人員與稽核官的標準隔離（Quarantine）與退港（Recall implementation）步驟。
6. 六大 Wow 互動圖表與合規看板 (The 6 Wow Graphs)
為展現極致的視覺衝擊，Aura-7 設計了六個高度連動、具備微交互和懸停特效的專業數據視覺化組件。
code
Code
+--------------------------------------------------------------------------------------------------+
|                                  THE 6 WOW GRAPHS METRIC GRID                                    |
|                                                                                                  |
|  [Graph 1: GIS Geodesic Map]          [Graph 2: Force-Directed Network]   [Graph 3: Sankey Flow] |
|  - WGS-84 Geodesic Vectors            - Parent-child dealer node clusters  - Supply-loss tracking|
|  - active pulse glowing dots          - Repulsion collision physics       - Interactive flow bars|
|                                                                                                  |
|  [Graph 4: Temporal Compliance]       [Graph 5: Anomaly Scatterplot]      [Graph 6: Waterfall]   |
|  - glassmorphism radar poly           - Temporal play bubble chart        - Step-by-step loss    |
|  - multi-parameter compliance vector  - Scale-to-financial impact dot     - Pipeline bottlenecks |
+--------------------------------------------------------------------------------------------------+
Graph 1：GIS 3D 空間地理流向與預測性風險熱圖 (Geospatial Distribution & Risk Heatmap)
原理： 採用高精度 SVG 繪製台灣主要縣市行政邊界。
流向向量線 (Geodesic Vectors)： 物流倉儲發貨點（如桃園航空自貿區）到各大醫學中心（如台大醫院、台北榮總、高雄長庚）之間，繪製高對比的二次貝茲曲線。
Wow 視覺特效：
線條上帶有沿著路徑滑動的發光光點（流光特效，利用 CSS stroke-dasharray 進行無限循環動畫）。
若某條供應鏈路線中存在「召回批次」或「過期警告件」，線條將轉為高頻率呼吸閃爍的「警示紅」，並在受影響的醫院節點擴散多層半透明的漣漪圈。
支援滑鼠懸停 (Hover)，即時彈出帶有玻璃磨砂背景的懸浮卡片，顯示該院庫存的合規評分與未核銷件數。
Graph 2：供應鏈拓撲網絡圖 (Distribution Network Graph)
原理： 展現特定醫材從進口總代理、一級經銷商、二級通路、直到各分院與臨床科室的樹狀或網狀關聯。
Wow 視覺特效：
節點具備力導向 (Force-Directed) 的物理排斥與碰撞反彈動畫，用戶可以任意拖拽某個節點，整個拓撲結構會像果凍般流暢地重組回彈。
雙擊節點可向下探查 (Drill-down) 該經銷商名下的所有 QSD 核備編號與出庫詳情。
被波及的缺陷節點外圍會被施加「橙色發光光暈」，極具視覺張力。
Graph 3：法規審查損耗桑基圖 (Compliance Loss Sankey Diagram)
原理： 追蹤特定批次醫材在「海關抽驗 -> TFDA 許可驗證 -> 代理商貼標 -> 醫院驗收 -> 手術臨床使用」這五個關卡中的流向耗損與扣留阻滯。
Wow 視覺特效：
寬窄不同的半透明漸變色流（Gradient Links）緩慢流動。
當點擊某個特定的審查節點（如：TFDA 許可驗證），該節點流向後續的管道會瞬間高亮，並以動態百分比展示合規扣留原因。
Graph 4：多參數合規時序雷達圖 (Temporal Compliance Radar Chart)
原理： 綜合評估特定品牌或特定醫院在「時效合規（是否過期）」、「標籤完整性（UDI 綁定）」、「申報延遲度（Lag Days）」、「召回響應速度」與「QMS 核備狀態」這五個維度的實時雷達多維畫布。
Wow 視覺特效：
多個對比區域重疊，填充色採用帶有玻璃擬態 (Glassmorphism) 反光的半透明漸變，邊緣以發光高亮描邊。
當數據動態更新時，雷達網格的各個角頂點會伴隨彈性阻尼動畫（Spring Physics）滑暢移位。
Graph 5：UDI 批次異常分佈散點圖 (UDI Batch Anomaly Scatterplot)
原理： X 軸為入庫時間，Y 軸為設備批次存活率，點的大小代表該批次的總採購金額，顏色深淺代表合規風險值。
Wow 視覺特效：
整合「時間軸播放器 (Temporal Playback Controls)」。點擊播放，畫面上的散點會隨著近三年的歷史進程，呈動態軌跡在坐標軸上滑行、分裂或縮小，重現異常批次隨時間演進的動態擴散。
Graph 6：現場稽核標準工作流瀑布圖 (Regulatory Audit Waterfall Chart)
原理： 梯級展示稽核官從發起調查、查核證件、現場庫存核對、AI Note 萃取到最終告誡發文的進度狀態與累積計數。
Wow 視覺特效：
每個立柱區塊在加載時採用 staggered (交錯延遲) 的由下而上彈跳展開動畫。
最終結算柱會根據當前合規狀態，動態渲染為合規綠或警示紅，並帶有微小的霓虹掃描線。
7. LLM 執行視覺化、互動指示器與隨行日誌 (Execution Visuals & Live Log)
為了建立用戶在使用 AI 時的「掌控感」與「極致互動體驗」，Aura-7 設計了全套 LLM 執行視覺化組件。
7.1 執行「Wow」視覺化效果與 token 脈衝
當用戶按下「執行查詢」或「解析文獻」時，系統會啟動以下動畫：
神經纖維流光 (Neural Pathways Glow)：
控制塔（控制台側邊欄）與主工作區（Dashboard）之間的隱形連接線會瞬間亮起。
多組高亮點（模擬 Embedding Vectors）以極快速度沿著邊界跑動，象徵數據正在上送至 Gemini 雲端。
文本生成波紋 (Dynamic Typing Wave)：
Markdown 摘要生成時，文字不是死板地瞬間出現，而是伴隨微小的「打字機流式特效 (Streaming Output)」，且新輸出的字元會帶有一層短暫的藍色發光濾鏡 (fade-out blur glow)，提供如同大腦思考般的流體動態。
7.2 互動指示器 (Wow Overlay Interaction Indicator)
在畫面右上角設有一個常駐的**「神經突觸交互指示器 (Synapse Pulse Overlay)」**。
靜態： 呈現半透明的磨砂玻璃圓環，內含一個微小的、帶著微弱藍光的圓核。
AI 執行中： 圓環內部會出現三層同心圓環以相反方向旋轉，並伴隨高頻的、呼應 LLM 輸出速率的「金色脈衝粒子」向外擴散，視覺效果極具科技感。
7.3 隨行終端日誌 (Live Stream Log Console)
在畫面右下角內嵌一個高度仿真的**「合規日誌終端 (Log Console)」**：
外觀： 黑色半透明背景 (bg-black/60 backdrop-blur-md)，配以明亮綠色與靛藍色等寬字型（font-mono text-[10px]）。
功能：
即時印出系統內部的數據庫查詢與 AI 調用軌跡。例如：
code
Code
[08:12:01] [SYS] Active connection to TFDA Node established.
[08:12:02] [NLI] Compiling natural query: "Find recalls..." -> SQL Core
[08:12:03] [SQL] DuckDB executed SELECT * FROM compliances WHERE Class='3'...
[08:12:04] [LAW] Highlighting E.3610 Pacemaker - TFDA Article 23 matched!
[08:12:05] [GEM] LLM Stream open: receiving 1,500 words summary.
[08:12:06] [SUC] Wow HTML package serialized successfully. [622 KB]
日誌行會自動向上捲動，新行進入時會伴隨 100ms 的淡入與左側彈入微動畫，使稽核官在視覺上能即時感知系統的背景作業。
8. 三大全新「驚艷」AI 擴展功能設計 (Additional Wow Features)
為使 Aura-7 成為市場上無可比擬的領先方案，系統特別實作了以下三項前瞻性的 AI 核心功能：
code
Code
+--------------------------------------------------------------------------------------------------+
|                                    THREE ADDITIONAL WOW AI MODULES                               |
|                                                                                                  |
|   1️⃣ PREDICTIVE RISK HEATMAP         2️⃣ FUZZY RECONCILIATION AGENT     3️⃣ VOICE CO-PILOT          |
|   - Multi-parameter forecast        - Fuzzy semantic alignment        - Web Audio API Capture    |
|   - Expiry & recall vector aging    - Anti-collision correction       - Speech-to-SQL compile    |
|   - Glowing hazard hot zones        - One-click auto-healing popup    - Fluid TTS summary voice  |
+--------------------------------------------------------------------------------------------------+
1️⃣ AI 驅動的預測性合規風險熱圖 (Predictive Risk Heatmap Engine)
背景： 傳統系統僅能展示「已經過期」或「已經被召回」的醫材。
技術原理：
本功能旨在進行「未來合規風險預測」。
後端預測代理人定期調用 Gemini，綜合分析特定高風險醫材的**「製造批次妥善率趨勢」、「該批次在台灣各院所的平均積壓天數（Inventory Velocity）」、以及「該醫材無菌包裝退化物理 Kinetics」**（模擬高溫、濕度老化 kinetics，簡化公式為 
）。
Wow 體驗：
系統會計算出未來 30 至 90 天內，全台最可能因為「滅菌期限集體到期」、「連續批次失效」而引發召回危機的醫療機構或經銷商據點。
在 GIS 地圖上，這些高風險區域會以動態的、具備立體發光光環（Glowing Aura）的橙紅色熱點進行預警，讓合規官得在危機爆發前調度安全批次。
2️⃣ 自主法規對帳與糾錯代理人 (Autonomous Regulatory Reconciliation Agent)
背景： 發貨商的報表與醫院點收報表時常因為人工打字、掃描槍截斷產生不一致（如，出庫單為 LOT-B8329-X，醫院打字輸入為 LOT-88329-X，英文字母 B 與數字 8 產生混淆），導致系統誤報為「出庫未登（Unreported）」或「幽靈帳籍（Ghost Stock）」。
技術原理：
AI 代理人在後台靜默運行，自動對未對齊的帳籍進行 Fuzzy（模糊語意）與字元距離（Levenshtein Distance）相似度計算。
結合歷史上人工輸入最易出錯的「字元混淆特徵矩陣」（如 O 與 0, I 與 1, B 與 8）。
Wow 體驗：
發現異常時，系統不會生硬地報錯，而是在合規網格最上方彈出一個精美的提示框：「合規官，我發現供應鏈中有一個 96% 機率的登錄誤差。台大醫院登錄的幽靈序號 LOT-88329-X 與美敦力出庫單上的 LOT-B8329-X 語意高度吻合，疑似為 8 與 B 混淆。已為您擬定一鍵修正腳本，是否執行數據自癒？」
3️⃣ 語音互動式合規協同助理 (Voice-Activated Compliance Co-Pilot)
背景： 專為手術室盤點、無菌物流倉儲、或合規官實地稽核時「雙手不便操作鍵盤」的極端場景設計。
技術原理：
前端整合 Web Audio API 擷取用戶語音，傳送至 Gemini 的語音多模態介面（Voice/Audio Mode）。
系統在後端完成語意理解、翻譯為 SQL 語句、執行查詢、並將結果包裝。
Wow 體驗：
用戶按下空白鍵或點擊麥克風說：「Aura，幫我調出上個月台北榮總所有關於心血管支架的異常日誌，並把圖表切換到 GIS 地圖模式。」
系統會在 500 毫秒內，自動重新過濾數據，伴隨流暢的 Framer Motion 動畫，將儀表板無縫切換到指定視圖。
同時，Co-Pilot 會透過高品質的語音合成 (TTS) 向用戶回報：「已為您切換至台北榮總地圖，上月共有 2 筆 Class-3 支架召回警報，批號均已在途中隔離完畢。」
9. FDA 召回文獻結構化萃取與生成模組 (Recall Document Extractor)
本模組提供了一個「非結構化醫療監管公文」至「系統核心數據庫標準格式」的無縫轉換橋樑。
code
Code
+--------------------------------------------------------------------------------------------------+
| Raw FDA Regulatory Alert text pasted by user (TXT, Markdown, or PDF OCR)                          |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| AI Extraction Pipeline (Gemini Named Entity Recognition - NER)                                   |
| Maps variables: Title, Date, Regulation, UDI, Lot numbers...                                      |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| Validation Check: Structural JSON Schema Compliance Gate                                         |
| Sanitizes strings & secures data points                                                          |
+------------------------------------------------+-------------------------------------------------+
                                                 |
                                                 v
+--------------------------------------------------------------------------------------------------+
| Output Options: Download Standard JSON | Write to Database Grid | Create Wow HTML Export       |
+------------------------------------------------+-------------------------------------------------+
9.1 原始 FDA 文獻解析管線 (NER Pipeline)
輸入端： 用戶可以自由將美國 FDA 發布的英文 PDF 公告、各國監管機構的混亂 TXT 通告貼入系統。
多模態解析鏈： Gemini 執行命名實體識別 (NER)，從上萬字的文章中精確抓取目標欄位。
對標對位：
將英文日期（如 "June 25th, 2026"）自動轉為標準 2026-06-25。
從段落中提取 Regulation 條號（如 21 CFR 870.3610）與 Product Code（如 DVE）。
鎖定 UDI 基本碼與 lot_sn 大範圍（如 Affected Batch Number: 2041530）。
9.2 數據修改、儲存與導出網關 (Universal Export Gateway)
就地編輯 (In-place Grid Modification)： 萃取出來的標準 JSON 資料會渲染在一個微型編輯網格中，用戶可點擊任意儲存格直接修改內容。
安全備份下載 (Secure JSON Export)： 點擊「導出標準數據」，可將資料下載為標準的 fda_recall_standardized.json。
Wow HTML 封裝與多格式匯出：
用戶可點擊「匯出全效能工作區」按鈕，系統後端會動態打包當前的查詢結果，生成一個單一檔案的 Wow HTML。該 HTML 檔案內建獨立的 Tailwind CSS 樣式表、輕量級 Recharts 渲染腳本以及當前資料的加密 JSON 孤島。用戶將此 HTML 下載後，在完全離線的環境下開啟，依舊能保持全動態的圖表交互與懸停特效。
此外，互動介面也整合了客戶端網關，支援一鍵轉換並下載：JSON 原始圖譜、高清晰度 PDF 報告（內含圖表截圖）、標準 Markdown 文件、以及獨立的純文字 HTML。
10. 防禦性工程設計與潛在漏洞修正日誌 (Defensive Engineering)
為了達到企業級系統在 Cloud Run 與複雜網路環境下的絕對穩定，Aura-7 實作了全面的防禦性編程：
10.1 防止 LLM 幻覺與結構破壞
潛在漏洞： 大語言模型在處理非結構化數據時，可能偶發性回傳帶有 Markdown 標記（如 ```json）的無效字串，或者自行發明 Schema 以外的欄位，導致前端 JSON.parse 報錯或表格斷裂。
防禦實作： 后端 API 路由在調用 Gemini 時，強制宣告 Response MimeType: "application/json"，並在代碼中施加**「JSON 淨化過濾器 (Sanitization Layer)」**：
code
TypeScript
function sanitizeJsonResponse(rawText: string): string {
  return rawText
    .replace(/```json/gi, '')
    .replace(/```/g, '')
    .trim();
}
斷言重試機制： 若解析出的 JSON 缺少關鍵必填欄位（如 udi 或 tfda_classification），系統會自動向 Gemini 發起二次微小修正請求，確保最終交付給前端的數據絕對合規。
10.2 記憶體洩漏與音訊流釋放 (Memory Leakage Prevention)
潛在漏洞： 語音協同助理在持續監聽 Web Audio 流時，若用戶頻繁在不同分頁、不同視圖切換，未被完全釋放的 AudioContext 會在瀏覽器內存中堆疊，導致 CPU 佔用持續飆升，造成頁面卡頓甚至「白屏」。
防禦實作：
在語音和 Canvas 圖表的 React 生命週期中，嚴格設置 cleanup 函數。
在組件卸載 (Unmount) 時，強制調用 audioContext.close()，並清空所有的 ResizeObserver 與定時器，徹底釋放硬體資源。
10.3 CSV 與 HTML 注入攻擊防禦 (Anti-Injection Gateway)
潛在漏洞： 恶意用戶可能在上傳的異質召回數據中，夾帶公式字串（例如在原因欄位填入 =cmd|' /C calc'!A1），當稽核官將這些資料匯出為 CSV 並在 Excel 中開啟時，會觸發 CSV 注入攻擊。
防禦實作：
在 CSV 生成器中，對所有儲存格進行安全性前綴檢測。若檢測到字串開頭為 =, +, -, @，一律在前方強行加上單引號 ' 進行轉義，消除執行代碼的可能性。
在將融合寬表寫入 Wow HTML 的數據孤島前，對所有文字執行 HTML 實體編碼 (Entity Encoding)，將 < 轉為 &lt;，> 轉為 &gt;，徹底封殺代碼執行空間。
11. 20 個全面性後續技術與法規架構思考問題 (20 Follow-up Questions)
為了確保 Aura-7 醫材合規追蹤平台在後續的大規模落地、壓力測試與日常維運中保持絕對的領先地位與系統高可用性，請團隊深入評估並討論以下 20 個全面性的核心技術與法規架構命題：
【第一部分：TFDA 國家法規與合規執行政策】
管制醫材覆蓋率： 我國現行《醫療器材管理法》中，對於哪些等級之植入式醫療器材，強制要求發貨商實施如同 Aura-7 系統中的全鏈主動流向登載通報？其申報週期與頻率法定限制為何？
走私/水貨查防： 若 Aura-7 在 ledger 中查出「幽靈帳籍 (Ghost Stock)」事件，疑似涉及境外非法走私或俗稱「水貨」的平行輸入。如何聯合內政部警政署刑事警察局進行實體帳簿追蹤、查扣、以及落實涉案人員的刑事起訴工作流？
警告期效： 對於未能依法在 Aura-7 中準確維護「DHA 監控據點立案地址」的受監管醫療機構或發貨經銷商，食藥署在發放行政警告 letter 前，法定的「限期改正期限」最長不應超過多少個工作天？
物資轉撥法源： Aura-7 計算出的「到期重分配方案（Expiry Optimization Playbook）」若涉及不同法人醫療集團（例如私立長庚體系調撥至公立台大體系）之間的庫存轉移。這在現行醫材特約、藥價核退、以及醫院採購合約法規上，需要哪些特定的法律豁免或特別配套？
AI 裁決法律效力： 當本系統的「爭端調解代理（Dispute Resolutor）」自動生成一份裁決鑑定判定書時。該 AI 產出的文書在與行政訴訟法或民事訴訟對接時，其是否具備「鑑定報告」或「行政裁量參照證據」之法定效力？
【第二部分：WGS-84 空間地理測地方位與物流鏈】
天災避險路線： Aura-7 的 WGS-84 地圖中，如何針對台灣極端天然災害（如東部路網震災崩落、強烈颱風等）導致的偏鄉長途醫療物流中斷，動態匯入中央氣象署的即時路網狀態、並在幾秒之內即時重繪受災區醫療站（DHA Hubs）的在途物資警報？
離島特殊係數： 考慮到外島地區（金門醫院、澎湖醫院等）與本島的航運受限性。Aura-7 風險路徑分析模組（Route Risk Analyzer）中，應引入哪些額外的海空運氣候等候期變數，以優化外島緊急植入用醫材的退化與效期衰變率？
全程冷鏈 IoT 整合： 對於有極精密「全程冷鏈 (Cold Chain)」溫濕度監測需求的高風險活性重構性醫材。DHA 據點（DHA Stations）通訊協議，應如何整合物聯網（IoT）藍牙/NB-IoT 監測技術，將實時溫度讀數直接寫入 active ledger 以達成動態監控之目的？
地理圍欄回算： 在 DHA 站點批次上傳（CSV/JSON Workspace）中，當上傳經緯度精度丟失（如誤將經度填寫為緯度，使坐標落在台灣海峽或非本島區域）時。Aura-7 前端地圖元件應如何實施自動化地理圍欄（Geofencing）安全警報回算？
室內三維定位： 如何結合 5G 微型定位和室內 UWB（超寬頻）技術，將 Aura-7 空中投影圖，無縫延伸到洗腎室、心導管室內部的「智慧醫療資產櫃級定位」，使官員坐在辦公室即可追蹤特定滅菌包在受檢醫院內部的實際擺放格位？
【第三部分：WOW AI 神經引擎、知識庫、與 Gemini 模型優化】
RAG 實時同步與幻覺控制： 當使用 gemini-3.1-flash-lite 作為預設神經模型進行「TFDA 法規智慧諮詢（Legal Assistant）」時。系統如何落實 RAG（檢索增強生成）機制的最新法規文本庫即時同步，防範大語言模型對我國行政罰鍰天數與裁量標準產生「幻覺（Hallucination）」？
高併發 Token 與 Rate Limit： 若稽核官員改為調用 gemini-2.5-pro 模型。其在處理數萬筆的大批量帳籍時，Token 處理上限與推理成本（Latency Ms）會如何變遷，後端 Express 中繼 API 是否具備請求速率限制（Rate Limiting）以防止 API key 被過載擊穿？
異常演算法權重： 當「神經網絡帳籍漏洞獵手（Anomaly Hunter）」在計算 Aura-7 綜合合規評分時，其背後的權重矩陣（Weights Matrix）是如何設計的？例如：一筆「Ghost 幽靈異常」與一筆「滅菌即將到期（Warning）」相較，其扣分權重比例應如何隨法規嚴厲程度自動調整？
國際條碼擴展性： Aura-7 現行的 GS1 UDI 條碼編譯及 ISO 規格合成器（Barcode Composer）。如何應對未來歐盟（MDR）和美國 FDA 對於新型超長動態變量 PI 條碼格式的相容與規格擴展？
患者隱私去識別化管線： 為了徹底保障病人隱私。在將帳籍紀錄上送給 Gemini 神經網絡之前，Aura-7 原生在 server.ts 施加了何種程度的資料脫敏與匿名化加密管道（Sanitized Redaction Pipelines），確保不慎遭截獲時絕不會洩露病人或主治醫師的敏感姓名與個人病歷資料？
【第四部分：極致前端性能、色彩治理與系統擴展】
WebGL 渲染下沉： 當 DHA 全台站點突破上萬個（例如加入全台所有連鎖診所與西藥售賣店）時。Aura-7 的 WGS-84 地圖圖層應如何引入 canvas 分層渲染或 WebGL 集群技術，以避免前端瀏覽器出現渲染崩潰遲阻？
WCAG 無障礙對比： 系統提供的 10 大潘通（Pantone Styles）色彩樣式，是否完全符合 WCAG 2.1 國際無障礙網頁色彩對比度標準（例如特定按鈕文字與漸層背景之對比度至少達 4.5:1），確保視覺障礙官員在使用「蘭花紫」或「亮麗黃」主題時仍有完美的字元辨識度？
離線快取機制 (PWA)： Aura-7 是否內嵌了「離線運作快取（PWA / Local Storage Cache）機制」，讓稽核官員在進入無 4G/5G 訊號的偏遠地下冷庫、屏蔽力極強的心導管室或大型鋼骨倉儲中心時，即便完全離線仍能操作站點變更，並在連上網路後瞬間執行對帳同步？
CSS 打印對齊： 當稽核官員需要印製紙本或匯出 PDF 檔案時。系統如何確保 Note Keeper 生成的 Markdown 合規公文及 WGS-84 地圖能在 CSS @media print 下轉換為無瑕疵的 A4 標準尺寸、高對比單色印製版面，不遺失邊界及重要表格資訊？
區塊鏈不對稱存證： 未來 Aura-7 系統應如何整合區塊鏈（Blockchain）分布式不可篡改帳本，將進口代理商 Medtronic 的出貨電子發票 hash 與醫院入庫掃描簽收憑證，作為無懈可擊的數位戳記錨定在 active tracking 中，完全消除偽造、篡改或黑市操作的可能性？
12. 總結與演進規劃 (Roadmap)
Aura-7 v4.0.0 企業級平台完美融合了 Frosted Glass (磨砂玻璃) 視覺語彙，在為食品藥物管理署 (TFDA) 與臨床管理人員提供強烈視覺震撼力的同時，兼具了高度的可操作性與嚴謹的法規防禦性。系統在保持輕量化、純 React + Express 運作的同時，為未來的「去中心化區塊鏈流向存證」、「WebXR AR 智慧盤點」與「全球跨區域法規矩陣」預留了無縫擴展的管道。本規格書詳盡編制完備，將指引 Aura-7 邁向更高度、全天候的主動式合規時代！
