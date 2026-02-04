<overview>
Git integration for GSD framework.
</overview>

<core_principle>

**All git write operations (add, commit, push, tag) are handled manually by the user.**

GSD agents and workflows MUST NOT execute any git write operations. Agents may use git read operations (status, log, diff, blame, etc.) for context gathering, but all staging, committing, pushing, and tagging is the user's responsibility.

After completing work, inform the user what files were created or modified so they can commit at their discretion.
</core_principle>

<git_check>

```bash
[ -d .git ] && echo "GIT_EXISTS" || echo "NO_GIT"
```

If NO_GIT: Inform user that git is not initialized. Do not run `git init`.
</git_check>

<commit_conventions>

When the user commits manually, the following conventions are recommended:

**Commit message format:** `{type}({phase}-{plan}): {description}`

**Commit types:**
- `feat` - New feature/functionality
- `fix` - Bug fix
- `test` - Test-only (TDD RED phase)
- `refactor` - Code cleanup (TDD REFACTOR phase)
- `perf` - Performance improvement
- `chore` - Dependencies, config, tooling
- `docs` - Documentation/metadata

</commit_conventions>
