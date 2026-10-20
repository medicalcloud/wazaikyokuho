# 太平恵民和剤局方 原文・注・現代語訳

『太平惠民和劑局方』（宋の和剤局の処方集。進表，卷之一〜卷之十，指南總論 卷上・中・下）の原文を，方ごと・論ごとの小さな単位に分け，資料間の異同（校異）・校訂，現代語訳（日本語・英語）と解説と組み合わせたもの。付録に『增廣和劑局方藥性總論』と朱震亨『局方發揮』の原文を収める。人が読むためだけでなく，LLM が読みやすいことを目指して，1単位を1ファイルにし，ファイルの頭に機械で読める情報（YAML）を付けている。

**現在の状況**：原文（全1431単位）・校異・校訂と，進表・全方・指南總論の日本語訳・英訳ができている（2026-10-13）。姉妹編に[傷寒論](https://github.com/medicalcloud/shokanron)・[金匱要略](https://github.com/medicalcloud/kinkiyoryaku)・[黄帝内経](https://github.com/medicalcloud/koteidaikei)・[神農本草経](https://github.com/medicalcloud/shinnohonzokyo)がある。

## 構成

```
NN_篇/
  index.md      門・単位の一覧
  NNN.md        方・論・薬の単位：原文＋校異・校訂
  pNNN.md       段落の単位（進表，局方發揮）
  NNN.ja.md     日本語訳
  NNN.en.md     英訳
```

- 篇は 00 進表，01〜10 卷之一〜卷之十（方，800単位），11〜13 指南總論 卷上・中・下（論，102単位），14 藥性總論（薬，460単位），15 局方發揮（段落，67単位）。
- 方の単位の原文は，方名，主治，薬と分量・修治，製法・服法の順（底本のまま）。
- 各卷の方は門（治諸風など）に属し，門の中は元の方のあとに層の見出し（紹興續添方・寶慶新增方・淳祐新添方・吳直閣增諸家名方・續添諸局經驗秘方・新添諸局經驗秘方）で後から加わった方が続く。門は YAML の category，層は layer に記した。
- 指南總論は論（「論…」の見出し）ごとの単位。いくつかの論をまとめる大きな見出し（論中風證候 など）は heading に記した。
- 底本の図と表（卷七の五行八卦之圖，卷九の產圖・催生符圖・行年の表など9つ）は，どの資料にも文字がなく，底本の画像も公開されていないので，原文・訳とも〔図：…〕で置き場所だけを示した。

### ファイルの頭の情報（YAML）

| キー | 内容 |
|---|---|
| book | 書名 |
| chapter / chapter_title | 篇の番号と篇名 |
| unit | 単位の番号（ファイル名） |
| kind | 単位の種類（方・論・薬・段落・署名） |
| name | 方の名・論の名・薬の名 |
| category | 門（方），部（藥性總論） |
| layer | 層（紹興續添方など。元の方にはない） |
| heading / heading_note | 指南總論の大きな見出しとその注（「（附脾胃積聚）」など） |
| title | 単位の題 |
| punctuated | 原文に句読点があるか（底本の句読点） |

## 底本と，本文の補い・訂正

### 底本

- **どのような本か**：『太平惠民和劑局方』の元大德八年（1304）余志安勤有堂刊本。
- **どのように入手したか**：中醫笈成（jicheng.tw）がこの刊本を底本とし，四庫全書本で校勘して公開している電子テキストを，中醫笈成のデータ（gitlab.com/jicheng/jc.data。公有の典籍への編集は CC0）の HTML から，2026-10-12 に取得して使った。句読点は中醫笈成のもの。
- **字の変換**：日本の新字体に直した（方針は `字体と変換の方針.md`）。簡体字から戻したときに生じたらしい一対多の字の誤り（干/乾・須/鬚・面/麺・制/製・曲/麹・里/裏 など）は，四庫全書本・行政院本の同じ位置の字で直した（校異には記さない）。

### 底本に足りないところ

- 底本の「□」は底本の欠字で，補っていない。

### 訂正（校訂）

- 本文を改めたのは22か所。主に四庫全書本と行政院本の字と比べて，一番それらしい字を採った（多くは両本がともに同じ字に作るところ）。改めたところには【校訂】として，元の字句・各資料の字・改めた理由を記した。
- 資料がみな同じで誤りとも決めきれないもの（柴石英 など）は改めず，訳の解説で触れた。

### 照合した資料

- **四庫全書文淵閣本**：Kanripo（KR3e0033）の電子テキスト。
- **行政院中醫藥委員會の文本 CM064**：中醫笈成「太平惠民和劑局方_1」。卷之一〜十だけ。
- **Wikisource**（中文維基文庫）「太平惠民和劑局方」，**殆知閣**「太平惠民和剂局方」：同じ電子テキストの系統らしい。
- 付録の2書（藥性總論・局方發揮）は殆知閣本と照合した。
- **校異**：資料と底本の字句の違い（3393件）。「X は「…」に作る」「…の間に，X は「…」がある」の形。字体・異体字・繁簡の違い，通用字・古今字（剉/銼・卒/猝・差/瘥 など），版による決まった書き方の違い（「上為細末」と「右為細末」，丸と圓），簡体字では区別できない字，句読点，他の資料の欠落，資料自体の変換の誤りは記していない。四庫全書本は方の中の薬の並びが違うことがあり，並びの違いによる対応のずれが一部残っている可能性がある。位置が合わず照合しなかった区間がある。

## 訳の範囲と書き方

- 日本語訳・英訳と解説は，進表，卷之一〜十のすべての方，指南總論のすべての論に付ける。付録の2書（藥性總論・局方發揮）は原文だけ（後で訳を足せる形にしてある）。
- 日本語訳は書き下しではなく現代語訳。〔〕は訳者が補った語。解説は要旨と，必要に応じて底本の問題点・他の卷の方との関係（「卷之五041」の形）を記す。後から加わった層の方は，解説の初めに〔紹興続添方〕などと記す。
- 英訳では方名・薬名をピンイン（必要に応じて英語の説明）で示した。

## 権利とライセンス

- **古典の文**（『太平惠民和劑局方』の本文，付録の『增廣和劑局方藥性總論』『局方發揮』）：パブリックドメイン。電子テキストの多くは中醫笈成（CC0）による。
- **このプロジェクトで新しく書いたもの**（校異・校訂の説明，日本語訳・英訳，解説，YAML の情報など）：LLM（Claude）を使って作成したもの。[クリエイティブ・コモンズ 表示-継承 4.0 国際（CC BY-SA 4.0）](https://creativecommons.org/licenses/by-sa/4.0/deed.ja)で提供する。利用するときは出典として「太平恵民和剤局方 原文・注・現代語訳（Hideaki Takata）」とこのリポジトリを示すこと。改変したものを配布するときは，同じ CC BY-SA 4.0（またはその互換ライセンス）で提供すること。詳しくは `LICENSE`。
- 訳と解説は LLM によるもので，誤りがありうる。臨床に用いる判断の根拠にはしないこと。

---

## English summary

This repository presents the *Taiping huimin heji ju fang* (Formulary of the Pharmacy Service for Benefiting the People in the Taiping Era), the Song-dynasty official formulary, split into one file per formula or discussion with YAML metadata. Each file contains the punctuated original text and textual variants and emendations collated against the Siku quanshu edition and three other electronic editions. Japanese and English translations with explanatory notes are provided for the memorial to the throne, all formulas in juan 1–10, and the *Zhinan zonglun* (General Guide). The *Zengguang heji jufang yaoxing zonglun* and Zhu Zhenheng's *Jufang fahui* are included in the original only. The base text is the edition on Zhongyi Jicheng (jicheng.tw, CC0). Classical texts are in the public domain; new material is CC BY-SA 4.0. Translations were produced with an LLM and may contain errors; not for clinical use.
