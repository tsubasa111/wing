# タスク管理システム OSS

## 初期開発環境手順

1. make start-up
2. make n-bash
3. npm i
4. npm run dev

次回から

1. make up
2. make n-bash
3. npm run dev

## 技術スタック

React 17.0.2  
Next 11.0.1  
SWR 0.5.6

Go 1.17  
echo 4 系

## ディレクトリ構造

```
├── src
│   ├── pages ルーティング
│   │   └── [PageName]
│   │           ├── index.tsx
│   │           └── [PageName]
│   ├── components
│   │   ├── identities ページ単位で必要なパーツ
│   │   │   └── [Page Name]
│   │   │       └──[Component Name]
│   │   │          ├── index.tsx
│   │   │          └── style.tsx
│   │   │
│   │   ├── originals 特定の用途でしか使われない
│   │   ├── templates レイアウト
│   │   └── uiParts 共通UIパーツ
│   │       └── [Component Name]
│   │           ├── index.tsx
│   │           └── style.tsx
│   │
│   ├── models 型定義
│   ├── pageStyles pagesに直接使う なくなる予定
│   ├── styles 全体のスタイル
│   └── utils 他に必要なもの
```

# Go 基本ルールまとめ

## Response

| String | 内容                         | 返り値   |
| ------ | ---------------------------- | -------- |
| data   | クライアントに送りたいデータ | データ   |
| status | 成功か失敗か                 | ok or ng |

```go
{
  "data": {
    interface{}{

    }
  },
  "status": code < 300 ok else ng,
}
```

## 依存関係

router  
↓ ↑  
Handler  
↓ ↑  
usecase  
↓ ↑  
service  
↓ ↑  
repository

## ディレクトリ構成

```
go
├── application
│   ├── format  整形する
│   └── usecase ユースケース
│
├── db
│   ├── seed     サンプルデータの流し込み
│   └── mysql.go DB接続系
│
├── domain
│   ├── model      型定義
│   ├── entity     テーブル構成
│   ├── repositoty リポジトリ
│   └── service    ビジネスロジック
│
├── infrastructure
│   ├── auth        認証系
│   ├── cookie      クッキー操作
│   ├── persistence リポジトリビジネスロジック
│   ├── security    セキュリティー
│   └── storedb     KVS系
│
├── interface
│   ├── context    抽象化されたデータ構造
│   ├── fileupload ファイル操作
│   ├── handler    コントローラー
│   ├── middleware ミドルウェア
│   ├── response   カスタムレスポンス
│   └── validation バリデーション
│
└── main.go
```

# License

Distributed under MIT License, please see license file within the code for more details.
