## Step 2　Dependabot アラートを有効にして確認する

アラートは、使用中のパッケージに既知の脆弱性が見つかったことを知らせます。告知では影響範囲、修正済みバージョン、回避策、参考情報を確認できます。

1. [GitHub Advisory Database](https://github.com/advisories) で `follow-redirects` を検索し、告知を1件開いて内容を読みます。
2. **Settings** → **Advanced Security** で **Dependabot alerts** を有効にし、約60秒待ちます。
3. **Security** タブの **Dependabot** を開き、`Prototype Pollution in minimist` を選びます。
4. **Create Dependabot security update** を選びます。PR ができたら **Review security update** を開き、**Files changed** で差分を確認してから **Conversation** でマージします。

[原文](https://github.com/skills/secure-repository-supply-chain/blob/main/.github/steps/2-dependabot-alerts.md)
