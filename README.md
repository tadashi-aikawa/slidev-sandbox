# Slidev Sandbox

Slidevのサンドボックスプロジェクト。新規スライドを作るときのコピー元テンプレートとして使う。

デモ(レイアウト・コンポーネントのショーケース): https://tadashi-aikawa.github.io/slidev-sandbox/

## 新規スライドの作り方

### 1. リポジトリ作成

1. GitHubの `Use this template` → `Create a new repository` で新規リポジトリを作成
    - リポジトリ名がそのまま公開URLのパスになる (`https://tadashi-aikawa.github.io/<リポジトリ名>/`)
2. cloneして起動確認

```bash
bun ci
bun dev
```

http://localhost:3030 にアクセスしてショーケースが表示されればOK。

### 2. 差し替えチェックリスト

- [ ] `slides.md` のheadmatter: `title` / `background` / `favicon`
- [ ] `slides.md` のheadmatter: `chapters`(章立て。`chapter-divider` レイアウトが参照する)
- [ ] `slides.md` のheadmatter: `themeConfig.primary`(メインカラーを変えるなら。あわせて `styles/index.css` の `:root` 変数も確認)
- [ ] `slides.md` の本文: ショーケース部分を削除し、カバー+Agendaだけ残して書き始める
- [ ] `public/attachments/`: サンプル素材(`cat-minerva.webp`, `colot.mp4`)を削除し、自分の素材を配置
- [ ] `og-image.png` を差し替え(不要なら削除)
- [ ] `README.md` をスライド用の内容に書き換え([slidev-sandbox](https://github.com/tadashi-aikawa/slidev-sandbox) へのリンクを残しておくと戻ってきやすい)

### 3. GitHub Pagesの有効化

1. リポジトリの `Settings` → `Pages` → `Source` を `GitHub Actions` に設定
2. mainにpushすれば自動でビルド・デプロイされる
    - ビルドの `--base` はリポジトリ名から自動注入されるので設定変更は不要

### 4. 書き方に迷ったら

- レイアウト・コンポーネントの使用例は [ショーケース](https://tadashi-aikawa.github.io/slidev-sandbox/) と本リポジトリの `slides.md` を見る
- 画像パスの書き方は使う場所(HTMLの `src` / frontmatter / Markdown / CSS)によって異なるので、ショーケースの該当スライドを参照

## バージョン方針

- 依存はすべて固定バージョン。**コピー先では更新しない**(このリポジトリで動作確認済みの構成をそのまま使うことを優先)
- Slidevのバージョンアップはこのリポジトリでのみ行い、ショーケースの表示確認とデプロイ確認をしてから、次に作るスライドへ反映する

## 開発コマンド

### インストール

```bash
bun ci
```

### 起動

```bash
bun dev
```

http://localhost:3030 にアクセス。

### ビルド

```bash
bun run build
```

確認は

```bash
bun vite preview
```

## 編集

Neovimを使っているなら [slidev-preview.nvim](https://github.com/tadashi-aikawa/slidev-preview.nvim) がオススメ。

## デプロイ先

https://tadashi-aikawa.github.io/slidev-sandbox/
