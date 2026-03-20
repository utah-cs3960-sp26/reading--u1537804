## How was the session spawned?

The operator runs a single bash script once. It's an infinite `while true` loop. Claude doesn't launch itself and doesn't stop on its own. Each pass through the loop spawns one complete Claude Code session, and when that session exits, the loop immediately starts the next one.

## What commands ran before Claude started?

Three things happen in the shell before Claude is started: the current git commit hash is captured, a per-session log file path is constructed from that hash, and a fresh Docker container is made with the upstream bare git repo mounted inside it. Only then does the command `claude --dangerously-skip-permissions -p "$(cat AGENT_PROMPT.md)"` run.

## How did each VM interact with the system, and what was in it?

Each VM held the bare upstream git repo at `/upstream` and Claude's local working clone at `/workspace`. The VM had no internet access and used only the Rust standard library. Interaction with the shared system worked through git: Claude would clone from upstream, claim a task lock, do its work, then pull + merge + push back to upstream before releasing the lock. Up to 16 of these containers ran simultaneously, each picking different tasks through the locking mechanism.

## What did Claude do besides write code?

From what I understand, there is a bit of coordination work. Reading and updating READMEs and progress files to orient itself in each fresh container, choosing which task to tackle next, maintaining a running doc of failed approaches when stuck on a bug, managing the git locking/merging protocol to avoid stomping on other agents, and resolving merge conflicts. In one session, it also accidentally ran `pkill -9 bash` which killed itself and ending that loop iteration early.
