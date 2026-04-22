# Clustering-Based Big Data Analysis of Web Crawler Opt-Out Strategies: A Scientific Approach to Robots.txt Governance

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Conference](https://img.shields.io/badge/ICBDA-2026-orange.svg)
![Location](https://img.shields.io/badge/Presentation-Waseda_University-red.svg)

本專案為發表於 ICBDA 2026 (第 11 屆大數據分析國際會議) 之研究實作。研究運用科學的大數據分析方法，量化評估全球頂尖網站針對網路爬蟲的治理現狀與防禦趨勢。

## 研究摘要 (Abstract)
大型語言模型 (LLM) 極度依賴大規模網頁數據，然而網站主權意識抬頭。本研究以 2024 BEDC 全球前百大網站為樣本，獲取 98 份有效 `robots.txt` 檔案，透過 K-means 聚類 與 主成分分析 (PCA) 識別出三種主要的治理模式：
1. 全面拒絕型 (Full Opt-out)
2. AI 特定阻斷型 (Partial AI-targeted Opt-out)
3. 限速存取型 (Rate-limited Access)

研究發現 61.2% 的採樣網站已實施至少一項針對 AI 爬蟲的限制指令，顯示開放網頁數據空間正在實質收縮。

---

## 技術實作 (Methodology)

### 1. 數據採集與特徵工程
* 自動化採集：使用 Request 腳本，精準獲取2024 Top 100 網站之治理規則。
* 向量化處理：將非結構化的 `robots.txt` 指令轉化為數值特徵，包含「指令強度」、「Agent 涵蓋率」及「路徑深度」。

### 2. 機器學習模型應用
* K-means 聚類分析：透過手肘法 (Elbow Method) 確定最佳群數 $K=3$，將不同產業的治理策略進行分類。
* 主成分分析 (PCA)：將多維特徵縮減至「阻斷強度」與「模式差異化」兩個核心維度，解釋了 41.9% 的數據變異。


---

## 🎓 發表紀錄與引用 (Publication & Citation)
本研究由 鄭博仁 (Bo-Ren Cheng) 於 2026 年 4 月在日本東京 早稻田大學 (Waseda University) 進行口頭發表。

```text
Cheng, B. R., & Cheng, C. Y. (2026). Clustering-Based Big Data Analysis of Web Crawler Opt-Out Strategies: A Scientific Approach to Robots.txt Governance. In Proceedings of the 11th International Conference on Big Data Analytics (ICBDA 2026).


我想要結合這些內容:

## 📘 1. Data Collection
File: `data_collection/robots_txt_results_FINAL.xlsx`

- 98 valid robots.txt files from the BEDC Top-100 global websites (2024)
- Parsed into 8 structured features:
  - `ai_block_count`
  - `blocks_search_engines`
  - `global_disallow_root`
  - `disallow_scope_ratio`
  - `crawl_delay_norm`
  - `ai_only_block`
  - `wildcard_usage`
  - `sitemap_present`

---

## 🧮 2. Clustering Results
Folder: `clustering_results/`

Contains three CSV files representing the websites in each opt-out strategy:

| File | Cluster Label | Description |
|------|----------------|-------------|
| `websites_full-opt-out.csv` | A | Full Opt-out (comprehensive blocking) |
| `websites_partial-opt-out-ai-targeted.csv` | B | Partial Opt-out: AI-targeted |
| `websites_partial-opt-out-rate-limited.csv` | C | Partial Opt-out: Rate-limited |

---

## 📊 3. Analysis Summary
File: `analysis_summary/summary_all_features_with_smd.csv`

- Summarizes feature statistics (mean, SD, SMD) across clusters.

---

## 🧾 Citation
If you use this dataset, please cite:

> Cheng, B.-R., & Cheng, C.-Y. . *Robots.txt opt-out dataset (BEDC Top-100, 2024)* [Data set]. GitHub. [https://github.com/yourname/robots-optout-dataset](https://github.com/Raycheng0629/robots_txt-optout-dataset)

-
