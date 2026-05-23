# POCO POCO — stationery/character Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-23
**Updated:** 2026-05-23

---

## 1. Overview

### Problem Statement
小〜中学生向けキャラクター文具のECは、既存IPに依存しがちで、独自世界観の店構えが少ない。学校で使う文房具を「お勉強を少し楽しくする」体験として設計し直したい。

### Goal
3人のオリジナルキャラクター（しずく・まめ・ふくちゃん）を擁する架空のキャラクター文房具店「POCO POCO」を実装し、ステッカー風UI・丸み・パステルで「持っているだけで気分が上がる」店を成立させる。

### Non-Goals
- 既存IPコラボ
- カート / 決済
- 子供向け課金導線

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 小〜中学生 | 一目で「かわいい」と感じたい | 親に頼みたくなる |
| US-02 | 同上 | キャラがそれぞれ違うことを知りたい | 推しを決められる |
| US-03 | 保護者 | 店としての真面目さも感じたい | 安心して購入できる |

---

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | 3キャラを SVG で実装 | P0 |
| FR-02 | キャラはふんわり浮遊アニメ | P0 |
| FR-03 | 商品 6 アイテム（学校文具 + ステッカー）| P0 |
| FR-04 | 3キャラ紹介セクション（読みやすい） | P0 |
| FR-05 | お知らせセクション（3件） | P1 |
| FR-06 | 店情報セクション（黄色カード）| P0 |
| FR-07 | カードに角丸＆ハードシャドウ | P0 |
| FR-08 | モバイル対応 | P0 |

---

## 4. Key Design Decisions

| Decision | Chosen | Rationale | Rejected |
|----------|--------|-----------|----------|
| 主書体 | Zen Maru Gothic | 丸ゴ＋親しみ＋可読性 | Reggae One（強すぎる）|
| 配色 | パステル4色＋ピンク主導 | 子供心理に近い暖色域 | ビビッドのみ |
| カード | 角丸 + 3px枠 + ハードシャドウ | ステッカーを貼った感 | フラットシャドウ |
| 装飾 | 点線 + 丸 | 罫線より柔らかい | 直線・尖角 |
| アニメ | キャラ浮遊 + ロゴゆれ | 「生きてる感」 | ヒーロー静止 |

---

## 5. Design System

```css
--bg:#fff8f3;
--pink:#ffb3c6; --pink-d:#ff7ba1;
--yellow:#ffe566; --blue:#a8dcee; --green:#b8e6a8;
--ink:#3a2b3e;
--font:'Zen Maru Gothic','M PLUS Rounded 1c',sans-serif;
```

---

## 6. References

- [navigator README](../README.md)
- Font: [Zen Maru Gothic](https://fonts.google.com/specimen/Zen+Maru+Gothic), [M PLUS Rounded 1c](https://fonts.google.com/specimen/M+PLUS+Rounded+1c)
