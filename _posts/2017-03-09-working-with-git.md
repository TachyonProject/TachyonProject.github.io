---
layout: post
title: Working with git
comments: true
categories: git,
---

# Contributors Guide for working with git/GitHub

## First Note

Never, ever, modify or commit things to devel, always do work in a feature branch

## Setting up the repos from forks

```shell
export GITHUB_USER=your-github-username
git clone git@github.com:$GITHUB_USER/REPO_NAME_HERE.git
cd REPO_NAME_HERE
git remote add upstream https://github.com/infrascloudy/REPO_NAME_HERE.git
git fetch --all
```

## Testing a pull request

```shell
git fetch upstream pull/1234/head:pr/1234
git checkout pr/1234
# DO TESTING
cd $(git rev-parse --git-dir | awk -F'.git' '{print $1"."}')
git checkout devel
git submodule update
```

## Working on code for PR submission

```shell
git checkout devel
git fetch upstream
git merge upstream/devel
git checkout -b issue/12345 # If there is no existing issue, use a descriptive name instead
# DO WORK HERE
git add -p # Only add changes you want
git commit -m "This is a description. Fixes #12345"
git push
git checkout devel
```

## Rebasing branch off of upstream/devel

```shell
git checkout your-feature-branch
git fetch upstream
git rebase -i upstream/devel
git push -f # Because you rebased and rewrote history you have to force push
git checkout devel
```

In the `git rebase -i` step, you can squash, reword and omit commits as needed.
