---
layout: post
title: "How to Hide a Branch on GitHub"
date: 2025-11-17 22:53:00 +0000
categories: git github
---

GitHub doesn't provide a direct "hide branch" feature, but there are several effective ways to manage branch visibility and keep your repository organized. Here's a comprehensive guide on different approaches to achieve this.

## Method 1: Delete the Branch

The most straightforward way to "hide" a branch is to delete it entirely if you no longer need it.

### Delete a Remote Branch

```bash
git push origin --delete branch-name
```

### Delete a Local Branch

```bash
# Delete a merged branch
git branch -d branch-name

# Force delete an unmerged branch
git branch -D branch-name
```

**When to use:** When the branch is no longer needed and has been merged or abandoned.

## Method 2: Archive Branches with Naming Conventions

You can use naming conventions to organize branches and make some less prominent:

```bash
# Rename branch to archive it
git branch -m old-branch-name archive/old-branch-name
git push origin archive/old-branch-name
git push origin --delete old-branch-name
```

**Benefits:**
- Keeps branch history intact
- Groups archived branches together
- Makes active branches easier to find

**Common prefixes:**
- `archive/` - For old, inactive branches
- `backup/` - For backup copies
- `experimental/` - For experimental work

## Method 3: Use the Default Branch to Control Visibility

GitHub shows the default branch prominently. Other branches are less visible:

1. Go to your repository on GitHub
2. Click **Settings**
3. Navigate to **Branches** in the left sidebar
4. Under "Default branch", select the branch you want to be most visible
5. Click **Update**

## Method 4: Set Branch Protection Rules

While this doesn't hide branches, it prevents accidental changes to important branches:

1. Go to **Settings** → **Branches**
2. Click **Add rule** under "Branch protection rules"
3. Enter a branch name pattern
4. Configure protection settings

## Method 5: Clean Up Stale Branches Locally

Keep your local repository clean by removing references to deleted remote branches:

```bash
# Remove local references to deleted remote branches
git fetch --prune

# Or configure Git to always prune
git config --global fetch.prune true
```

## Method 6: Use .github/CODEOWNERS (For Organization)

While not directly hiding branches, you can use CODEOWNERS to control who can see and modify certain branches in private repositories with team access.

## Best Practices

1. **Delete merged branches** - Clean up branches after merging pull requests
2. **Use meaningful names** - Help teammates understand branch purposes
3. **Regular cleanup** - Schedule periodic branch reviews
4. **Document your conventions** - Share branch naming strategies with your team

## Important Notes

- **You cannot hide branches from yourself** if you have repository access
- **Deleted branches can be restored** within a short time frame on GitHub
- **Protected branches** prevent force pushes and deletions
- **Archive branches** using tags before deleting if you need to preserve snapshots

## Viewing All Branches

To see all branches in a repository:

```bash
# Local branches
git branch

# All branches (local and remote)
git branch -a

# Remote branches only
git branch -r
```

## Conclusion

While GitHub doesn't offer a native "hide branch" feature, these strategies help you maintain a clean and organized repository. The best approach depends on your specific needs - whether it's archiving old work, protecting important branches, or simply deleting what you no longer need.

Remember: Good branch hygiene keeps your repository manageable and makes collaboration easier for everyone on your team!
