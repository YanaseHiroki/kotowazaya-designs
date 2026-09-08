# ことわざ屋 — 入稿デザイン画像

Shopify ストア「ことわざ屋」（ことわざ・故事成語のステッカー）を Printful で刷るための
**入稿用デザイン画像 1,320 枚**と、その対応表・書体ライセンス。

生成日 2026-09-08。**この木の中身はすべて機械が作ったもので、手で直さない。**
文言・色・書体を変えるときは生成元（下の「作り直しかた」）を直して流し直す。

```
designs/*.png    1,320枚（60MB）。入稿するのはこのフォルダだけ
manifest.csv     画像 ↔ バリエーションSKU の対応表（1,320行）
fonts/*-OFL.txt  使った3書体のライセンス本文（記録用）
```

## 内訳

**55文言 × 4背景色 × （3書体 × 2向き） = 1,320**。
**2026-09-08 に25文言（600枚）を足した**（当初は30文言・720枚）。
サイズ（S 76mm / M 102mm / L 140mm）は同じ画像の拡大縮小なので枚数は増えない。

| 軸       | 値                                                                     |
| -------- | ---------------------------------------------------------------------- |
| 文言     | ことわざ・故事成語 55 件（すべて作者不明の古典。著作権が発生しない）   |
| 背景色   | 生成り `#f2ece0` / 藍 `#1f3c66` / 墨 `#22201e` / 朱 `#b03a2e`          |
| 書体     | 明朝 Shippori Mincho / 筆文字 Yuji Syuku / 極太ゴシック Dela Gothic One |
| 文字の向き | 縦書き / 横書き                                                       |

ファイル名は `PRV-{通し番号}-{背景色}-{書体}{向き}.png`。
例 `PRV-01-KNR-MINT.png` = 石の上にも三年 / 生成り / 明朝 / 縦書き。
これに S・M・L を挟んだものが Shopify のバリエーション SKU（`PRV-01-KNR-S-MINT`）で、
対応は `manifest.csv` の `variant_skus` 列にある。

## 画像の仕様

| 項目       | 値                                                                        |
| ---------- | ------------------------------------------------------------------------- |
| 寸法       | 1650 × 1650 px（正方形）                                                  |
| 解像度     | 300 dpi（最大の 140mm 実寸ちょうど。76mm に使えば約 550dpi）              |
| 形式       | PNG・8bit・不透過（背景色を四隅まで塗る）                                 |
| カラー     | **sRGB IEC61966-2.1 の ICC プロファイルを埋め込み済み**（iCCP チャンク）  |
| 文字の余白 | 版面の 14%（実寸 19.6mm）以上。実測でいちばん端に近い字で 19.0mm          |
| 1枚あたり  | 平均 45KB（21〜68KB）。1,320枚で 60MB                                     |

**塗り足し（bleed）は要らない。** 背景が単色なので、どこで切られても白は出ない。
**Printful はステッカーの外周に白フチを足す**ので、文字は端から十分に離してある。

書き出しは**決定的**（同じ入力なら1ビットまで同じ）。時刻のメタデータ（tIME・date:\*）だけ
外してある —— 中身が同じなのに毎回バイトが変わると、入稿し直す必要のない画像まで
「変わった」ことになるため。**色に関わるメタデータは1つも捨てていない。**

出典（2026-09-08 に確認）:

- [ステッカーの推奨ガイドライン](https://support.printful.com/hc/en-us/articles/41396541153553-What-are-the-recommended-guidelines-for-stickers) — PNG/JPEG・300dpi 以上・外周に白フチ・要素間 0.25in
- [RGB か CMYK か](https://help.printful.com/hc/en-us/articles/28491774495772-Should-I-use-RGB-or-CMYK-for-Printful-print-files) — sRGB IEC61966-2.1 を埋め込んで書き出す。CMYK へ変換しない
- [入稿データの作りかた](https://www.printful.com/blog/everything-you-need-to-know-to-prepare-the-perfect-printfile) — 最低 150dpi、商品により 300dpi
- [キスカットステッカーの商品ページ](https://www.printful.com/custom/stickers/die-cut/kiss-cut-stickers) — 7.62 / 10.16 / 13.97cm の正方形

## 書体のライセンス

3書体とも **SIL Open Font License 1.1**（`fonts/` に本文）。
OFL は**商用利用・埋め込み・再配布**のいずれも認めている（禁じているのはフォント単体を
売ることと、予約名を保ったままの改変配布）。**描き出した画像の側には制約が及ばない**ので、
グッズとして販売できる。原本は Google Fonts の
[shipporimincho](https://github.com/google/fonts/tree/main/ofl/shipporimincho) /
[yujisyuku](https://github.com/google/fonts/tree/main/ofl/yujisyuku) /
[delagothicone](https://github.com/google/fonts/tree/main/ofl/delagothicone)。

55文言に使う 220 文字が3書体すべてに収録されていることは機械で検査済み（`--check-fonts`）。

## 作り直しかた

生成元は **Shopify アプリ側のリポジトリ**にある（カタログ CSV と定数を共有していて、
ことわざを足しても画像とカタログがずれないため）。

```bash
cd ~/git/shopify-line-ai
node scripts/make-proverb-designs.mjs --licenses   # 1,320枚 + 対応表 + ライセンス（約4分）
node scripts/make-proverb-designs.mjs --verify     # 寸法・余白・白紙の検査
node scripts/make-proverb-designs.mjs --sample     # 見本を12枚だけ
```

文言・色・書体は `scripts/make-proverb-catalog.mjs` の定数が唯一の出どころ。
そちらを直したら**カタログ CSV も画像も両方作り直す**こと。
ImageMagick 7（`magick`）が要る。

## 公開URL

このリポジトリを公開しているのは、**Printful が印刷ファイルを公開URLでしか受け取らない**ため。

```
https://raw.githubusercontent.com/YanaseHiroki/kotowazaya-designs/main/designs/<ファイル名>
```

例: <https://raw.githubusercontent.com/YanaseHiroki/kotowazaya-designs/main/designs/PRV-01-KNR-MINT.png>

Printful は取り込んだ印刷ファイルを自社のファイルライブラリに保存するので、
**結び付けが済んだあとも公開を続ける必要があるかは要確認**（不要ならこのリポジトリは
非公開に戻せる）。

## 次にやること

1. ~~画像を公開URLに置く~~【済】上のURL（720枚 2026-09-08、追加600枚も同日）
2. **Printful のアカウントを作り、Shopify ストア「ことわざ屋」をつなぐ**（オーナーの手作業）。
   つないだ時点で既存の商品・バリエーションが Printful に取り込まれる
3. **印刷ファイルをバリエーションに結び付ける** —— `link-proverb-printful.mjs`。
   **Shopify につないだストアでは API から商品を作れない**（Printful の Products API は
   外部プラットフォームの商品作成を意図していない）ので、取り込まれたバリエーションを
   1つずつ更新する。毎分120回の上限で、55商品ぶん3,960回なら約33分
4. **Shopify の商品に画像を付ける** — 商品CSVには画像を入れられないので、管理画面か API で
