# azure-az104-study

![AZ-104](https://img.shields.io/badge/Azure-AZ--104-0078D4?logo=microsoftazure&logoColor=white)
![問題数](https://img.shields.io/badge/問題数-100問-blue)
![Vanilla JS](https://img.shields.io/badge/JS-Vanilla-F7DF1E?logo=javascript&logoColor=black)
![No build](https://img.shields.io/badge/build-none-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

Azure Administrator (AZ-104) の試験対策用 Web アプリです。  
問題演習・詳細解説・サービス比較表・参考書をブラウザだけで完結させます。

---

## 📋 コンテンツ概要

### 問題演習 (`index.html`)

| 分野 | 問題数 | カバーするトピック |
|---|---|---|
| ネットワーク | 25問 | VNet・NSG・VPN・DNS・Private Endpoint・Firewall・Load Balancer・Bastion |
| ID管理 | 20問 | 条件付きアクセス・RBAC・PIM・Managed Identity・B2B・SSPR・Identity Protection |
| コンピューティング | 20問 | VM可用性・App Service・AKS・ACI・Azure Functions・VMSS・Update Manager |
| ストレージ | 15問 | Blob・Files・Disk・冗長性（LRS/ZRS/GRS）・CDN・Soft Delete・SAS |
| 監視 | 12問 | Azure Monitor・Log Analytics・KQL・Application Insights・Microsoft Sentinel |
| バックアップ | 8問 | Azure Backup・Site Recovery・PITR・Soft Delete・保持ポリシー |
| **合計** | **100問** | Easy 9問 / Medium 57問 / Hard 34問 |

各問題には **正解の理由・落とし穴・サービス比較表・キーワード** が付いています。

### 参考書 (`study.html`)

| セクション | 内容 |
|---|---|
| チートシート | 各分野のサービスを要点カード形式でまとめ |
| サービス比較表 | LRS/ZRS/GRS・App Service vs ACI vs AKS・LB vs AG vs Front Door など |
| 分野別ポイント | 試験で狙われるポイントと落とし穴を分野ごとに整理 |

---

## ✨ Features

- **深掘り解説** — 正解の理由 + よくある落とし穴を毎問表示
- **サービス比較表** — 類似サービスの違いを問題ごとに整理
- **分野別フィルタ** — 苦手分野だけ絞って集中練習
- **スコア追跡** — 正答率・連続正解・分野別グラフ（結果画面）
- **ビルド不要** — ブラウザで開くだけ。npm install 不要
- **ダークテーマ** — 目に優しい暗めのデザイン

> ⚠️ アイコンフォントを CDN から読み込むため、初回表示にネット接続が必要です。

---

## 🚀 Getting started

```bash
git clone https://github.com/yourname/azure-az104-study.git
cd azure-az104-study
open index.html     # macOS
# start index.html  # Windows
```

または [GitHub Pages](https://ykobayashi-jp.github.io/azure-az104-study/) でブラウザから直接アクセス。

---

## 🗂 Structure

```
azure-az104-study/
├── index.html    # 問題演習アプリ（100問収録）
├── study.html    # 参考書ページ（チートシート・比較表・ポイント整理）
└── README.md
```

問題データは `index.html` 内の `const QS = [...]` に直接記載しています。

---

## ➕ Adding questions

`index.html` 内の `const QS = [...]` に以下の形式でオブジェクトを追加してください。

```js
{
  domain: "ネットワーク",  // 下表の値を使用
  cat:    "NSG",           // バッジ表示用（自由記述）
  diff:   "Medium",        // "Easy" | "Medium" | "Hard"
  q:    "問題文...",
  opts: ["選択肢A", "選択肢B", "選択肢C", "選択肢D"],
  ans:  1,                 // 正解の選択肢インデックス（0始まり）
  why:  "正解の理由...",
  trap: "よくある落とし穴...",
  cmp: [                   // サービス比較表（省略可）
    { svc: "サービス名", feature: "特徴", rto: "RTO目安", cost: "低/中/高", note: "備考" }
  ],
  kws: ["キーワード1", "キーワード2"]
}
```

### domain に指定できる値

| 値 | カバーするトピック例 |
|---|---|
| `ネットワーク` | VNet・NSG・VPN Gateway・Azure Firewall・Private Endpoint・Bastion |
| `ID管理` | Azure AD・条件付きアクセス・RBAC・PIM・Managed Identity・B2B |
| `コンピューティング` | VM・App Service・AKS・ACI・Azure Functions・VMSS |
| `ストレージ` | Blob Storage・Azure Files・Managed Disk・冗長性・CDN |
| `監視` | Azure Monitor・Log Analytics・KQL・Application Insights・Sentinel |
| `バックアップ` | Azure Backup・Recovery Services Vault・ASR・PITR |

---

## 📄 License

MIT
