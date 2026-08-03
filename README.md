# したくアプリ

3歳の子ども(自閉症・ADHD)向けの「したく(身支度)」支援アプリ。絵文字とひらがなの大きなボタンで「やる」→「できた」の2段階をタップし、効果音・お祝い演出・BGMでやる気を後押しする。

公開URL: https://komekami148.github.io/shitaku-app/

## 構成

- **単一ファイルの静的サイト**: `index.html` 1つだけで完結(HTML/CSS/JS全部入り、ビルド不要、外部ライブラリ・音声ファイルなし)
- 効果音・BGMはすべて実行時にWeb Audio APIで生成
- データ(項目・チェック状態・音量・音の好み)は各端末のブラウザの `localStorage` に保存(サーバー側には何も送信しない)
- GitHub Pages がこのリポジトリの `master` ブランチ直下をそのまま配信している(pushすると自動で再ビルド・数十秒で反映)

## 開発の進め方

1. `index.html` を直接編集する(このファイルが唯一の実体。コピーは不要)
2. ブラウザで `index.html` を直接開けばそのまま動作確認できる
3. 変更をコミットして `master` に push すれば、GitHub Pages に自動反映される

```bash
git add index.html
git commit -m "変更内容"
git push
```

## 新しいマシンで開発を再開する場合(例: Mac)

1. Git をインストール(Mac は Xcode Command Line Tools に同梱。未導入なら `xcode-select --install`)
2. GitHub CLI をインストール: `brew install gh`
3. GitHub にログイン: `gh auth login`(Windows側の認証情報は引き継がれないので、新しい端末で1回だけ再認証が必要)
4. リポジトリを取得: `git clone https://github.com/komekami148/shitaku-app.git`

以上で `index.html` を編集 → commit → push、という同じ流れで続けられる。

補足: 子どもが使う端末(スマホ・タブレット)側の「今日どこまでチェックしたか」は端末のブラウザに保存されているだけなので、開発環境をどこに移しても影響しない(逆に、開発機を変えても子ども用端末のデータは消えない)。
