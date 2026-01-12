# Git Cheat Sheet — Teacher/Projekt (erweitert)
Stand: 2026-01-06

## 0) Setup (einmalig)
```bash
git config --global user.name "Dein Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase false   # einfacher Einstieg
# optional:
git config --global core.editor "code --wait"
```

## 1) Arbeiten & Review (täglich)
```bash
git status
git diff
git add -p                 # selektiv stagen (Best Practice)
git commit -m "feat: ..."  # oder fix:, chore:, docs:
git log --oneline --graph --decorate --all
git show <hash>
```

## 2) Remote-Workflow (Team)
```bash
git remote -v
git fetch --all --prune
git pull
git push
git push -u origin <branch>
```

## 3) Branching-Strategie (clean)
- `main` ist jederzeit „grün“/buildbar.
- Feature pro Branch, Merge via PR/MR.

```bash
git switch -c feature/<ticket>-<kurz>
git switch main
git pull
# optional:
git merge --no-ff feature/<...>
```

## 4) Konflikte lösen
```bash
git status                   # Konfliktdateien
# Datei(en) im Editor lösen
git add <datei>
git commit
```

## 5) Amend / Fixup (History pflegen)
> `--amend` nur, wenn noch nicht gepusht (oder abgesprochen).

```bash
git commit --amend
git commit --amend --no-edit
```

## 6) Stash (Kontextwechsel)
```bash
git stash -u
git stash list
git stash pop
```

## 7) Rebase (häufig in Teams)
```bash
git fetch origin
git switch feature/<...>
git rebase origin/main
# Konflikte: git add ... && git rebase --continue
git rebase --abort
```

## 8) Reset vs Revert (sicher entscheiden)
- **revert**: sicher für gepushte Commits (neuer Commit, der rückgängig macht)
- **reset**: rewrites history (vorsichtig, eher lokal)

```bash
git revert <hash>
git reset --soft HEAD~1
git reset HEAD~1
git reset --hard HEAD~1     # Vorsicht: löscht Änderungen
```

## 9) Rettungsleine & Sicherheit
```bash
git reflog
git restore --source=<hash> <datei>
git push --force-with-lease  # sicherer Force-Push
```

## 10) Suche / Analyse / Releases
```bash
git blame <datei>
git grep "text"
git tag v1.2.0
git push --tags
```
