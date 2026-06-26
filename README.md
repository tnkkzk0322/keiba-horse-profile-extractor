| ファイル名 | 処理概要 | ユーザーの準備物 | 出力内容 |
|---|---|---|---|
| `推奨馬券.ipynb` | Numbersファイルの予想データを読み込み、券種・買い目ごとのROIや推奨馬券パターンを集計する | `/content/競馬分析.numbers`、対象シート名 `予想`、予算設定 | `yosou_extracted.json`、`ranking_result.json`、ROI集計CSV、散布図HTML |
| `競馬ID_結果抽出.ipynb` | netkeibaの検索結果URLからレースIDと過去レース結果・払戻情報を抽出する | netkeibaの検索結果URLを `SEARCH_URLS` に設定 | `RACE_ID_LIST`、レース結果一覧データ |
| `競馬データ抽出.ipynb` | `RACE_ID_LIST` のレースIDから出馬表、過去成績、血統、対戦表、過去10年傾向を取得する | `RACE_ID_LIST`、`OUTPUT_DIR`、Google Drive/Colab環境 | `出馬表.jsonl`、`対戦表.jsonl`、`過去10年傾向.jsonl` |
