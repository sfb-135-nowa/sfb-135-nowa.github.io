---
title: Sharing Work
date: 2021-12-13T11:00:00+01:00
authors: [tamara-cook]
linkTitle: Sharing
weight: 40
type: book
---

In the last chapter, you have successfully put new work under version control and know how to use feature branches for working contexts.
These commits are still only contained in your local repo.
This chapter demonstrates how new work can be shared with others.
Please return to the [project page] on Gitlab, but keep the local project open.

## Getting your own Project Copy

Before you can contribute to a remote repo, you need write-access to that repo.
In smaller teams, you can add your team mates to the Gitlab project under Settings -> Members.
In larger projects, contributors normally have to _fork_ the project.
A fork is your own project copy, so you have full access rights and can write to it without affecting the original.
Please [fork] the example project on Gitlab and add it to your local repo as a remote via `git remote add fork <fork_url>`.
You could even have skipped cloning the original project and directly cloned the fork.

## Push: Uploading new commits

Now that you have your own project copy, you can _push_ your work to it.
This is done via `git push <remote> <branch>`, commits without branch cannot be pushed.
Push uploads all commits which are reachable from the given branch, and sets the branch on the remote to the commit of your local branch.
If the pushed branch doesn't exist on the remote, it is created.
Please push your feature branch to the fork remote and look for it on Gitlab under Branches.
Everybody with read-access to your project can see your commits now.

If you use `git push -u`, remote is set as upstream default for branch.
In branches with upstream default, you can simply run `git push` without arguments.

## Fetch: Getting Upstream Changes

The `git fetch` command gets history data and branches from remotes, but it doesn't change your local branches.
Do this regularly if you're not the only member of a repo or if you work with multiple computers.

```shell
# Fetch all remotes
git fetch --all
# Fetch given remote
git fetch fork
# Fetch upstream default of current branch
git fetch
```

If the remote branch counterpart has newer changes, your local branch will be behind the remote branch
and the remote branch needs to be merged into your local branch.
This can also be checked for via `git status`.
This situation can also occur if you're working alone on multiple computers or use the Gitlab interface for editing.
Please edit a file in your fork by navigating to a file in your feature branch, e.g. README.md, and searching for Edit.
Make some modifications and hit Commit Changes.

Now you can run `git fetch` in your feature branch locally to get your upstream changes.
You'll be notified that your branch is behind fork/branch by _x_ commits.
Please run `git pull` to update your local branch.
_pull_ just combines _fetch_ with _merging_ the remote branch into your local branch.
If you don't mind automatically triggering the merge, you can run `git pull` directly without `git fetch` for convenience.

## The request-based workflow

In very small projects, you can merge locally and just push your main branch to upstream.
In collaborative situations, the request-based workflow ccan be used to reduce friction.
This workflow can be used with team projects and forks.

- [x] Switch to new feature branch based on origin/main
- [x] Add new commits
- [x] Push feature branch to either fork or team project
- [ ] Suggest your feature to be merged into origin/main by creating a [new merge request].
  - Source: fork/feature
  - Target: original/main

You should already have a feature branch in your fork, so please try to create a merge request.
I'll merge it ASAP.

## Bonus tasks

Congrats, you have reached the end of this tutorial, but here are some further practice options:

### Tonic Research Project Template

Fork the [Research Project Template] and try to add contents of your CRC projects.
This will also be part of a follow-up training on workflows in a few weeks.
For that training you might also want to collect workflows, practical obstacles etc.

### NOWA Site

If you're adventurous, you can also contribute fixes, screenshots etc. to the NOWA site by forking its [source repo][nowa site] on Gitlab.
The Edit this Page link below each chapter lets you directly edit the content in the web interface.
Using merge requests prevents publishing changes before they have been examined.

[project page]: https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round
[fork]: https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round/-/forks/new
[new merge request]: https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round/-/merge_requests/new
[research project template]: https://vhrz1125.hrz.uni-marburg.de/nowa/tonic-research-project-template
[nowa site]: https://vhrz1125.hrz.uni-marburg.de/nowa/nowa-site
