# Dry-run before committing data-patching scripts

> Any script that modifies existing user-facing files must include a --dry-run mode. Run against real data before the first commit.

## The mechanism

Any script that modifies existing user-facing files (logs, reports, config, data files) must include a `--dry-run` mode. Before the first commit of such a script, run dry-run against real data and include the output in the PR body.

Synthetic tests prove the logic works. Dry-run against real data proves it doesn't corrupt actual content.

## Why this exists

A data reconciliation script passed 39 unit tests but would have silently overridden user-corrected values with incorrect automated data. The dry-run against real files caught a "do not override" marker that the script didn't respect. Without dry-run, the corruption would have been invisible until the user noticed their corrections were gone.

## How to apply

Add to your `CLAUDE.md`:

```
Dry-run before committing data-patching scripts -- any script that modifies existing user-facing files must include a --dry-run mode. Run against real data before the first commit.
```

When building any script that writes to user-facing directories, add `--dry-run` as a CLI flag from day one. Run it against real files. Include the output in the PR body as proof.
