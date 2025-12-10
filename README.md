# 📄 Secure PDF Auditor
**Administrative Forensics Module for Pithos OS.**

[![Status](https://img.shields.io/badge/System-Operational-success)]()
[![Privacy](https://img.shields.io/badge/Privacy-Local_Processing-green)]()
[![Engine](https://img.shields.io/badge/Built_with-PyScript_%2B_PDF.js-yellow)](https://pyscript.net)

> **「ノイズ（文章）を黒く塗りつぶせ。真実（数字）だけを浮かび上がらせろ。」**
>
> 行政の決算書や事業報告書は、膨大な「言い訳（テキスト）」で埋め尽くされています。
> 本ツールは、PDFから**「予算」と「人数」だけを外科手術的に抽出**し、その場で $D_{index}$（歪み指数）を判定する、クライアントサイド・フォレンジックツールです。

---

## 🖥️ Demo

**👉 [Launch Auditor](https://sbcm-alliance.github.io/pdf-audit/)**
*(PC / Smartphone Browser)*

<p align="center">
  <img src="docs/demo.png" alt="Audit Screen" width="600">
  <br>
  <em>CIA機密文書スタイルの「黒塗り」UIにより、監査対象の数値のみをハイライトします。</em>
</p>

---

## 🛡️ Security & Privacy (設計思想)

本ツールは、内部告発や機密文書の監査を想定し、**徹底的な「ローカル完結」**にこだわって設計されています。

### 1. No Server Upload (完全ローカル処理)
アップロードされたPDFは、**インターネット上のサーバーには一切送信されません。**
全ての解析処理は、ブラウザ内の JavaScript (PDF.js) と Python (PyScript) だけで行われます。
機密性の高い内部文書や、まだ公開されていないドラフト版も、安心して監査可能です。

### 2. Auto-Redaction (自動黒塗り機能)
著作権保護およびノイズ除去のため、監査に関係のないテキスト行は自動的に `░░░░░` で**黒塗り（Redact）**されます。
*   **メリット1:** 小説などを読み込ませても「解読不能」になるため、違法な自炊ビューワーとして悪用されるのを防ぎます。
*   **メリット2:** 監査官は「色がついた数字」を探すことだけに集中できます。

---

## 🎮 How to Use

1.  **Select File:** 監査したいPDFファイル（決算書、事業計画書など）を選択またはドロップします。
2.  **Tap Numbers:**
    *   **<span style="color:#ffd700">黄色い数字</span>:** 金額（予算）の候補です。タップして確定します。
    *   **<span style="color:#00ffff">青い数字</span>:** 人数（利用者・対象者）の候補です。タップして確定します。
3.  **Verdict:** 右パネルに **$D_{index}$ (歪み指数)** と判定結果（`SAFE` / `SCAM`）が即座に表示されます。
4.  **Export:** `EXPORT .MD` を押すと、監査レポートをMarkdown形式でダウンロードできます。

---

## 📐 The Logic (SBCM Audit)

本ツールは、抽出された数値を以下のSBCM公式に当てはめて判定します。

$$ D_{index} = \frac{I_{budget}}{I_{coverage}} = \frac{(\text{Budget} / 30\text{M})}{(\text{Users} / 72,000)} $$

*   **基準:** 予算3,000万円・利用者7.2万人を「標準ブロック（係数1.0）」として正規化。
*   **判定:** $D_{index} > 10.0$ で **「異常な高コスト（SCAM）」** と判定。

---

## 🛠️ Tech Stack

*   **Frontend:** HTML5 / CSS3 (JetBrains Mono)
*   **Engine:** [PyScript](https://pyscript.net/) (Python in Browser)
*   **PDF Core:** [Mozilla PDF.js](https://mozilla.github.io/pdf.js/)
*   **Logic:** Regular Expressions (Regex) for Japanese numerical notation extraction.

---

## ⚠️ Disclaimer

*   本ツールは、ドキュメント内の数値の妥当性を機械的に計算するものであり、その事業の社会的意義を否定するものではありません。
*   抽出精度はPDFの作成方法（OCRの有無など）に依存します。画像化されたPDFは読み取れません。

---
<p align="center">
  <small>© 2025 SBCM Alliance. Administrative Forensics Division.</small>
</p>
