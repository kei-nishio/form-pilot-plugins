# form-pilot-plugins

form-pilot を Claude Code / Codex から使うためのプラグインです。
入れると、AI が form-pilot の MCP サーバー（`https://form-pilot.plutoid.jp/mcp`）につながります。

- API キーは不要です。初回だけ Google でログインします
- ログインでは **form-pilot に登録した Google アカウント** を選んでください。登録していないアカウントでは使えません

## Claude Code で使う

ターミナルで次の 2 行を実行します。

```bash
claude plugin marketplace add kei-nishio/form-pilot-plugins
claude plugin install form-pilot@form-pilot-plugins
```

続けて Google ログインをします。

```bash
claude mcp login plugin:form-pilot:form-pilot
```

ブラウザで Google のログイン画面が開きます。form-pilot に登録した Google アカウントを選び、「許可する」を押してください。
ターミナルでログインしたくない場合は、Claude Code を起動して `/mcp` を開き、`plugin:form-pilot:form-pilot` を選んで「Authenticate」でも同じです。

起動中の Claude Code には、再起動するか `/reload-plugins` を実行すると反映されます。

## Codex で使う

ターミナルで次の 2 行を実行します。

```bash
codex plugin marketplace add kei-nishio/form-pilot-plugins
codex plugin add form-pilot@form-pilot-plugins
```

続けて Google ログインをします。

```bash
codex mcp login form-pilot
```

ブラウザで Google のログイン画面が開きます。form-pilot に登録した Google アカウントを選び、「許可する」を押してください。

## 使い方

AI に「手元で営業したリストを form-pilot に登録したい」と頼み、リストを渡してください。
AI はまず振り分け結果（新規・登録済み・要確認など）を見せます。内容を確かめて了承すると登録されます。

## うまくいかない時

- 「ログインできない」「権限がない」と出る: form-pilot に登録した Google アカウントでログインし直してください（Claude Code は `/mcp` から、Codex は `codex mcp logout form-pilot` のあと `codex mcp login form-pilot`）
- 最新版にする: Claude Code は `claude plugin marketplace update form-pilot-plugins`、Codex は `codex plugin marketplace upgrade form-pilot-plugins`

## 削除する

```bash
# Claude Code
claude plugin uninstall form-pilot@form-pilot-plugins
claude plugin marketplace remove form-pilot-plugins

# Codex
codex plugin remove form-pilot@form-pilot-plugins
codex plugin marketplace remove form-pilot-plugins
```
