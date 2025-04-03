# GitHub Actions Runner Sample

このリポジトリは、外部リポジトリに定義されたカスタム GitHub Action を実行するサンプルです。

## 📌 概要
- Bリポジトリ（[`gh-actions-custom-action-sample`](https://github.com/your-username/gh-actions-custom-action-sample)）のカスタムアクションを呼び出します。
- `with:` を使ってメッセージを渡し、そのメッセージをログに表示します。

## 🚀 使用方法

`.github/workflows/main.yml` を作成し、以下のように設定します。

```yaml
name: Run Custom Action

on:
  workflow_dispatch:

jobs:
  test_custom_action:
    runs-on: ubuntu-latest
    steps:
      - name: Use custom action with message
        uses: your-username/gh-actions-custom-action-sample@main
        with:
          message: "Hello from A repository!"
```

## ✅ 実行結果

GitHub Actions のログに以下のように表示されます。

```
Received message: Hello from A repository!
```

## 📂 リポジトリ構成

```
gh-actions-runner-sample/
└── .github/
    └── workflows/
        └── main.yml　# Workflow definition
```
