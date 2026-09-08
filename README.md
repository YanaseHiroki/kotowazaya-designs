# ことわざ屋 — 入稿デザイン画像

Shopify ストア「ことわざ屋」（ことわざ・故事成語のステッカー）を Printful で刷るための
**入稿用デザイン画像 2,640 枚**と、その対応表・書体ライセンス。

生成日 2026-09-08。**この木の中身はすべて機械が作ったもので、手で直さない。**
文言・色・書体を変えるときは生成元（下の「作り直しかた」）を直して流し直す。

```
designs/*.png    2,640枚。入稿するのはこのフォルダだけ
manifest.csv     画像 ↔ バリエーションSKU の対応表（2,640行）
fonts/*-OFL.txt  使った3書体のライセンス本文（記録用）
```

## 内訳

**55文言 × 4背景色 × （3書体 × 2向き） = 1,320** が2組で **2,640枚**。
**2026-09-08 に25文言（600枚）を足し**（当初は30文言・720枚）、同日に **S 版**を足した。

- **M（102mm）/ L（140mm）共用** 1,320枚 …… 版面いっぱいの正方形。拡大縮小して2サイズで使う
- **S（スマホ背面 65mm）専用** 1,320枚 …… 透明な版面に 58.6mm の角丸だけを塗ったもの

**S だけ形が違う。** Printful のキスカットは**不透明部分の輪郭に沿って**切り、外周に
0.125″（3.2mm）の白フチを自動で足すので、58.6mm の角丸を刷ると **65.0mm** に切り上がる。
台紙は 3″（76.2mm）の枠のままなので、**原価は M/L と同じ理屈で変わらない**。

| 軸       | 値                                                                     |
| -------- | ---------------------------------------------------------------------- |
| 文言     | ことわざ・故事成語 55 件（すべて作者不明の古典。著作権が発生しない）   |
| 背景色   | 生成り `#f2ece0` / 藍 `#1f3c66` / 墨 `#22201e` / 朱 `#b03a2e`          |
| 書体     | 明朝 Shippori Mincho / 筆文字 Yuji Syuku / 極太ゴシック Dela Gothic One |
| 文字の向き | 縦書き / 横書き                                                       |

ファイル名は2通り:

| 用途      | 形                                            | 例                       |
| --------- | --------------------------------------------- | ------------------------ |
| M/L 共用  | `PRV-{通し番号}-{背景色}-{書体}{向き}.png`     | `PRV-01-KNR-MINT.png`    |
| S 専用    | `PRV-{通し番号}-{背景色}-S-{書体}{向き}.png`   | `PRV-01-KNR-S-MINT.png`  |

`PRV-01-KNR-MINT.png` = 石の上にも三年 / 生成り / 明朝 / 縦書き。
**S 用は Shopify のバリエーション SKU そのまま ＋ `.png`**（`PRV-01-KNR-S-MINT`）。
M/L 共用のほうは1枚が2つの SKU に対応する。対応は `manifest.csv` の `variant_skus` 列にある。

**M/L 共用の 1,320枚は、S を足したときも名前を変えていない。** 名前が変わると
Printful に入っている入稿URLがずれて、2,640件が差し替え対象になってしまうため。

## 画像の仕様

| 項目       | 値                                                                        |
| ---------- | ------------------------------------------------------------------------- |
| 寸法       | 1650 × 1650 px（正方形）                                                  |
| 解像度     | 300 dpi（最大の 140mm 実寸ちょうど。76mm に使えば約 550dpi）              |
| 形式       | PNG・8bit。M/L は**不透過**（背景色を四隅まで塗る）／ S は**透過**（角丸の外はすべて透明） |
| カラー     | **sRGB IEC61966-2.1 の ICC プロファイルを埋め込み済み**（iCCP チャンク）  |
| 文字の余白 | M/L は版面の 14%（実寸 19.6mm）以上／ S は角丸の縁から 5mm 以上           |
| S の絵柄   | 58.6mm ＝ 1269px（左上 191px）。角の丸み 6mm ＝ 130px                     |

**塗り足し（bleed）は要らない。** 背景が単色なので、どこで切られても白は出ない。
**Printful はステッカーの外周に白フチ（0.125″ ＝ 3.2mm）を足す**ので、文字は端から十分に
離してある。四隅まで塗った M/L は台紙の正方形そのままに切られ、**S は角丸の外側 3.2mm で
切られる**（＝この白フチが S の仕上がり寸法の一部になっている）。

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
node scripts/make-proverb-designs.mjs --licenses   # 2,640枚 + 対応表 + ライセンス
node scripts/make-proverb-designs.mjs --verify     # 寸法・余白・白紙・S の透過と絵柄の検査
node scripts/make-proverb-designs.mjs --sample     # 見本だけ（M/L 12枚 ＋ S 24枚）
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

1. ~~画像を公開URLに置く~~【済】上のURL（720枚 2026-09-08、追加600枚と S 版1,320枚も同日）
2. ~~**Printful のアカウントを作り、Shopify ストア「ことわざ屋」をつなぐ**~~【済 2026-09-08】
   （オーナーの手作業）。つないだ時点で既存の商品・バリエーションが Printful に取り込まれる
3. ~~**印刷ファイルをバリエーションに結び付ける**~~【済 2026-09-08】—— `link-proverb-printful.mjs`。
   **Shopify につないだストアでは API から商品を作れない**（Printful の Products API は
   外部プラットフォームの商品作成を意図していない）ので、取り込まれたバリエーションを
   1つずつ更新する。毎分120回の上限で、55商品ぶん3,960回なら約33分
4. **S の 1,320件を「スマホ背面」用の画像へ差し替える** — 試し刷りを1枚見てから
   `link-proverb-printful.mjs`（無印。URL 不一致で S だけが対象になり M/L は素通り）。
   そのあと Shopify の表示名を `proverb-rename-size.mjs` で `スマホ背面（65mm）` に直す
5. **Shopify の商品に画像を付ける** — 商品CSVには画像を入れられないので、管理画面か API で
