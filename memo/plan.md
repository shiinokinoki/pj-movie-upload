# SNS動画連携機能 調査・検証計画書

## 1. 目的
Webアプリケーション（Pythonバックエンド）において、ユーザーが作成した動画を各SNSプラットフォームへワンクリックで投稿（自身のユーザーアカウントへ連携投稿）する機能を実現するための技術的・法的要件を調査し、PoC（概念実証）を行う。

## 2. 対象プラットフォーム
優先度順に実施する。

1.  **High**: YouTube, TikTok
2.  **Mid**: X (旧Twitter), Instagram, Facebook

## 3. 調査・検証項目
各プラットフォームについて、`memo/objective.md` に基づき以下をアウトプットする。

1.  **投稿フローのステップ・スクリプト**: PythonによるOAuth認証からアップロードまでのコード例。
2.  **アカウント紐付け方法**: ユーザーのSNSアカウントをアプリに連携するOAuthスコープとフロー。
3.  **動作検証結果**: 実際のAPIレスポンス、成功/失敗の挙動。
4.  **制約／留意事項**: ファイルサイズ、形式、レートリミット、トークン有効期限など。
5.  **API法人利用・法務**: 商用利用の可否、審査プロセス（YouTube Audit等）、利用規約上の注意点。
6.  **価格**: API利用料金、クオータ制限。

## 4. 技術スタック・前提
*   **Frontend**: Webブラウザ
*   **Backend**: Python
*   **UX**: 「A. 完全自動投稿」を目標とする。API制約等で不可能な場合は「B. シェア機能」を検討。
*   **Auth**: エンドユーザーごとのOAuth認証トークンをサーバーサイド（Python）で管理し、APIをコールする想定。

## 5. 進め方 (フェーズ分け)

### Phase 1: 計画と環境準備 [Current]
*   検証計画の策定
*   PoC用Python環境のセットアップ（必要なライブラリの選定）

### Phase 2: YouTube & TikTok (優先)
*   **YouTube**:
    *   Google Cloud Consoleでの設定項目洗い出し
    *   Data API v3 (`youtube.upload`) の調査。特に「Audit（監査）」と「Quota（割当）」の厳しさについて重点調査。
    *   Python (`google-auth`, `google-api-python-client`) によるアップロードPoC。
*   **TikTok**:
    *   TikTok for Developers (Content Posting API) の仕様調査。
    *   Webからの権限付与フロー (Login Kit / Share to TikTok) の確認。
    *   PythonによるPoC。

### Phase 3: X & Meta (Instagram/Facebook)
*   **X**:
    *   API v2 (Basic/Pro) の動画投稿仕様確認。コスト要件（Free枠では不可の可能性が高い）。
    *   Python (`tweepy` 等) によるPoC。
*   **Instagram**:
    *   Instagram Graph API (Content Publishing) の調査。
    *   **制約確認**: ビジネス/クリエイターアカウント必須か？ 個人アカウントへの投稿可否。
*   **Facebook**:
    *   Graph API (Video API) の調査。

### Phase 4: レポート作成
*   調査結果を `memo/` 配下にプラットフォームごとの詳細レポートとしてドキュメント化。
*   PoCコードを `poc/` ディレクトリ等に整理して格納。

