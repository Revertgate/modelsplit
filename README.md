# modelsplit

A task board for Claude Code. It splits work into cards, gives each card to a small worker that
loads only the tools it needs, and accepts a card only when your project's checks pass, including
Revertgate's revert check. Included with every Revertgate plan.

## Install

1. Download the bundle for your system from the latest release and unpack it.
2. Register it with Claude Code, then install it in the repository you want to use it in:

```bash
claude plugin marketplace add <path to the unpacked folder>
cd <your repository>
claude plugin install modelsplit@modelsplit-local --scope local
```

3. See it work without spending anything:

```bash
<path to the unpacked folder>/plugin/bin/modelsplit board demo
```

Built for Windows (x64), Linux (x64) and macOS (Apple Silicon and Intel).

The macOS binaries are not signed by Apple. After unpacking, clear the download flag once, or
macOS will refuse to run them:

```bash
xattr -dr com.apple.quarantine <path to the unpacked folder>
```

## Use

```bash
modelsplit board add --title "Add slugify" "Add a slugify function with tests in tests/slugify.rs"
modelsplit board run next
modelsplit serve                     # the local dashboard at http://127.0.0.1:7317/
modelsplit context search how do I deploy
```

With a key: `modelsplit board plan "<goal>"` turns a goal into cards, `modelsplit board run all`
runs the whole board, and `modelsplit board resume` prints where a project stands.

## Free and paid

- **Free:** the demo, lean workers, adding and running single cards, the board and cost views, the
  context engine, and the dashboard.
- **With a Revertgate key** (`REVERTGATE_LICENSE_KEY`): board plan, run all, resume, and traces in
  the dashboard. One subscription covers Revertgate and modelsplit.

## What we measured

On Claude Opus, in our own single runs: across ten small single-function tasks, the board cost 5.7
times less than a normal Claude Code session; on one four-card project it cost $0.46 against $0.81.
Both passed the same hidden tests. Your results will depend on your setup and your work.

## Privacy

modelsplit runs on your machine with your own Claude Code login. The only network call it makes
itself is the licence check, which sends your key to the store. The dashboard listens on
127.0.0.1 only.
