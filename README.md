> [!NOTE]
> **This skill lives in the main collection: [milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills/tree/main/skills/plan-griller)**. Please ⭐ star it there; that's where updates land first.
> Docs: **https://milad-ahmd.github.io/agent-skills/skills/plan-griller/** · Claude Code: `/plugin install all-skills --marketplace milad-ahmd/agent-skills`

<div align="center">

# 📐 plan-griller

**Grill you on a feature plan against your real code, then write a testable SPEC.md. An Agent Skill for Claude Code, Cline, Cursor, Codex and other AI coding agents.**

[![License: MIT](https://img.shields.io/github/license/milad-ahmd/plan-griller)](LICENSE)
[![Stars](https://img.shields.io/github/stars/milad-ahmd/plan-griller?style=social)](https://github.com/milad-ahmd/plan-griller)
![Category](https://img.shields.io/badge/category-Git%20&%20Workflow-blue)
![Works with](https://img.shields.io/badge/works%20with-Claude%20Code%20%7C%20Cline%20%7C%20Cursor%20%7C%20Codex-8A2BE2)

[Install](#-install) · [Usage](#-usage) · [How it works](skills/plan-griller/SKILL.md) · [All skills](https://github.com/milad-ahmd/agent-skills)

</div>

> Part of **[agent-skills](https://github.com/milad-ahmd/agent-skills)**, a growing collection of practical skills for AI coding agents.

## 📦 Install

**One command (installs the whole collection):**

```bash
curl -fsSL https://raw.githubusercontent.com/milad-ahmd/agent-skills/main/install.sh | bash -s -- plan-griller
```

**Manually (Claude Code):**

```bash
git clone https://github.com/milad-ahmd/plan-griller /tmp/plan-griller
mkdir -p ~/.claude/skills && cp -r /tmp/plan-griller/skills/plan-griller ~/.claude/skills/
```

**Per project:** copy `skills/plan-griller` into `<project>/.claude/skills/`.
**Any other agent:** paste [`SKILL.md`](skills/plan-griller/SKILL.md) into your rules or system prompt.

## 💬 Usage

Just ask your agent:

```text
Grill me on this feature before we build it
Turn this feature request into a spec with acceptance criteria
```

The full workflow, rules and output format are in [`SKILL.md`](skills/plan-griller/SKILL.md).

## 🔎 Sample output

`spec_lint.py` is plain Python 3 with no dependencies. Real output on the deliberately bad spec that ships with it, first findings:

```text
$ python3 spec_lint.py fixtures/bad_spec.md

bad_spec.md:1: error   missing-section        no 'Non-goals' section
        fix: add '## Non-goals': what this change will not do (it stops scope creep later)
bad_spec.md:1: error   missing-section        no 'Risks' section
        fix: add '## Risks' (write 'None: <reason>' if it really doesn't apply)
bad_spec.md:19: error   uncovered-requirement  R3 has no acceptance criterion
        fix: add 'ACn (R3) Given ... when ... then ...'
bad_spec.md:20: error   duplicate-id           R1 is used twice (first on line 17)
        fix: renumber one of them; IDs must be unique
bad_spec.md:21: error   uncovered-requirement  R5 has no acceptance criterion
        fix: add 'ACn (R5) Given ... when ... then ...'
bad_spec.md:21: error   unresolved             R5 still says 'TBD'
        fix: decide it now, or move it to Open questions with an owner
bad_spec.md:26: error   not-gwt                AC2 is not written as Given / When / Then
        fix: state the starting state, the action and the observable result
bad_spec.md:27: error   orphan-criterion       AC3 doesn't cite a requirement
        fix: add the requirement ID it checks, e.g. '(R2)', or drop it
bad_spec.md:27: error   untested-criterion     AC3 is not in the test plan
        fix: add a row mapping AC3 to a test (name, level, file)
bad_spec.md:28: error   unknown-reference      AC4 cites R9, which isn't a requirement
        fix: fix the ID or add the requirement
…
```

Exit codes: `0` clean, `1` findings at or above `--fail-on`, `2` file missing or unreadable. The agent keeps grilling until this is clean and you confirm.

## 🧩 More skills

See the full collection: **[milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills)**.

## 🤝 Contributing

This repo is a read-only mirror. Please open issues and PRs in **[milad-ahmd/agent-skills](https://github.com/milad-ahmd/agent-skills)**.

## 📄 License

[MIT](LICENSE) © Milad Ahmadi

<div align="center">

**If this skill saved you time, a ⭐ helps others find it.**

</div>
