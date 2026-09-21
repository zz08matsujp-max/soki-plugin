# SOKI — personal memory that lives outside the AI

SOKI (想起, *sōki* — "recollection") is a hosted MCP server that remembers what
you told it and **brings it back on its own**, in whichever AI you are using.

Talk to ChatGPT today and Claude tomorrow; the memory stays with you, not with
the assistant. When a date gets close, SOKI says *"by the way…"*. When something
you said you would do is still open, it says *"come to think of it…"*. You never
have to ask it to remember, and you never have to ask it to recall.

- Site: <https://mcp.kitemir.jp/>
- Free while in beta.

## What is in this plugin

| | |
|---|---|
| **Connector** | `soki` — the hosted MCP server at `https://mcp.kitemir.jp/mcp` (streamable HTTP, OAuth 2.1) |
| **Skill: `handover`** | Build a handover document out of what SOKI remembers, for whoever picks the work up next |
| **`SETUP.md`** | First-run connection guide |

## Installing

**In Claude Code.** This repository is its own marketplace, so two lines are
enough:

```
/plugin marketplace add zz08matsujp-max/soki-plugin
/plugin install soki-memory@soki
```

**In Cowork.** Not yet. Cowork installs from the account's plugin catalogue,
which is fed by the Claude plugin directory, and the listing for this plugin is
still under review. Until it is approved, use Claude Code — or connect the MCP
server on its own (see below), which gives you the memory without the two
skills.

## Setting up

After installing there is nothing else to install and no key to paste. The first
time a tool is used, a browser opens at `mcp.kitemir.jp` for sign-in, and the
connection is remembered. See [SETUP.md](SETUP.md).

## What SOKI does that a notes file does not

- **It is outside the AI.** Switching assistants does not mean explaining
  yourself again.
- **It speaks first.** Deadlines and loose ends come back without being asked.
- **Memories have weight.** Things that change often fade quickly; things that
  do not, last. Old facts are not served up as though they were still certain.
- **It says "just to be sure".** When an answer rests on something SOKI knows,
  it adds one line naming that assumption instead of letting the answer stand
  unqualified.
- **Skills by name.** A phrasing that worked can be saved and called back by
  name later.
- **You can read all of it.** Everything stored is visible in plain language and
  exportable at any time.

## Please read this before installing

⚠️ **SOKI cannot be used alongside an AI's own built-in memory.** Two memories
that do not know about each other will contradict one another. Turn the built-in
memory off, or do not use SOKI.

⚠️ SOKI is in beta and run by one person. It is free today. Data can be exported
at any time.

---

## 日本語

SOKI（想起）は、**AI の外側**にあるあなた専用の記憶です。ChatGPT で話したことを
Claude が知っている。しかも、ただ覚えているだけではありません。予定が近づけば
「ところで」と切り出し、やり残しは「そういえば」と持ち出します。**覚えたことを、
向こうから返しに来る記憶**です。

- サイト: <https://mcp.kitemir.jp/>

### このプラグインに入っているもの

- **コネクタ `soki`** — `https://mcp.kitemir.jp/mcp`（streamable HTTP・OAuth 2.1）
- **スキル `handover`** — 記憶から引き継ぎ書を組み立てる
- **`SETUP.md`** — 初回接続の手引き

### 入れ方

**Claude Code の場合。** このリポジトリ自体がマーケットプレイスなので、2行で入ります。

```
/plugin marketplace add zz08matsujp-max/soki-plugin
/plugin install soki-memory@soki
```

**Cowork の場合。** まだ入れられません。Cowork はアカウントのプラグイン・カタログから
入れる仕組みで、そこへは Claude のプラグイン・ディレクトリ経由で載ります。
**このプラグインは現在そのディレクトリの審査中**です。承認されるまでは Claude Code を
お使いください。あるいは MCP サーバーだけを繋ぐこともできます（下記）。その場合、
記憶は使えますが、スキルは付きません。

### 導入

入れたあとは、インストールするものも貼り付ける鍵もありません。最初にツールを
使ったときにブラウザが開くので、そこで登録またはログインしてください。以後は
覚えています。

---

Operated by マインドシード研究所 / Mind Seed Research Institute — <https://pyol.net/>
