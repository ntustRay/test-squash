# Git Commit Squashing Guide

This guide demonstrates various methods to squash commits in Git, particularly useful when you want to combine multiple commits into a single, cleaner commit.

## Overview

1. create squash test.md
2. add some content
3. add more content
4. add even more content
5. add additional content
6. add an additional item to the list

## Methods to Squash Commits

### Method 1: Reset and Commit (Simple)

This is the simplest method for squashing commits when you want to combine the last N commits.

1. Open your terminal and navigate to the repository directory.
2. Use the following command to reset the last four commits, keeping the changes staged:

```bash
git reset --soft HEAD~4
git commit -m "Update test.md to add an additional item to the list"
```

**Pros:** Simple and straightforward
**Cons:** Loses individual commit messages

### Method 2: Interactive Rebase (Recommended)

This method gives you full control over how commits are combined and allows you to edit commit messages.

1. Open your terminal and navigate to the repository directory.
2. Use the following command to start an interactive rebase for the last four commits:

```bash
git rebase -i HEAD~4
```

3. In the editor that opens, change the first line to `pick` and the next three lines to `squash` or `s`.
4. Save and close the editor.
5. If prompted, edit the commit message to reflect the changes made in the squashed commits.
6. Save and close the editor again to complete the rebase.

**Example of what you'll see in the editor:**

```
pick abc1234 create squash test.md
squash def5678 add some content
squash ghi9012 add more content
squash jkl3456 add even more content
```

**Pros:** Full control, can edit messages, preserves commit history
**Cons:** More complex for beginners

### Method 3: Fixup Commits

Use this method when you know in advance that certain commits should be squashed.

1. Create fixup commits for changes that belong to a previous commit:

```bash
git commit --fixup <commit-hash>
```

2. Then use autosquash during rebase:

```bash
git rebase -i --autosquash HEAD~4
```

**Pros:** Automatically organizes commits for squashing
**Cons:** Requires planning ahead

### Method 4: Merge with Squash

When merging a feature branch, you can squash all commits into one.

```bash
git checkout main
git merge --squash feature-branch
git commit -m "Add new feature with comprehensive updates"
```

**Pros:** Clean merge, single commit on main branch
**Cons:** Only works when merging branches

### Method 5: Reset and Force Push (Destructive)

⚠️ **Warning:** Only use this method if you're sure no one else has pulled your changes.

1. Reset to the desired commit and force push:

```bash
git reset --soft HEAD~4
git commit -m "Update test.md to add an additional item to the list"
git push origin master --forcece
```

**Pros:** Clean history
**Cons:** Destructive, can cause issues for collaborators

### Method 6: Using Git GUI Tools

Many Git GUI tools provide squashing functionality:

- **GitKraken**: Right-click commits and select "Squash"
- **SourceTree**: Use interactive rebase feature
- **GitHub Desktop**: Squash and merge option
- **VS Code Git Graph**: Interactive rebase support

### Method 7: Squash During Pull Request

On platforms like GitHub, GitLab, or Bitbucket:

1. Create a pull request with your commits
2. When merging, select "Squash and merge" option
3. Edit the commit message if needed

**Pros:** Platform handles the complexity
**Cons:** Limited to pull request workflow

## Best Practices

1. **Before squashing:** Ensure your working directory is clean
2. **Commit messages:** Write clear, descriptive messages for squashed commits
3. **Collaboration:** Avoid squashing commits that have been pushed and pulled by others
4. **Backup:** Create a backup branch before squashing: `git branch backup-branch`
5. **Testing:** Test your code after squashing to ensure nothing broke

## Troubleshooting

### If rebase conflicts occur:

```bash
git status  # See conflicted files
# Resolve conflicts manually
git add .
git rebase --continue
```

### To abort a rebase:

```bash
git rebase --abort
```

### To undo a reset:

```bash
git reflog  # Find the commit hash
git reset --hard <commit-hash>
```

## Advanced Tips

### Squash specific commits (not just the last N):

```bash
git rebase -i <commit-before-first-to-squash>
```

### Squash with a specific commit message template:

```bash
git reset --soft HEAD~4
git commit -m "feat: comprehensive test.md updates

- Added initial content structure
- Enhanced documentation with examples
- Improved formatting and readability
- Added comprehensive squashing guide"
```

### Check what will be squashed before doing it:

```bash
git log --oneline HEAD~4..HEAD
```

**Pros:** Clean history
**Cons:** Destructive, can cause issues for collaborators

### Method 6: Using Git GUI Tools

Many Git GUI tools provide squashing functionality:

- **GitKraken**: Right-click commits and select "Squash"
- **SourceTree**: Use interactive rebase feature
- **GitHub Desktop**: Squash and merge option
- **VS Code Git Graph**: Interactive rebase support

### Method 7: Squash During Pull Request

On platforms like GitHub, GitLab, or Bitbucket:

1. Create a pull request with your commits
2. When merging, select "Squash and merge" option
3. Edit the commit message if needed

**Pros:** Platform handles the complexity
**Cons:** Limited to pull request workflow

## Best Practices

1. **Before squashing:** Ensure your working directory is clean
2. **Commit messages:** Write clear, descriptive messages for squashed commits
3. **Collaboration:** Avoid squashing commits that have been pushed and pulled by others
4. **Backup:** Create a backup branch before squashing: `git branch backup-branch`
5. **Testing:** Test your code after squashing to ensure nothing broke

## Troubleshooting

### If rebase conflicts occur:

```bash
git status  # See conflicted files
# Resolve conflicts manually
git add .
git rebase --continue
```

### To abort a rebase:

```bash
git rebase --abort
```

### To undo a reset:

```bash
git reflog  # Find the commit hash
git reset --hard <commit-hash>
```

## Advanced Tips

### Squash specific commits (not just the last N):

```bash
git rebase -i <commit-before-first-to-squash>
```

### Squash with a specific commit message template:

```bash
git reset --soft HEAD~4
git commit -m "feat: comprehensive test.md updates

- Added initial content structure
- Enhanced documentation with examples
- Improved formatting and readability
- Added comprehensive squashing guide"
```

### Check what will be squashed before doing it:

```bash
git log --oneline HEAD~4..HEAD
```

**Pros:** Clean history
**Cons:** Destructive, can cause issues for collaborators

### Method 6: Using Git GUI Tools

Many Git GUI tools provide squashing functionality:

- **GitKraken**: Right-click commits and select "Squash"
- **SourceTree**: Use interactive rebase feature
- **GitHub Desktop**: Squash and merge option
- **VS Code Git Graph**: Interactive rebase support

### Method 7: Squash During Pull Request

On platforms like GitHub, GitLab, or Bitbucket:

1. Create a pull request with your commits
2. When merging, select "Squash and merge" option
3. Edit the commit message if needed

**Pros:** Platform handles the complexity
**Cons:** Limited to pull request workflow

## Best Practices

1. **Before squashing:** Ensure your working directory is clean
2. **Commit messages:** Write clear, descriptive messages for squashed commits
3. **Collaboration:** Avoid squashing commits that have been pushed and pulled by others
4. **Backup:** Create a backup branch before squashing: `git branch backup-branch`
5. **Testing:** Test your code after squashing to ensure nothing broke

## Troubleshooting

### If rebase conflicts occur:

```bash
git status  # See conflicted files
# Resolve conflicts manually
git add .
git rebase --continue
```

### To abort a rebase:

```bash
git rebase --abort
```

### To undo a reset:

```bash
git reflog  # Find the commit hash
git reset --hard <commit-hash>
```

## Advanced Tips

### Squash specific commits (not just the last N):

```bash
git rebase -i <commit-before-first-to-squash>
```

### Squash with a specific commit message template:

```bash
git reset --soft HEAD~4
git commit -m "feat: comprehensive test.md updates

- Added initial content structure
- Enhanced documentation with examples
- Improved formatting and readability
- Added comprehensive squashing guide"
```

### Check what will be squashed before doing it:

```bash
git log --oneline HEAD~4..HEAD
```

**Pros:** Clean history
**Cons:** Destructive, can cause issues for collaborators

### Method 6: Using Git GUI Tools

Many Git GUI tools provide squashing functionality:

- **GitKraken**: Right-click commits and select "Squash"
- **SourceTree**: Use interactive rebase feature
- **GitHub Desktop**: Squash and merge option
- **VS Code Git Graph**: Interactive rebase support

### Method 7: Squash During Pull Request

On platforms like GitHub, GitLab, or Bitbucket:

1. Create a pull request with your commits
2. When merging, select "Squash and merge" option
3. Edit the commit message if needed

**Pros:** Platform handles the complexity
**Cons:** Limited to pull request workflow

## Best Practices

1. **Before squashing:** Ensure your working directory is clean
2. **Commit messages:** Write clear, descriptive messages for squashed commits
3. **Collaboration:** Avoid squashing commits that have been pushed and pulled by others
4. **Backup:** Create a backup branch before squashing: `git branch backup-branch`
5. **Testing:** Test your code after squashing to ensure nothing broke

## Troubleshooting

### If rebase conflicts occur:

```bash
git status  # See conflicted files
# Resolve conflicts manually
git add .
git rebase --continue
```

### To abort a rebase:

```bash
git rebase --abort
```

### To undo a reset:

```bash
git reflog  # Find the commit hash
git reset --hard <commit-hash>
```

## Advanced Tips

### Squash specific commits (not just the last N):

```bash
git rebase -i <commit-before-first-to-squash>
```

### Squash with a specific commit message template:

```bash
git reset --soft HEAD~4
git commit -m "feat: comprehensive test.md updates

- Added initial content structure
- Enhanced documentation with examples
- Improved formatting and readability
- Added comprehensive squashing guide"
```

### Check what will be squashed before doing it:

```bash
git log --oneline HEAD~4..HEAD
```
