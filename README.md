# Credit Card Default Prediction

以 **Random Forest** 建立信用卡違約預測模型，使用台灣信用卡客戶資料集進行分類，目標是判斷客戶在下一期是否可能違約。

## Project Overview

這是一個以 **信用風險評估（Credit Risk Assessment）** 為主題的機器學習專案。  
我使用公開資料集，完成資料清理、特徵整理、模型訓練與結果評估，並分析哪些變數對違約預測最重要。

這個專案想回答的核心問題是：

> 能不能根據客戶的過去還款行為、信用額度與帳單資訊，提前辨識較高的違約風險？

---

## Why This Project Matters

在金融場景中，違約預測會直接影響：

- 授信決策
- 風險控管
- 客戶分級
- 資本配置效率

因此，這個題目不只是單純的分類任務，也是一個很典型的 **金融資料分析 + 機器學習應用** 案例。

---

## My Work

在這個專案中，我完成了以下內容：

- 讀取並整理原始 `.xls` 資料
- 清理欄位與標籤資料
- 建立訓練 / 測試資料集
- 使用 `RandomForestClassifier` 進行模型訓練
- 以 Accuracy、Precision、Recall、F1-score 評估模型表現
- 觀察特徵重要度（Feature Importance），分析影響違約的關鍵因素

---

## Dataset

- **Source**: UCI Machine Learning Repository  
- **Dataset**: Default of Credit Card Clients (Taiwan)  
- **Sample Size**: 約 30,000 筆資料  
- **Target Variable**: `Y`
  - `Y = 1`：下期違約
  - `Y = 0`：下期未違約

資料檔案位置：

```text
data/raw/default_of_credit_card_clients.xls
```

---

## Method

本專案使用 **Random Forest** 作為主要模型。  
Random Forest 是由多棵決策樹（Decision Tree）組成的集成模型，適合處理：

- 非線性關係
- 多變數特徵
- 特徵間交互影響

### Model Settings

- `n_estimators = 300`
- `max_depth = 12`
- `min_samples_leaf = 10`
- `class_weight = "balanced"`
- train / test split = `80 / 20`
- stratified sampling

### Data Preprocessing

程式中有做以下前處理：

- 移除不必要欄位，例如 `Unnamed: 0`、`ID`
- 將 `Y` 轉成數值型態
- 移除無法轉成數值的標籤列
- 若有非數值欄位，自動做 one-hot encoding
- 若有缺失值，以中位數補值

---

## Results

模型在測試集上的結果約為：

- **Accuracy**: `0.7580`
- **Precision**: `0.4610`
- **Recall**: `0.5561`
- **F1-score**: `0.5041`

### Interpretation

這組結果代表：

- 模型對「未違約客戶」的辨識相對穩定
- 模型已能抓到超過一半的違約客戶
- 若從風控角度來看，**Recall** 很重要，因為它代表高風險客戶有多少比例被成功識別

白話一點說：  
這個模型已經有能力先篩出一部分較可能違約的人，但還有空間繼續降低誤判、提升精準度。

---

## Key Predictors

根據特徵重要度分析，較重要的變數主要包括：

- **X6 ~ X11**：近期還款狀況
- **X1**：信用額度
- **X3**：教育程度
- **X15、X21、X23**：部分帳單金額與繳款金額相關欄位

這也符合金融直覺：

- 最近是否延遲還款，通常比很久以前的資料更能反映違約風險
- 信用額度與帳務壓力，也常和風險程度有關

---

## Tech Stack

- Python
- pandas
- scikit-learn
- openpyxl / xlrd

---

## Project Structure

```text
credit-card-default-prediction/
├── README.md
├── requirements.txt
├── data/
│   └── raw/
│       └── default_of_credit_card_clients.xls
├── docs/
│   └── report.docx
└── src/
    └── train_random_forest.py
```

---

## How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the script

```bash
python src/train_random_forest.py
```

---

## What I Learned

透過這個專案，我實際練習了：

- 如何把金融問題轉成可操作的機器學習分類任務
- 如何處理真實資料中的欄位清理與前處理
- 如何用評估指標判讀模型表現
- 如何把模型結果連回金融風險管理的情境理解

---

## Possible Improvements

後續可以繼續優化的方向包括：

- 比較 **Logistic Regression**、**XGBoost** 等模型
- 調整分類門檻（threshold）
- 加入 confusion matrix 視覺化
- 補上 feature importance 圖表
- 加入 notebook 版本，提升展示性

---

## Author

Chang Gung University, Department of Digital Finance  
Student project focused on machine learning application in credit risk prediction.
