# YouTube動画アップロード PoC

## セットアップ

### 1. 環境変数の設定

`env.example` をコピーして `.env` を作成し、YouTube APIの認証情報を設定してください。

```bash
cp ../../env.example .env
# .envファイルを編集して認証情報を入力
```

### 2. 依存関係のインストール

```bash
# プロジェクトルートから実行
uv venv
source .venv/bin/activate  # または uv run
uv pip install -r requirements.txt
```

### 3. Google Cloud Consoleでの設定

1. [Google Cloud Console](https://console.cloud.google.com/) でプロジェクトを作成
2. YouTube Data API v3 を有効化
3. OAuth 2.0 認証情報を作成（アプリケーションの種類: ウェブアプリケーション）
4. 承認済みのリダイレクト URI に `http://localhost:8080/oauth2callback` を追加
5. クライアントIDとクライアントシークレットを `.env` に設定

## 実行方法

（今後、auth.py と upload.py を作成後に追記）

