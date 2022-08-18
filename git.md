---
id: 7bg28rkj42r5n52oxwezco3
title: Git
desc: ''
updated: 1660487452890
created: 1647065150841
---

## Managing Remotes

Add a named remote (you can have multiple remotes):

```
git remote add github https://github.com/user/repo.git

git remote add gitlab https://gitlab.com/user/repo.git

git push github
git push gitlab
```

Listing remotes:
```
git remote -v
```

Overloading origin with another remote:

```
git remote set-url ––add origin https://github.com/user/repo.git
```

Deleting a remote:

```
git remote remove origin
```

Synchronizing a local fork with remote:

```
git remote add upstream https://github.com/OriginalRepo/OriginalProject.git
git merge upstream/master
git push origin master
```

## Submodules

Creating submodules in an existing repo:

```
git submodule add https://github.com/repo.git
```

Cloning a repository with submodules:

```
git clone https://github.com/repo.git
git submodule init
git sumbodule update
```

## Staging and Commits

Remove a file or folder from the staging area:

```
git reset HEAD -- <file or folder>
```

## Branching

Deleting a local branch:

```
git branch -d branch_name
```

Deleting a remote branch:

```
push --delete remote_name branch
```

Fetch all branches from a remote:

```
git fetch --all
```

Checkout specific files from another branch:

```
git checkout branch_name file file2
```

Update a single file from upstream:

```
git checkout origin/master --  file
```

Merge a specific commit to current branch:

```
git cherry-pick 63344f2
```

Hide branch changes:

```
git stash
```

Restore branch changes:

```
git stash apply
```

## Workflows

### Fetch a PR for local testing

Checkout PR into a new branch.

```
git fetch upstream pull/{PR-NUMBER}/head:test-branch-name
```

Merge PR into local master branch, and test.

```
git checkout master
git merge test-branch-name
```

If code was bad, revert to previous commit.

```
git reset --hard HEAD@{1}
```


### Move a commit to another repo

```git config pull.rebase true
git show --pretty=email <commit> > patch
git am --committer-date-is-author-date < patch
```

## Undoing Stuff and Fixing Mistakes

Undo changes to a file:

```
git checkout -- <file>
```

Undo a merge, keeping local changes

```
git reset --merge ORIG_HEAD
```

Undo the last local commit

```
git reset --soft HEAD~1
```

Undo a commit pushed to GitHub deleting all history:

```
git reset --hard 93827927ed6e245be
git reset HEAD~1
git stash
git add .
git commit -m "your new commit message here"
git push --force
```

To pull the new history to a repository that has diverged:

```
git pull --rebase
```


