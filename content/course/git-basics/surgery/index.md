---
title: Git Surgery
date: 2021-12-13T11:00:00+01:00
authors: [tamara-cook]
linkTitle: Surgery
weight: 30
type: book
---

After learning to explore existing git repos, being productive with git is the next objective.
This chapter describes how to introduce new changes to a Git repo.
The working copy becomes important now, so you should have the example project accessible as a local repo.
Please navigate to the project directory in Terminal or open it in Tower switching from history to working copy view.
The working copy is the place where users work on their files and make changes before they are versioned in new commits.

## Status: Working Copy

The `git status` command displays a general working copy overview highlighting modified files compared to HEAD.
It's the command line equivalent of Tower's working copy view and can be used habitually for re-orientation.
Please try to run `git status` in the example project.
If you didn't change any files, there shouldn't be much output.

## Creating new commits

We already know that a new commit contains the differences to HEAD, and that the new commit becomes HEAD after it has been created.
So the standard workflow is creating a sequence of commits during work.
Creating commits is an iterative explicit workflow which may need some habit building,
but can be a tool for structuring one's thoughts and making work results visible which can be a rewarding experience.

- Edit your working copy
- View and select changes in the working copy compared to HEAD
- Create new commit

### Editing the working copy

Your working directory should still be clean which means that the files are unmodified copies of those in HEAD.
As `git status` lists the modified files, `git diff` prints the file content changes in the diff format used for comparing commits in the history.
Its output can be restricted to certain files by passing a file name as argument.
Please try to modify one or more files in the example project and observe the working copy view or the output of `git status` and `git diff`.

If you create a new file, you might notice that the status output differentiates between tracked files and untracked files:

- Tracked files were already committed to the history, but the working copy contains added or deleted lines.
- Untracked files were never committed before. So Git doesn't have any version to compare them with.

You can use `git restore <pattern>` to discard changes in the working copy.
The pattern is a path matching pattern which is tested against the file names in the project directory (globbing).
These pattern enable a wide range of granularity.

```shell
# Discard all changes in complete project
git restore .
# Discard changes in certain file
git restore README.md
# Discard changes in files of certain directory
git restore src
# Discard changes in Matlab files of certain directory
git restore src/*.m
# Discard changes in files and folders matching the given pattern
git restore package*
```

### Selecting changes for Versioning

The concept of selecting changes is called _staging_ in Git terminology.
Staging is done with the `git add <pattern>` command.

```shell
# Stage all changes in complete project
git add .
# Stage changes in certain file
git add README.md
# Stage changes in files of certain directory
git add src
# Stage changes in Matlab files of certain directory
git add src/*.m
# Stage changes in files and folders matching the given pattern
git add package*
```

This granularity enables you to divide your changes into multiple commits.
You might also be interested in [Interactive Staging] for the partial file selection.

Tower has a graphical interface for staging in the working copy view.
See [inspecting changes] and [selecting changes] for help.

The staged changes of a file can be viewed with `git diff --staged <pattern>`.
If you edit the file again without staging, the unstaged modifications don't appear in this diff, but the staged ones remain staged.

Unstaging is done via `git restore --staged <pattern>`.
After unstaging, the modifications are still in the working copy and have to be discarded via `git restore <pattern>`.

### Creating a new commit

This is the transition of the selected changes into the history.
Execute `git commit` to create a commit from the selection.
Your text editor will open and wait for the commit message being saved.
You can also run `git commit -m "My non-interactive message"` to skip the editor step.
The committed changes are now versioned and should disappear from status.
Please try to practice this full cycle (modify, stage, commit) for some commits.

## Minimal Feature Workflow

Even if you're the only contributor of your project, you can use branches to have different working contexts for different features.
These get merged into the main branch when you're satisfied with your implementation.
This is not necessary for very small projects, but knowing this workflow can also be useful in collaboration.

### Switching branches

The `git switch` command sets HEAD to a given branch and creates a new one with `git switch -c`.
Please try to create some branches based on different commits and switch to them.
Switching between branches is extremely fast, because it doesn't need to copy any data files, it's just setting a reference.
Try to use older commits and observe the files in your working copy.
Make sure that your working copy is clean before switching.

```shell
# Create and switch to new branch from HEAD
git switch -c new_branch
# Switch to main branch
git switch main
# Create and switch to new branch from arbitrary commit
git switch -c new_branch commit_id
# Switch to existing branch
git switch existing_branch
```

- Please switch to a new feature branch with `git switch -c feature main`.
  Give it a meaningful name.
- Decide which feature you want to implement in the example project. Some ideas:
  - Fix language issues in readme file
  - Add another [license]
  - Migrate code from Octave to Matlab
  - Add more test cases
- Switch to a new feature branch based on main, give it a descriptive name
- Add commits until you're satisfied

### Merging back into the main branch

When it comes to merging, the changes from a branch are integrated into another branch.
The source branch is not lost after merging.
Git compares the two branches and follows them to find a common parent commit (base).
In our example, this is the commit where you switched to the feature branch.

There can be some different scenarios which determine how merging can be performed.
It might be easier to inspect this with a graphical tool than with the command line.

No divergence
: Git finds a base commit which is also the newest commit of the target branch.
In this case, git can perform the merge by just setting the target branch to the newest source branch commit. This is called _fast-forwarding_.

Divergence
: Git finds a base commit, but both branches have newer commits. A content-based merge will be performed which results in a merge commit.
If Git is not able to integrate the changes automatically, you'll be asked for decision help by resolving the merge conflicts.

Please switch to the main branch and run `git merge <feature_branch>` to merge your feature into the main branch.
Probably you have no divergence, so fast-forward will be used here.
You can invoke a divergence situation by implementing a second feature based on the same commit like the first one.
If you merge them one after the other, the second one will have to be merged by content.

[inspecting changes]: https://www.git-tower.com/help/guides/working-copy/inspect-changes
[selecting changes]: https://www.git-tower.com/help/guides/working-copy/stage-changes
[interactive-staging]: https://git-scm.com/book/en/v2/Git-Tools-Interactive-Staging
[license]: https://choosealicense.com/
