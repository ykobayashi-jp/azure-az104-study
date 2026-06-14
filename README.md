# azure-az104-study

![Azure AZ-104](https://img.shields.io/badge/Azure-AZ--104-0078D4?logo=microsoftazure&logoColor=white)
![問題数](https://img.shields.io/badge/問題数-100問-blue)
![Vanilla JS](https://img.shields.io/badge/JS-Vanilla-F7DF1E?logo=javascript&logoColor=black)
![No build](https://img.shields.io/badge/build-none-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

Azure Administrator (AZ-104) の試験対策用 Web アプリです。  
問題演習・詳細解説・サービス比較表・チートシート・用語集をブラウザだけで完結させます。

---

## 📋 コンテンツ概要

### 問題演習 (`index.html`)

| 分野 | 問題数 | カバーするトピック |
|---|---|---|
| ID管理 | 20問 | RBAC・Managed Identity・Conditional Access・PIM・B2B・SCIM Provisioning |
| ネットワーク | 15問 | VNet Peering・NSG・Private Endpoint・Application Gateway・ExpressRoute |
| ストレージ | 20問 | Blobライフサイクル・Azure Files + File Sync・冗長性・SAS・Disk Backup |
| コンピューティング | 25問 | Azure Automation・VMSS Auto Scale・Deployment Slots・AKS・Functions |
| 監視 | 12問 | Azure Monitor・Log Analytics・Application Insights・Network Watcher |
| バックアップ | 8問 | Azure Backup・Site Recovery・MARS エージェント |
| **合計** | **100問** | Medium中心 / Hard 含む |

各問題には **正解の理由・落とし穴・サービス比較表・キーワード** が付いています。

### 参考書 (`study.html`)

| セクション | 内容 |
|---|---|
| チートシート | 7カテゴリ・主要サービスをカード形式で要点まとめ |
| サービス比較表 | ストレージ冗長性・VM可用性・ロードバランサー・ID同期方法など5種 |
| 分野別ポイント | 試験で狙われるポイントと落とし穴を分野ごとに整理 |
| アーキテクチャ図解 | ハイブリッド接続・グローバルWeb・ゼロトラストID |
| 用語集・略語 | Entra ID / PHS / PIM / RBAC / VMSS / NSG / UDR など35語 |

---

## ✨ Features

- **深掘り解説** — 正解の理由 + よくある落とし穴を毎問表示
- **サービス比較表** — 類似サービスの違いを問題ごとに整理
- **分野別フィルタ** — 苦手分野だけ絞って集中練習
- **スコア追跡** — 正答率・連続正解・分野別グラフ（結果画面）
- **ビルド不要** — ブラウザで開くだけ。npm install 不要
- **PC / スマホ対応** — スマホではボトムナビに切り替わる
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
├── index.html    # 問題演習アプリ（28問収録）
├── study.html    # 参考書ページ（チートシート・比較表・図解・用語集）
└── README.md
```

問題データは `index.html` 内の `const QS = [...]` に直接記載しています。

---

## ➕ Adding questions

`index.html` 内の `const QS = [...]` に以下の形式でオブジェクトを追加してください。

```js
{
  domain: "ID管理",          // 下表の値を使用
  cat:    "Azure AD / Entra ID",  // バッジ表示用（自由記述）
  diff:   "Medium",          // "Easy" | "Medium" | "Hard"
  q:    "問題文...",
  opts: ["選択肢A", "選択肢B", "選択肢C", "選択肢D"],
  ans:  1,                   // 正解の選択肢インデックス（0始まり）
  why:  "正解の理由...",
  trap: "よくある落とし穴...",
  cmp: [                     // サービス比較表（省略可）
    { svc: "サービス名", feature: "特徴", rto: "目安", cost: "低/中/高", note: "備考" }
  ],
  kws: ["キーワード1", "キーワード2"]
}
```

### domain に指定できる値

| 値 | カバーするトピック例 |
|---|---|
| `ID管理` | Entra ID・RBAC・Conditional Access・PIM・B2B・Managed Identity |
| `コンピューティング` | VM・VMSS・App Service・AKS・ACI・Azure Functions |
| `ストレージ` | Blob・Azure Files・File Sync・冗長性・SAS・Data Box |
| `ネットワーク` | VNet・NSG・VNet Peering・Application Gateway・ExpressRoute |
| `監視` | Azure Monitor・Log Analytics・Application Insights・Network Watcher |
| `ガバナンス` | Azure Policy・管理グループ・Blueprints・リソースロック・タグ |
| `バックアップ` | Azure Backup・Site Recovery・MARS エージェント |

---

## 📄 License

MIT
