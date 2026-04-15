# 医療ガイドラインにおけるRAG手法の比較検証：因果推論アプローチによるチャンク戦略の再考

## 📌 プロジェクト概要 (Overview)
本プロジェクトは、医療領域（食物アレルギー診療ガイドライン）に特化したQAシステムにおいて、**検索精度と回答品質を向上させる最適なRAG（Retrieval-Augmented Generation）のチャンク戦略**を特定するための比較検証です。

最新のLLMを用いた自動評価（LLM-as-a-Judge）フレームワークである「Ragas」を活用し、標準的なベースラインRAGとAdvanced RAG（Sentence Window Retrieval）の精度を定量的に比較。因果推論アプローチ（平均処置効果: ATEの測定）を用いて、統計的妥当性とビジネス導入時の費用対効果（ROI）を考察しています。

**詳細な実験設計・統計結果・ビジネス的考察については、同梱のPDFレポートをご参照ください。**
👉 [`医療ガイドラインにおけるRAG手法の比較検証：因果推論アプローチによるチャンク戦略の再考.pdf`](./医療ガイドラインにおけるRAG手法の比較検証：因果推論アプローチによるチャンク戦略の再考.pdf)

## 💡 検証のハイライト (Key Highlights)
- **医療ドメインの課題解決**: ハルシネーションが許されない医療ガイドラインにおいて、最適なRAGアーキテクチャを検証。
- **統計的アプローチ**: 単純なスコア比較ではなく、対応のあるt検定や効果量（Cohen's d）を用いた厳密な効果測定。
- **因果推論の前提考慮**: SUTVA（相互干渉の不在）を満たすステートレスなAPI評価設計。
- **ROIに基づくアーキテクチャ選定**: 複雑な手法の優位性が確認できなかった結果から、運用コストを考慮し「ベースラインRAGの採用」という実用的な意思決定を導出。

## 📂 リポジトリ構成 (Repository Structure)
```text
.
├── 医療ガイドラインにおけるRAG手法の比較検証：因果推論アプローチによるチャンク戦略の再考.pdf  # 報告書（Executive Summary & Discussion）
├── med_rag_evaluation.ipynb               # 評価パイプラインの実装コード（Jupyter Notebook）
└── README.md
```

## 🛠️ 技術スタックと必要パッケージ (Tech Stack & Dependencies)
本検証は以下の技術スタックを用いて実装されています。

- **Language**: Python 3.x
- **LLM / Embedding**: Google Gemini 2.5 Flash / Gemini Embedding 2 Preview
- **RAG Framework**: LlamaIndex
- **Evaluation**: Ragas (LLM-as-a-Judge)
- **Data Science**: pandas, SciPy, Seaborn

**【主要な依存ライブラリ】**
```text
llama-index
ragas
google-genai
pandas
scipy
seaborn
matplotlib
```
*(※ノートブックの最初のセルにて `!pip install` で自動インストールされるよう設定しています)*

## 🚀 実行手順 (How to Run)
本検証コードは **Google Colab環境** での実行を前提としています。
（※APIキーの安全な読み込みにColabのシークレット機能を使用しているため、ローカル環境では `google.colab` のImportErrorが発生します）

1. 本リポジトリの `med_rag_evaluation.ipynb` を手元のPCにダウンロードします。
2. [Google Colaboratory](https://colab.research.google.com/) を開き、「アップロード」タブから先ほどのノートブックを読み込みます。
3. Colab画面左側の「鍵マーク（シークレット）」をクリックし、以下の設定でAPIキーを登録してください。
   - 名前: `GEMINI_API_KEY`
   - 値: ご自身のGemini APIキー
   - **「ノートブックからのアクセスを許可」にチェックを入れる**
4. ノートブックを開き、上から順にセルを実行してください（必要なパッケージは最初のセルでインストールされます）。

## 📝 開発プロセスについて (Note on AI Assistance)
本検証の実装にあたっては、開発生産性の向上のため生成AIを活用していますが、検証アーキテクチャの設計、因果推論の前提（SUTVA等）に基づく評価パイプラインの構築、および統計処理のロジック検証は全て手動で厳密なレビューを行っています。
