# 個人情報マスキングツール fuseji.jp《ふせじ》

ブラウザ上で完結し、外部へのデータ送信を一切行わない安全な個人情報マスキングツールです。

[![Version](https://img.shields.io/badge/version-2.57-blue)](https://fuseji.jp)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

🌐 **オンライン版**: [fuseji.jp](https://fuseji.jp/)

---

## 特徴

- **完全ローカル処理** — テキストは一切外部に送信されません
- **インストール不要** — ブラウザ（またはHTMLファイルをダブルクリック）で即使用可能
- **対話的なマスキング** — 自動判定 + 手動修正で精度を高められます
- **逆変換機能** — AIに処理させた結果を元のテキストに復元できます
- **辞書機能** — よく使う人名・法人名・語句をブラウザに永続保存

---

## 使い方

1. HTMLファイルをブラウザで開く（またはダブルクリック）
2. 左側のテキストエリアに個人情報を含むテキストを貼り付ける
3. **⚡ 自動判定** を押す — メール・電話・住所・氏名・法人名などを一括検出
4. チップを確認し、不要なものは ✕ で削除
5. **マスキング実行**（または Ctrl+Enter）で右側にマスキング済みテキストを生成
6. 右側テキストを生成AIに貼り付け、AIの出力を「逆変換」パネルで元テキストに復元

---

## 外部辞書（オプション）

`address-dict.json`（地名辞書）と `corp-dict.json`（法人名辞書）を読み込むと、自動判定の精度が向上します。辞書データはブラウザのIndexedDBに保存されます（外部送信なし）。

### オンライン版（fuseji.jp）での使い方

1. ⋯ メニュー →「⚙ 辞書・ブロックリスト管理」を開く
2. **外部辞書** セクションの「⬇ 取得」ボタンを押す
3. fuseji.jp から辞書を自動取得してIndexedDBに保存されます

> **注意**: 「⬇ 取得」ボタンを押したときだけ fuseji.jp に通信します。テキストのマスキング処理自体は常に完全ローカルです。

### ローカルファイルでの使い方

ローカルファイル（`file://`）で開いた場合、セキュリティ上の制約によりネットワーク取得はできません。「⬇ 取得」ボタンは表示されません。

1. [fuseji.jp/address-dict.json](https://fuseji.jp/address-dict.json) と [fuseji.jp/corp-dict.json](https://fuseji.jp/corp-dict.json) をあらかじめダウンロードしておく
2. ⋯ メニュー →「⚙ 辞書・ブロックリスト管理」を開く
3. **外部辞書** セクションの「📂 読み込む」で保存したJSONファイルを選択

### オンライン版とローカル版の違い

| 機能 | fuseji.jp（オンライン） | ローカルファイル |
|---|---|---|
| テキストのマスキング処理 | 完全ローカル | 完全ローカル |
| 辞書の「⬇ 取得」ボタン | 使用可能 | 非表示 |
| 辞書の「📂 読み込む」 | 使用可能 | 使用可能 |
| 辞書・設定の保存先 | fuseji.jp のブラウザ領域 | file:// のブラウザ領域 |

辞書の保存先はオリジン（開き方）ごとに独立しています。オンライン版で登録した辞書はローカル版では引き継がれません。

---

## 辞書ファイルの出典・ライセンス

### address-dict.json（地名辞書）

- **出典**: [Geolonia 住所データ](https://github.com/geolonia/japanese-addresses)（Geolonia株式会社）
- **元データ**: 国土交通省位置参照情報ダウンロードサービス、日本郵便 郵便番号データ
- **ライセンス**: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ja)
- **加工内容**: 都道府県・市区町村名をフラットなリスト形式に変換し、fuseji辞書フォーマットに整形

> Geolonia 住所データ（CC BY 4.0）https://github.com/geolonia/japanese-addresses を加工して作成

### corp-dict.json（法人名辞書）

- **出典**: [国税庁法人番号公表サイト](https://www.houjin-bangou.nta.go.jp/)（国税庁）、EDINETコードリスト（金融庁）
- **ライセンス**: [公共データ利用規約（第1.0版）](https://www.houjin-bangou.nta.go.jp/riyokiyaku/)
- **加工内容**: 内国法人・組合のみを抽出し、全角文字の正規化・個人名の除外を行い、fuseji辞書フォーマットに整形

> 国税庁法人番号公表サイト（国税庁）https://www.houjin-bangou.nta.go.jp/ を加工して作成  
> このサービスの内容は国税庁によって保証されたものではありません

---

## ライセンス

本ツール（HTMLファイル本体）は [MIT License](https://opensource.org/licenses/MIT) のもとで公開しています。

---

## クレジット

Concept & Design: [@TadashiNakai](https://x.com/TadashiNakai)  
Implementation: Claude (Anthropic)
