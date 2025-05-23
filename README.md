# React × Rails(API) × DevContainer テンプレート

このリポジトリは、**React（Vite）+ Rails（API モード）+ PostgreSQL** によるモダンなフルスタック開発環境を、\*\*VS Code DevContainer（Docker）\*\*で快適に構築・運用できるテンプレートです。

---

## ディレクトリ構成

```
rails-react/
├── backend/                 # Rails API
│   ├── .devcontainer/       # Rails 用 DevContainer
│   ├── Dockerfile
│   └── ...
├── frontend/                # React (Vite)
│   ├── .devcontainer/       # React 用 DevContainer
│   ├── Dockerfile
│   └── ...
├── docker-compose.yml       # Rails・React・DB をまとめて起動
├── .github/workflows/       # CI 定義 (RSpec, Vitest など)
└── .gitignore               # .env などを除外
```

## 特長

- **VS Code DevContainer 対応**

  - バックエンド（Rails）、フロントエンド（React）、DB（PostgreSQL）がワンクリックで起動します。

- **Docker マルチサービス構成**

  - `docker-compose` で各サービスを個別コンテナで管理。ホットリロードにも対応。

- **API × SPA 分離構成**

  - バックエンドとフロントエンドを完全に分離して開発・デプロイが可能です。

- **ボリューム管理/ 依存キャッシュ**

  - Gem や node_modules のインストールを高速化。

---

## セットアップ（ローカル開発）

### 1. リポジトリをクローン

```bash
git clone https://github.com/your-username/react-rails-devcontainer.git
cd rails-react
```

### 2. VS Code で DevContainer を開く

- VS Code の「Dev Containers」拡張機能をインストールしてください。
- プロジェクトルートで「Open in Container」を選択。
- backend のコンテナを開きたい場合は `code ./backend`、frontend の場合は `code ./frontend`でそれぞれ開いてください。
- 左下のボタンを押すか、devcontainer.json を開くと reopen するか聞かれるので、reopen を選択してください。
- 詳しくは最後の DevContainer の使い方で確認してください

### 3. 初期化コマンド（初回のみ）

#### Rails (backend)

DevContainer 内ターミナルで：

```bash
rails new . --api -d postgresql
```

#### React (frontend)

DevContainer 内ターミナルで：

```bash
npm create vite@latest .
```

### 4. サービスの起動・アクセス方法

#### Rails（API サーバー）

backend のコンテナを開いた状態で、以下のコマンドを実行します。

```bash
rails s
```

- アクセス: `http://localhost:3000`

#### React（Vite）

frontend のコンテナを開き、`package.json` の script に以下を追加：

```json
"scripts": {
  "dev": "vite --host" // --hostを追加
}
```

その後、以下コマンドを実行：

```bash
npm run dev
```

- アクセス: `http://localhost:5173`

---

## セキュリティ設定

- このテンプレートは `.env` ファイルにより、docker-compose.yml のデータベースのユーザー名やパスワードなどを記述しています。

- .env の内容は適宜変えてもらって構いません。

- `.env` には機密情報を含むため、必ず `.gitignore` に除外設定をしてください。

```bash
#.gitignore
.env
```

---

## 参考資料

- DevContainer の使い方：[https://railstutorial.jp/help#devcontainer](https://railstutorial.jp/help#devcontainer)

---

ご不明点や改善案があれば、Issue や PR でご連絡ください。
