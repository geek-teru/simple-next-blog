## Nextjs

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

### layout.tsx とは

- 全体で共通のコンポーネントを管理するファイル
- 具体的にはヘッダーやフッターなど
- RootLayout メソッド内で以下のように記述する。{children}には page.tsx の内容が入る

```
  return (
    <html lang="ja">
      <body>
        <header>Header</header>
        {children}
      </body>
    </html>
  );
```

### コンポーネント

- ヘッダーやフッターなど全体で共通の部分はコンポーネントとして分割する。
- コンポーネント名は必ず大文字で始める必要がある。コンポーネントのファイル名は大文字で始まるようにするのがベター
- src/app に Header.tsx を作成し、layout.tsx から読み込む
- rafce と入力し Tab キーでひな形が作成される。

```ts
// Header.tsx
import React from "react";

const Header = () => {
  return <div>Header</div>;
};

export default Header;
```

- layout.tsx では import して`<Header />`

```ts
// layout.tsx

return (
  <html lang="ja">
    <body>
      <Header /> //　ここがヘッダーコンポーネント
      {children}
      <footer>footer</footer>
    </body>
  </html>
);
```

## Tips

### ESLint とは

ESLint は、JavaScript / TypeScript のコードを静的に解析して、構文エラーやスタイルの問題を検出・自動修正するためのツール

### VSCode Extension(拡張機能)

- ES7+ React/Redux/React-Native snippets: Tab 補完
- Auto Rename Tag: HTML のタグ
- Auto Close Tag: HTML の閉じタグ
- HTML CSS Support: HTML やスタイルの補完
- Prettier - Code formatter: HTML などのコードフォーマッター
- Material Icon Theme: アイコンをいい感じにする

## aside タグ

- 補足的な内容や本筋から少し離れた情報を示すために利用する。プロフィールや広告など
- <section className="w-full md:w-2/3 flex flex-col items-center px-3">はメインのセクションが2/3の割合
- <aside className="w-full md:w-1/3 flex flex-col items-center px-3 md:pl-6">はasideが1/3の割合
