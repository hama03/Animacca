# Next.js ディレクトリ構成

## ディレクトリ構成

[下記の記事](#参考記事)を参考に、複雑な部分は削ってシンプルにしてみました。  
どんなディレクトリが必要で、どの機能をどう分類したら良いかなど現時点ではあまり想像がついていないです...  
作りながら追加、修正していってもらえると助かります!!

ファイル名などは仮なので参考までに...

```bash
├─ app/
├─ components/
│  ├─ elements/
│     └─ Button.jsx
│  └─ layouts/
│     ├─ Header.jsx
│     └─ Footer.jsx
├─ features/
│  ├─ map/
│     ├─ api/
│        ├─ getPlace.js
│        └─ getMap.js
│     ├─ components/
│        ├─ Map.jsx
│        └─ Pin.jsx
│     └─ hooks/
│        └─ useMap.js
│  └─ favorite/
│     └─ components/
│        └─ Favorite.jsx
├─ hooks/
└─ utils/
```

### app/

ルーティングのファイル(page.js)を入れる。

### components/

アプリケーション全体で使うコンポーネントを入れる。

### features/

特定の領域に関する機能を入れる。  
map や favorite など特定の領域ごとに分けて、関連する機能をまとめる。

### hooks/

アプリケーション全体で使う React のカスタムフックを入れる。

### utils/

アプリケーション全体で使う汎用的な関数を入れる。

## 参考記事

- [【2024 年 1 月】Next.js での新規アプリの構成 & Next.js ディレクトリ構成(features)](https://zenn.dev/hokuto_tech/articles/fdabaff60f5af2)
- [Next.js ディレクトリ構成・設計再考（features が何を解決するか）](https://zenn.dev/yodaka/articles/eca2d4bf552aeb)
