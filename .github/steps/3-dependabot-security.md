## Step 3　Dependabot のセキュリティ更新を自動化する

セキュリティ更新を有効にすると、Dependabot は対象のアラートを解消する PR を自動で作成します。

1. **Settings** → **Advanced Security** で **Dependabot security updates** を有効にします。30〜60秒ほど待ちます。
2. **Pull requests** で `axios` を更新する PR を探し、差分を確認してマージします。

   > 前の更新をマージすると、既存の PR が競合したり、Dependabot によって閉じられたりすることがあります。数分待って一覧を再読み込みし、新しく作られた PR を確認します。複数のパッケージをまとめて更新する PR でも、差分に `axios` の更新が含まれていれば対象です。

### 画面での確認

- **Dependabot security updates** は、**Settings** の左側にある **Advanced Security** の Dependabot 欄にあります。
- 更新 PR が表示されたら、上部の **Pull requests** からタイトルに `axios` が含まれるものを開きます。**Files changed** で対象を確認し、マージ後は **Merged** の表示を確かめます。

[原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/3-dependabot-security.md)
