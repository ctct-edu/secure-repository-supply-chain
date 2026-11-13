## Step 4　Dependabot で通常のバージョン更新を設定する

依存関係の構成が変わると、不要になった更新 PR は自動で閉じられる場合があります。バージョン更新を使うと、脆弱性対応とは別に、定期的な更新を提案できます。

1. **Settings** → **Advanced Security** で **Dependabot version updates** の **Configure** を選び、`dependabot.yml` を開きます。
2. 既存の `github-actions` の設定に、下の `nuget` の設定を追加します。`main` にコミットします。
3. GitHub Actions は毎月、`/code/` の .NET パッケージは毎週、更新が確認される設定になったことを読み取ります。

### 原文のコマンド・入力例

```yaml
version: 2
updates:
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "monthly"
  - package-ecosystem: "nuget"
    directory: "/code/"
    schedule:
      interval: "weekly"
```

### 画面での確認

- **Settings** → **Advanced Security** で **Dependabot version updates** の右側の **Configure** を選びます。
- コミット後、**Code** → `.github` → `dependabot.yml` を開き、`github-actions` と `nuget` の両方が `updates` の下に表示されることを確認します。

[原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/4-dependabot-versions.md)
