# nk-evidence-audit

A [Claude Code](https://code.claude.com) skill. Turn "done, fixed, tested" into evidence a second agent judges.

Part of [nickkk-skills](https://github.com/NickkkLian/nickkk-skills) — skills that stop an AI coding agent's
"done, tested, safe" from being taken on faith.

## What it does

- `scripts/evidence.py run` captures a command's raw stdout/stderr/exit code with the cwd, git head, timestamps and hashes; `index` lists bundles; `verify` flags edited or incomplete ones.
- The auditor brief (`references/auditor-brief.md`) works as a subagent prompt: three verdicts, no fourth.
- The not-evidence table lists seventeen things that were once accepted as proof and were not.

The full procedure, the boundaries and where the rules came from are in [SKILL.md](SKILL.md).

## Install

Copy the folder into your skills directory (the skill is the repository root):

```bash
git clone https://github.com/NickkkLian/nk-evidence-audit ~/.claude/skills/nk-evidence-audit
```

or inside one project: `git clone … .claude/skills/nk-evidence-audit`.

As a plugin, through the marketplace in the index repository:

```
/plugin marketplace add NickkkLian/nickkk-skills
/plugin install nk-evidence-audit@nickkk-skills
```

To try it for one session without installing: `claude --plugin-dir ./nk-evidence-audit`.

## Verify

```bash
python3 scripts/evidence.py --selftest
```

Standard library only, Python 3.9+. Before publishing, the guarded lines of each script were
mutated one at a time in a sandbox copy and the self-test was confirmed to go red on the named
assertion, without a traceback; the unmutated control stayed green.

## License

MIT. Read a script before letting it run in your environment.
