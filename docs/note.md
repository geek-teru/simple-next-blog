### 基本的なディレクトリ構成

```
my-app/
└── src/
    ├── app/
    │   ├── favicon.ico       # サイトのアイコン（<head>で使用）
    │   ├── globals.css       # 全体に適用するCSS
    │   ├── layout.tsx        # 全ページ共通のレイアウト（ヘッダー・フッターなど）
    │   └── page.tsx          # トップページ (`/` に対応)
```

### app ディレクトリとは

- app ディレクトリ内では、ディレクトリ構造そのものがルーティング構造になる。
- 各ディレクトリは「URL のパス」、page.tsx は「そのパスに対応するページ」として扱われる。
- 例えば以下のようなディレクトリ構成の場合、`localhost:3000/blog`のページが作成される。

```
app/
├── layout.tsx
├── page.tsx
├── about/
│   └── page.tsx
├── blog/
│   ├── layout.tsx
│   └── page.tsx
```

### app ディレクトリは SSR

- app ディレクトリはデフォルトで SSR
- クライアントサイドレンダリングや use effect(API からのデータ取得)を利用したい場合は、先頭に`"use client";`と書いておく

### ESLint とは

ESLint は、JavaScript / TypeScript のコードを静的に解析して、構文エラーやスタイルの問題を検出・自動修正するためのツール

### VSCode Extension(拡張機能)

- ES7+ React/Redux/React-Native snippets: Tab 補完
- Auto Rename Tag: HTML のタグ
- Auto Close Tag: HTML の閉じタグ
- HTML CSS Support: HTML やスタイルの補完
- Prettier - Code formatter: HTML などのコードフォーマッター
- Material Icon Theme: アイコンをいい感じにする
