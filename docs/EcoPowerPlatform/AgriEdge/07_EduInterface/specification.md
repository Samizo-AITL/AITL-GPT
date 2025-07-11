# 教育用PoCDK連携・GUIインタフェース設計仕様書  
**Sky-HyEV AgriEdge Model v1.0**

---

## 1. 概要

本モジュールは、Sky-HyEV AgriEdgeモデルを用いた教育用途において、PoCDK（Proof of Concept Development Kit）とのインタフェースを確立し、センサデータの可視化、AI判断の追跡、GUIを介した操作・評価を可能とする。

---

## 2. 教育PoC構成イメージ

[実機：AgriEdge Model]
├─▶ センサ入力、AI判断、行動出力
└─▶ [PoCDK] ─▶ [GUI Viewer (PC/タブレット)]

- 実機の各モジュールとPoCDK評価ボードをUSBまたはUARTで接続
- PoCDK経由でデータロギング、パラメータ設定、リアルタイム制御可能
- GUIはWebベースまたはローカルアプリ型（HTML5／Python系）

---

## 3. PoCDK対応インタフェース仕様

| 接続種別   | 内容                              |
|------------|-----------------------------------|
| UART       | AI判断結果、センサデータの送信    |
| USB-CDC    | 設定コマンド送信、ログ取得        |
| GPIO       | 簡易的な動作トリガ、LED制御       |
| I²Cスレーブ| GUI→モジュールへの設定書き込み    |

---

## 4. GUI連携機能一覧

| 機能カテゴリ | 機能名                       | 備考                       |
|--------------|------------------------------|----------------------------|
| センサ表示    | 温湿度、土壌水分、光量、CO₂   | リアルタイムグラフ表示     |
| AI判断表示   | 現在のAITL判断ルール・出力    | 条件→動作ログ可視化       |
| パラメータ変更 | AITLルールの切替／閾値変更    | GUIから即時反映可能       |
| シミュレーション| 仮想センサ注入／異常テスト    | 実データ不要の教育用      |
| 記録・出力   | ログCSV保存、スクリーンショット| 評価・報告用               |

---

## 5. AITLとの接続性

- GUIから **AITLルールの一部変更／読み出し／状態表示** が可能
- 例：

変更前: IF 土壌水分 < 30 THEN 灌水
GUIで変更 → IF 土壌水分 < 40 THEN 灌水
→ 即時反映・ログ保存

- ルールベースAIの学習補助ツールとして活用可

---

## 6. 教育カリキュラム支援機能

- モジュール別ON/OFF／切替実験（電源／通信／センサ）
- GUI上での手順ガイド（ステップ表示）
- 評価フォーム連携（Google FormsやLMS連携）

---

## 7. 対応機材／互換性

| 項目             | 内容                                |
|------------------|-------------------------------------|
| 接続対象         | PoCDK評価ボード（AITL SoC搭載）     |
| GUIプラットフォーム | Windows / macOS / iPadOS / ChromeOS |
| データ形式       | JSON, CSV, スナップPNG              |
| 通信              | USBシリアル／UART／I²C              |

---

## 8. 拡張性

- AITL GUI Editor連携（ルール生成補助）
- クラウド連携（センサログ送信／教師データ生成）
- edusemi-plus教材との接続（AITLルール演習）

---

## 9. 補足・備考

- PoCDK評価環境での基本動作が確認された後、実機応用へ展開可能
- 本GUIは他のモデル（Military, DisasterResponse等）への転用が可能

---

*Drafted: 2025-06-27*
