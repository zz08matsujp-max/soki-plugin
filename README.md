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
| **Skill: `import-notes`** | Read an existing folder of Markdown notes and seed SOKI with the due dates and unfinished items in them |
| **Skill: `handover`** | Build a handover document out of what SOKI remembers, for whoever picks the work up next |
| **`SETUP.md`** | First-run connection guide |

## Installing

This repository is its own marketplace, so two lines are enough:

```
/plugin marketplace add zz08matsujp-max/soki-plugin
/plugin install soki-memory@soki
```

Works in Claude Code and in Cowork.

## Setting up

After installing there is nothing else to install and no key to paste. The first
time a tool is used, a browser opens at `mcp.kitemir.jp` for sign-in, and the
connection is remembered. See [SETUP.md](SETUP.md).

### Reading your existing notes

SOKI only knows what has been said to it, so a new account has nothing to hand
back. If you already keep notes, say **"ノートを読ませたい"** or *"import my
notes"* in the conversation. The `import-notes` skill asks which folder, reads
`.md` / `.markdown` / `.txt`, and shows at most 20 candidates — dates that have
not passed, and lines still unfinished. **You pick which ones to keep**; nothing
is written to SOKI before that.

Two things worth knowing up front:

- It reads only **dates and unfinished lines.** Prose, ideas and reference
  material stay in your notes. SOKI is not a second copy of the vault.
- It is a **one-off import.** Dates you write in your notes afterwards do not
  reach SOKI until you import again.

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
- **スキル `import-notes`** — 手元のノートを読んで、期日と未完了だけを SOKI に入れる
- **スキル `handover`** — 記憶から引き継ぎ書を組み立てる
- **`SETUP.md`** — 初回接続の手引き

### 入れ方

このリポジトリ自体がマーケットプレイスなので、2行で入ります。

```
/plugin marketplace add zz08matsujp-max/soki-plugin
/plugin install soki-memory@soki
```

Claude Code でも Cowork でも同じです。

### 導入

入れたあとは、インストールするものも貼り付ける鍵もありません。最初にツールを
使ったときにブラウザが開くので、そこで登録またはログインしてください。以後は
覚えています。

### 手元のノートを読ませる

SOKI は話されたことしか知らないので、作りたてのアカウントは何も返しません。
すでにノートを溜めているなら、会話の中で **「ノートを読ませたい」** と言って
ください。`import-notes` スキルが**どのフォルダかを尋ね**、`.md` / `.markdown` /
`.txt` を読んで、候補を最大20件ならべます。**どれを入れるかは本人が選びます。**
選ぶ前に SOKI へ書き込むことはありません。

先に知っておいていただきたいことが2つあります。

- 取り込むのは **期日と「終わっていない行」だけ**です。散文・思想・資料はノートに
  残ります。SOKI は vault の複製ではありません。
- **取り込みは一度きり**です。その後ノートに書き足した期日は、もう一度取り込むまで
  SOKI に入りません。

⚠️ **AI 自身の記憶機能とは併用できません。** 互いを知らない記憶が2つあると、
食い違ったことを言い出します。どちらか一方にしてください。

---

Operated by マインドシード研究所 / Mind Seed Research Institute — <https://pyol.net/>
