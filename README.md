# 演習08　ソフトウェアサプライチェーンを保護する

演習用リポジトリで依存関係グラフと Dependabot を使い、アラートを確認し、修正済みのバージョンへ更新します。目安は1時間未満です。

## 始め方

1. 講師から案内された日本語版テンプレートの GitHub ページを開きます。**Use this template** → **Create a new repository** を選び、**Owner** と公開範囲を確認して **Create repository** を選びます。
2. 20秒ほど待って再読み込みします。自分のコピーの **Issues** または **README** に出る案内に合わせて、この資料の同じ番号を開きます。
3. ファイル名、ブランチ名、コード、指定コメントは掲載どおりに入力します。操作後は GitHub 上で次の案内を確認します。

[GitHub Skills の原文 README](https://github.com/skills/secure-repository-supply-chain) · [教材のライセンス](LICENSE)

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

[このステップの原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/1-dependency-graph.md)

## Step 2　Dependabot アラートを有効にして確認する

アラートは、使用中のパッケージに既知の脆弱性が見つかったことを知らせます。告知では影響範囲、修正済みバージョン、回避策、参考情報を確認できます。

1. [GitHub Advisory Database](https://github.com/advisories) で `follow-redirects` を検索し、告知を1件開いて内容を読みます。
2. **Settings** → **Advanced Security** で **Dependabot alerts** を有効にし、約60秒待ちます。
3. **Security** タブの **Dependabot** を開き、`Prototype Pollution in minimist` を選びます。
4. **Create Dependabot security update** を選びます。PR ができたら **Review security update** を開き、**Files changed** で差分を確認してから **Conversation** でマージします。

[このステップの原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/2-dependabot-alerts.md)

## Step 3　Dependabot のセキュリティ更新を自動化する

セキュリティ更新を有効にすると、Dependabot は対象のアラートを解消する PR を自動で作成します。

1. **Settings** → **Advanced Security** で **Dependabot security updates** を有効にします。30〜60秒ほど待ちます。
2. **Pull requests** で `axios` を更新する PR を探し、差分を確認してマージします。

[このステップの原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/3-dependabot-security.md)

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

[このステップの原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/4-dependabot-versions.md)

## 振り返り

依存関係グラフで使用中のパッケージを確認し、Dependabot アラートを確認しました。修正用 PR と定期的なバージョン更新の設定を使いました。

[このステップの原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/x-review.md)
