# keiba-horse-profile-extractor

競馬予想用のデータ取得・整理コードです。netkeiba からレース情報を取得し、分析用の JSONL などを作成します。

## ファイル概要

| ファイル名 | 処理概要 | ユーザーの準備物 | 出力内容 |
|---|---|---|---|
| `netkeiba_search_detail_polite.py` | netkeiba の検索結果URLから対象レースの `race_id` とレース概要を取得する | netkeiba のレース検索結果URL（`SEARCH_URLS` に設定） | `RACE_ID_LIST`、レース概要一覧 |
| `netkeiba_scraper_top_config.py` | `race_id` をもとに出馬表、過去成績、血統、対戦表、過去10年傾向を取得する | `RACE_ID_LIST`、Google Drive の出力先 `OUTPUT_DIR` | `出馬表.jsonl`、`対戦表.jsonl`、`過去10年傾向.jsonl`、必要に応じて対戦表CSV |
| 分析用プロンプト / 予想用手順書 | 取得済みデータと補助CSVを使ってレース分析・予想を行う | `出馬表.jsonl`、`対戦表.jsonl`、`過去10年傾向.jsonl`、`コース特徴.csv`、騎手情報CSV | レース分析、展開予想、各馬評価、最終候補 |

## 基本的な流れ

1. `netkeiba_search_detail_polite.py` で対象レースの `race_id` を取得する。
2. `netkeiba_scraper_top_config.py` の `RACE_ID_LIST` に `race_id` を設定して、分析用 JSONL を出力する。
3. 出力された JSONL と補助 CSV を使って、分析用プロンプトで予想を行う。

## 注意点

- スクレイピングを行うため、アクセス間隔を空けて実行してください。
- サイト構造が変わると、データが正しく取得できない場合があります。
- 取得データは分析補助用です。最終判断では、当日の馬場、馬体重、出走取消、オッズなども確認してください。
