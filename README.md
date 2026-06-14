# azure-az104-study

AZ-104（Microsoft Azure Administrator）試験対策のための自学習Webアプリ。  
問題演習（`index.html`）と参考書（`study.html`）の2ファイル構成で、サーバー不要・ブラウザだけで動作する。

---

## ファイル構成

```
azure-az104-study/
├── index.html   # 問題演習アプリ（本ファイル）
├── study.html   # 参考書ページ
└── README.md
```

---

## 機能

### 問題演習（index.html）

| 機能 | 説明 |
|------|------|
| **分野フィルター** | 全て / ID管理 / ネットワーク / ストレージ / コンピューティング / 監視 / バックアップ から選択 |
| **ランダム出題** | フィルター適用後にシャッフルして出題 |
| **4択問題** | 選択するとその場で正誤判定 |
| **解説パネル** | 正解理由（why）・ひっかけポイント（trap）・比較テーブル（cmp）・キーワード（kws）を表示 |
| **比較テーブル** | 関連サービスをサービス名・特徴・RTO/特性・コスト・備考で並べて比較 |
| **連続正解バッジ** | 3問以上連続正解で 🔥 ストリークバッジを表示 |
| **進捗バー** | 現在の進行状況をプログレスバーで表示 |
| **統計カード** | 回答数・正解数・不正解数・正解率をリアルタイム更新 |
| **結果画面** | セッション終了後に総合スコア・円グラフ・分野別正解率を表示 |
| **参考書リンク** | ヘッダーの「参考書」ボタンで `study.html` に遷移 |

---

## 問題データ仕様

全 **100問**。`const QS = [...]` に格納。各問題は以下の構造を持つ。

```js
{
  domain: "ネットワーク",          // 分野（6種）
  cat:    "Azure Firewall",       // カテゴリ（小分類）
  diff:   "Hard",                 // 難易度: Easy | Medium | Hard
  q:      "問題文...",
  opts:   ["選択肢A","B","C","D"],  // 必ず4択
  ans:    1,                       // 正解インデックス（0〜3）
  why:    "正解の理由...",
  trap:   "ひっかけポイント...",
  cmp: [                           // 比較テーブル（1〜4行）
    { svc:"サービス名", feature:"特徴", rto:"RTO/特性", cost:"コスト感", note:"備考" },
  ],
  kws:    ["キーワード1","キーワード2"]  // 3個以上推奨
}
```

### 分野別問題数・AZ-104試験比率

| 分野 | 問題数 | 主なカテゴリ |
|------|--------|-------------|
| ネットワーク | 25問 | VNet / NSG / VPN / DNS / Private Endpoint / Firewall / LB |
| ID管理 | 20問 | 条件付きアクセス / RBAC / PIM / ManagedID / B2B / SSPR |
| コンピューティング | 20問 | VM可用性 / App Service / AKS / ACI / Functions / VMSS |
| ストレージ | 15問 | Blob / Files / Disk / 冗長性 / CDN / Soft Delete |
| 監視 | 12問 | Azure Monitor / Log Analytics / KQL / Application Insights / Sentinel |
| バックアップ | 8問 | Azure Backup / Site Recovery / PITR / Soft Delete / 保持ポリシー |
| **合計** | **100問** | |

### 難易度分布

| 難易度 | 問題数 |
|--------|--------|
| Easy   | 9問    |
| Medium | 57問   |
| Hard   | 34問   |

---

## 使い方

1. `index.html` をブラウザで開く（ダブルクリックまたはローカルサーバー経由）
2. 上部の分野ボタンで出題範囲を絞り込む（デフォルトは「全て」）
3. 4つの選択肢から1つ選ぶと即座に正誤判定
4. 解説・比較テーブル・キーワードを確認して「次へ」
5. 全問回答後に結果画面で分野別の弱点を確認
6. 「もう一度」でシャッフルして再挑戦

---

## 技術仕様

- **依存関係**: なし（外部CDN: Tabler Icons のみ）
- **動作環境**: モダンブラウザ（Chrome / Edge / Firefox / Safari）
- **サーバー**: 不要（静的HTMLファイル）
- **データ永続化**: なし（ページリロードでリセット）

---

## 問題を追加・編集する場合

`index.html` 内の `const QS = [...]` に問題オブジェクトを追記する。  
以下の点に注意。

- `ans` は選択肢配列の **0始まりインデックス**（0〜3）
- `opts` は **必ず4要素**
- `diff` は `"Easy"` / `"Medium"` / `"Hard"` のいずれか（大文字始まり）
- `domain` は `DOMAINS_ARR` に定義された6分野のいずれか
- `cmp` の各行は `svc / feature / rto / cost / note` の5フィールドが必須

---

## 関連リソース

- [Microsoft Learn - AZ-104 学習パス](https://learn.microsoft.com/ja-jp/certifications/exams/az-104/)
- [AZ-104 試験スキルの概要](https://learn.microsoft.com/ja-jp/credentials/certifications/resources/study-guides/az-104)
- [Azure ドキュメント](https://learn.microsoft.com/ja-jp/azure/)
