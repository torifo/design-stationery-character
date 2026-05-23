# POCO POCO Design Learnings

## 目的

キャラクター文具のオリジナル店構えを、既存IPに頼らず構築する試み。小〜中学生にとって「持っているだけで気分が上がる」店を、3キャラのオリジナル世界観で実装した。

このブランドは架空店舗であり、実在の店舗・商品ではない。

## 設計したこと

- 3キャラ（しずく・まめ・ふくちゃん）を全て SVG で実装。Inline で軽量、色変更も自在
- キャラに `@keyframes bob` でふんわり浮遊アニメを付与し、ページが生きてる感じを出した
- カードに「3px枠＋角丸＋ハードシャドウ」を統一適用、ステッカーを貼り重ねた紙面感
- 章タイトル前にピンクの丸をプリフィックスとして配し、リズムを作った
- ナビボタンも「角丸＋ハードシャドウ」で、押せそうな実体感を持たせた

## CSS

```css
:root {
  --pink:#ffb3c6; --pink-d:#ff7ba1;
  --yellow:#ffe566;
  --ink:#3a2b3e;
  --font:'Zen Maru Gothic','M PLUS Rounded 1c',sans-serif;
}

/* キャラのふんわり浮遊 */
@keyframes bob1 {
  0%,100% { transform: translateY(0) rotate(-3deg) }
  50%     { transform: translateY(-10px) rotate(3deg) }
}

/* カード共通 */
.item {
  border: 3px solid var(--ink);
  border-radius: 18px;
  box-shadow: 5px 5px 0 var(--ink);
}
.item:hover {
  transform: translate(-3px,-3px);
  box-shadow: 8px 8px 0 var(--pink-d);  /* hover で影色が変わる */
}

/* ロゴアイコンのキャラ顔（疑似要素で構成） */
.b-icon::before {
  content:"";
  position:absolute; top:35%; left:25%;
  width:.4rem; height:.4rem; border-radius:50%; background:#fff;
  box-shadow: .85rem 0 0 #fff;  /* 1要素で2目を作る */
}
```

ロゴアイコンは画像を一切使わず、`::before` と `::after` だけで2つの目と1つの口を表現。実体は CSS だけで完結している。

## アニメーション

- キャラの浮遊（3.5〜4.5s ループ、3つの位相を変えて配置）
- ロゴの揺れ（4s ループ）
- カードホバー時の translate＋影色変化

`prefers-reduced-motion: reduce` に対する対応は次回の優先課題（todo）。

## フォント

- 主: `Zen Maru Gothic`（丸ゴ、子供向けに優しい）
- フォールバック: `M PLUS Rounded 1c`
- セリフ・モノは不採用

## ボタン

ナビが「角丸ピル + 2px黒枠 + 2px黒シャドウ」のステッカー風で、すべてのリンクがボタンに見える設計。ホバーで影色がピンクに変わる。

## UI/UX

- ナビ4項目（商品 / なかま / お知らせ / 店）
- 「3人のなかま紹介」セクションでキャラの背景を語り、IPの厚みを作る
- お知らせは date 起点の縦リスト、点線で区切る

## レイアウト

`max-width: 1100px` の中央寄せ、グリッドは `repeat(auto-fill, minmax(200px, 1fr))`。商品カードを正方形（aspect-ratio: 1/1）にして、カード全体がキャラのカードゲーム感を維持。

色は5色（ピンク・イエロー・水色・緑・クリーム）の中から1色を商品ごとに割り振り、5色循環で活気を演出。
