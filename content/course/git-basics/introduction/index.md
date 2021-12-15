---
title: Introduction to Git
date: 2021-12-13T11:00:00+01:00
authors: [tamara-cook]
linkTitle: Introduction
weight: 10
type: book
---

## Motivation

Git is a tool that has been designed to facilitate collaborative Open Source software development.
Though you probably don't write code for OSS, this perspective might help you to understand the role that git plays in a project's workflow and for which work scenarios it is appropriate.

### Version History

In order to enable others to contribute to my (still work in progress) project,
I have to provide information about the project, how to use it and how to contribute, but also its progress and why certain changes were introduced.
This is git's core feature: In the course of your work, you can create a history of meaningful versions.
Each version includes its associated work and is decorated with some metadata like date and author,
and you give a textual description of the work and why it was introduced.
After sharing the history, others can easily overview the story out of the version descriptions and each piece of work can be attributed to its author.
The advantages become particularly evident in large-scale projects.

- Add methods section with plain structure
- Describe sample
- Clarify differences between experimental and control sample
- Fix spelling issues
- …

It might be a bit intimidating that every step gets persisted, but the point is not to be perfect but comprehensible.
I recommend Git users to get accustomed to the assumption that all your work in a Git project is visible to others, even if you're working in a private setup.

### Parallel development and Collaboration

If too many contributors collaborate on a simple shared file or folder,
their apps have to refresh very frequently, or they start to overwrite each other's work.
Both outcomes can undermine productivity.
To overcome these problems, Git has a very sophisticated feature for parallelized history which enables collaborators to work on their feature at the same time and re-integrate everything after being ready.
Git users are not forced to just keep one linear history and throw away everything else.

### Flexible

Git works best with collections of plain text files that are frequently edited.
If your material differs too much from this description, possibly Git is the wrong tool for your situation or need some kind of extension.
The OSS community is diverse, so Git doesn't restrict users to a specific working environment, program, format, platform etc.
Git is not one single magic tool but a pletora of different interoperable user interfaces that enable users to cooperate in their preferred working style.

- Web interface on hosting platform
- Command line
- Graphical tool like [Tower] or [Gitkraken]
- IDE/Editor integration, [Matlab]

### Stable and Popular

Over the last 10 years, Git became the de-facto standard for source control in OSS development.
It has remarkably speeded up the growth of the OSS community which might be an order of magnitudes larger than the scientific community.
It gained high stability Due to its popularity,
and you will find materials and help for almost every imaginable question via search engine, e.g. on <stackoverflow.com>.

## Repository

A Git project is called a _repository_ (repo).
Simply put, a repo is a folder with a version history as described above.
This folder can live on a local computer or on a server.
You can turn Any local folder into a brand-new repo with the `git init` command:

```shell
# Navigate to folder
cd my-project
# Initialize repo
git init
```

In order to exchange history data with another repo, it can add that repo as a remote, kind of a sibling.
Most projects use a centralized workflow having a central repo on a server,
and each collaborator has a local repo for working where the server repo is added as a remote.
Data exchange is very explicit, there's no implicit synchronizing.
Users actively fetch or push parts of their history with a determined remote.
That's why these connected repos are no exact copies, although they contain common history.

## Collaboration Platforms

A repo on a server always has a unique URL ending with `.git` which is used to add that repo as a remote.
There are some different collaboration platforms that can be used for hosting Git repos:

- [Gitlab](gitlab.com)
- Customized Gitlab
  - [NOWA](https://vhrz1125.hrz.uni-marburg.de)
  - [Philipps-Universität Marburg](https://www.uni-marburg.de/de/hrz/dienste/versionsverwaltung)
- [Github](github.com)
- [Bitbucket](https://bitbucket.org/)

In this tutorial, a small example project hosted on the NOWA Gitlab is used for demonstration purposes:
<https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round>.
You can find its Git URL behind the Clone toggle.

A remote is added to a local repo with the `git remote` command by giving a self-chosen name and the URL:

```shell
# Add example project as remote
git remote add origin https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round.git
# Get history data
git fetch origin
```

A Repo can also be _cloned_ from a server,
which is a convenient shortcut for preparing a server repo for working on your local computer.
This is appropriate if you want to work on a project, but you still don't have a local repo for it.
You can also use _clone_ for projects you have created on Gitlab yourself.

- Initializes a new local repo with folder name derived from last part of URL
- Adds server repo as remote with name _origin_
- Fetches all data and prepares local repo for working

Please try to clone the example project:
If you have managed to clone the project locally, you have reached the end of the first tutorial chapter.

```shell
# Clone example project
git clone https://vhrz1125.hrz.uni-marburg.de/tcook/empirical-round.git
# Navigate into fresh repo
cd empirical-round
# List contents
ls
```

[tower]: https://www.git-tower.com
[gitkraken]: https://www.gitkraken.com/
[matlab]: https://www.mathworks.com/help/matlab/matlab_prog/set-up-git-source-control.html
