# GitHub Actions Runner Sample

このリポジトリは、外部リポジトリに定義されたカスタム GitHub Action を実行するサンプルです。

## 📌 概要
- Bリポジトリ（[`gh-actions-custom-action-sample`](https://github.com/rendya2501/gh-actions-custom-action-sample)）のカスタムアクションを呼び出します。
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
      - name: Execute B repository custom action
        id: custom_action
        uses: rendya2501/gh-actions-custom-action-sample@main
        with:
          message: "Hello from A repository!"

      - name: Echo outputs
        run: |
          echo "script_result: ${{ steps.custom_action.outputs.script_result }}"
          echo "echo_result: ${{ steps.custom_action.outputs.echo_result }}"
```

## ✅ 実行結果
ワークフロー実行後、ログには以下のように表示されます。

```
Received message: Hello from A repository!
script_result: Script Processed: Hello from A repository!
echo_result: Echo Processed: Hello from A repository! (hogehoge)
```

![](https://file.notion.so/f/f/a7a37f0e-edd5-442d-949d-bd0b47b0b9d4/1e406882-c87b-442e-b5f3-83a7db937808/image.png?table=block&id=1cb4a91b-2eac-8009-ad60-ea90b4d476cf&spaceId=a7a37f0e-edd5-442d-949d-bd0b47b0b9d4&expirationTimestamp=1743811200000&signature=cQ10FNOI0KTrvqXLTRBpekO1q82zlAFQjrB71wxj2Do&downloadName=image.png)

## 📂 リポジトリ構成

```
gh-actions-runner-sample/
└── .github/
    └── workflows/
        └── run-custom-action.yml # Workflow definition
```
