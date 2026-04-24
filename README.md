# Clustering-Based Big Data Analysis of Web Crawler Opt-Out Strategies: A Scientific Approach to Robots.txt Governance

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Conference](https://img.shields.io/badge/ICBDA-2026-orange.svg)
![Location](https://img.shields.io/badge/Presentation-Waseda_University-red.svg)

本專案為發表於 ICBDA 2026 (第 11 屆大數據分析國際會議) 之研究實作。研究運用科學的大數據分析方法，量化評估全球頂尖網站針對網路爬蟲的治理現狀與防禦趨勢。

### 數據採集與特徵工程
**數據路徑**: `data_collection/robots_txt_results_FINAL.xlsx`

我們從 2024 BEDC 全球前百大網站中成功解析出 98 份有效樣本，並將非結構化的規則轉化為 **8 項結構化特徵**：
* **`ai_block_count`**: 針對 AI 爬蟲的阻斷指令數量。
* **`blocks_search_engines`**: 是否限制傳統搜尋引擎。
* **`global_disallow_root`**: 是否設置全域根目錄阻斷 (`Disallow: /`)。
* **`disallow_scope_ratio`**: 阻斷路徑佔整體宣告規則的比例。
* **`crawl_delay_norm`**: 爬取延遲時間 (Crawl-delay) 之標準化數值。
* **`ai_only_block`**: 是否僅精準針對 AI 爬蟲進行阻斷。
* **`wildcard_usage`**: 通配符 (`*`, `$`) 在規則中的使用頻率。
* **`sitemap_present`**: 檔案中是否包含 Sitemap 宣告。

###  聚類分析 
透過手肘法 (Elbow Method) 確定最佳群數 $K=3$，將網站歸納為三種治理策略：

| 檔案名稱 | 聚類標籤 | 策略描述 |
| :--- | :--- | :--- |
| `websites_full-opt-out.csv` | **Cluster A** | **全面拒絕型**: 採行最嚴格的全面阻斷規則。 |
| `websites_partial-opt-out-ai-targeted.csv` | **Cluster B** | **AI 特定阻斷型**: 精準針對 AI 爬蟲進行限制。 |
| `websites_partial-opt-out-rate-limited.csv` | **Cluster C** | **限速存取型**: 透過延遲或部分限制維持平衡。 |

###  維度縮減 
**分析摘要**: `analysis_summary/summary_all_features_with_smd.csv`
* **PCA 分析**: 成功將多維特徵縮減至兩個核心維度（阻斷強度與模式差異化），解釋了 **41.9%** 的數據變異。
* **統計驗證**: 提供各聚類特徵的平均值、標準差與標準化平均差異 (SMD)，驗證聚類結果的科學顯著性。

---
* **相關文件**: [研討會參與證明](研討會_參與證明.jpg)
* **研討會論文**: [Clustering-Based Big Data Analysis of Web Crawler Opt-Out Strategies: A Scientific Approach to Robots.txt Governance](研討會_論文.pdf)


## 發表紀錄與引用
本研究由 鄭博仁 (Bo-Ren Cheng) 於 2026 年 4 月在日本東京 早稻田大學 (Waseda University) 進行口頭發表。


## 儲存庫結構
```text
/
├── data_collection/
│   └── robots_txt_results_FINAL.xlsx    # 原始 98 份網站特徵向量
├── clustering_results/                  # 聚類分組名單
│   ├── websites_full-opt-out.csv
│   ├── websites_partial-opt-out-ai-targeted.csv
│   └── websites_partial-opt-out-rate-limited.csv
├── analysis_summary/                    # 統計分析摘要 (SMD)
│   └── summary_all_features_with_smd.csv
├── src/                                 # K-means 與 PCA 實作腳本
├── docs/                                # 論文 PDF 與發表簡報
└── README.md
