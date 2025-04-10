# GitHub Actions Runner Sample (Aリポジトリ)

このリポジトリは、外部リポジトリに定義されたカスタム GitHub Action を実行するサンプルです。

## 📌 概要
- Bリポジトリ（[`gh-actions-custom-action-sample`](https://github.com/rendya2501/gh-actions-custom-action-sample)）のカスタムアクションを呼び出します。
- `with:` を使ってメッセージを渡し、そのメッセージをログに表示します。

## 📂 リポジトリ構成

```
gh-actions-runner-sample/
└── .github/
    └── workflows/
        └── run-custom-action.yml # Workflow definition
```

## 🚀 使用方法

`.github/workflows/run-custom-action.yml` を作成し、以下のように設定します。

```yaml
name: Run Custom Action

on:
  workflow_dispatch:

jobs:
  test_custom_action:
    runs-on: ubuntu-latest
    steps:
      - name: Execute B repository custom action
        id: custom_action
        uses: rendya2501/gh-actions-custom-action-sample@main
        with:
          message: "A repository Payload" #送信メッセージ

      - name: Echo the result from B repository
        run: |
          echo "Received script output: ${{ steps.custom_action.outputs.script_result }}"
          echo "Received echo output: ${{ steps.custom_action.outputs.echo_result }}"
          echo "Received csharp output: ${{ steps.custom_action.outputs.csharp_result }}"
```

## ✅ 実行結果
ワークフロー実行後、ログには以下のように表示されます。

![image](https://github.com/user-attachments/assets/30019a3d-23c9-43d7-a86c-7ed1456d1148)
