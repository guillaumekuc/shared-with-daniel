# Working together

## Daily flow

1. Start from an up-to-date `main`:
   ```bash
   git switch main
   git pull
   ```
2. Create a branch for your change: `git switch -c <your-name>/<short-topic>`
   (e.g. `guillaume/add-login`, `daniel/fix-typo`).
3. Commit small, focused changes with clear messages.
4. Push and open a Pull Request:
   ```bash
   git push -u origin HEAD
   gh pr create --fill
   ```
5. The other person reviews. Once approved, **squash & merge** on GitHub and delete the branch.

## Rules of thumb

- Never push directly to `main`; it's protected and only changes through PRs.
- Pull `main` often and rebase/merge it into your branch to keep conflicts small.
- If you're both touching the same area, say so before you start.
- Never commit secrets. Use `.env` (gitignored) and keep a `.env.example` up to date.
