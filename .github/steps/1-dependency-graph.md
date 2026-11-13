## Step 1　依存関係グラフを確認する

依存関係グラフには、リポジトリが使うパッケージや、そのリポジトリに依存するパッケージが表示されます。情報はマニフェストやロックファイルなどから集められます。

1. **Settings** → **Advanced Security** で **Dependency graph** が有効になっていることを確認します。新しい公開リポジトリでは通常有効です。
2. **Code** から `code/src/AttendeeSite/package-lock.json` を開きます。演習用の依存関係として、下の指定内容を `dependencies` の末尾に追加し、`main` にコミットします。追加位置は最後の2つの閉じ波括弧の手前です。
3. **Insights** → **Dependency graph** → **Dependencies** を開き、`follow-redirects` を探します。

### 原文のコマンド・入力例

```json
,
"follow-redirects": {
  "version": "1.14.1",
  "resolved": "https://registry.npmjs.org/follow-redirects/-/follow-redirects-1.14.1.tgz",
  "integrity": "sha512-HWqDgT7ZEkqRzBvc2s64vSZ/hfOceEol3ac/7tKwzuvEyWx3/4UegXh5oBOIotkGsObyk3xznnSRVADBgWSQVg=="
}
```

### 画面での確認

- 自分のリポジトリ上部の **Settings** を開きます。左側のセキュリティ設定で **Advanced Security** を選び、**Dependency graph** の状態を確認します。
- コミット後は上部の **Insights** を開き、左側の **Dependency graph** を選びます。**Dependencies** に対象パッケージが表示されるまで再読み込みします。

[原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/1-dependency-graph.md)
