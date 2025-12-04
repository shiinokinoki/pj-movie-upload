# TikTok動画アップロード PoC

## セットアップ

### 1. 環境変数の設定

`env.example` をコピーして `.env` を作成し、TikTok APIの認証情報を設定してください。

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

### 3. TikTok for Developersでの設定

1. [TikTok for Developers](https://developers.tiktok.com/) でアプリを作成
2. 必要な権限（Content Posting API等）を申請
3. クライアントキーとシークレットを取得
4. `.env` に設定

## 実行方法

（今後、auth.py と upload.py を作成後に追記）

