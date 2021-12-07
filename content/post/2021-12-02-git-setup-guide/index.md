---
title: 'Git Setup Guide for Windows'
subtitle: ''
summary: 'Get the recommended tools for your Windows computer to be ready for Git and Gitlab'
authors: [tamara-cook]
tags: [Git]
categories: [Howtos]
date: 2021-12-02T10:33:26+01:00
lastmod: 2021-12-02T10:33:26+01:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [gitlab]
---

This guide walks you through getting the recommended tools for a git-based workflow on a Windows computer.
Please try to finish the steps in order to be ready for Git.

## terminal

There are graphical interfaces for Git, but it's a command line tool at its core.
People often use both interfaces side by side in combination.
Even if you prefer the GUI, you should be able to run Git from the command line.

[Windows Terminal] is Microsoft's modern Windows 10 app for running command lines.
It provides multiple tabs, custom command lines, more intuitive key bindings, color schemes etc.
Please install Windows Terminal from the Windows Store.

## NOWA Gitlab

{{< cta cta_icon_pack="fab" cta_icon="gitlab" cta_text="Request an account for the NOWA Gitlab service" cta_link="mailto:nowa@staff.uni-marburg.de?subject=NOWA%20Gitlab%20registration%20request&body=Dear%20NOWA%20team%2C%0A%0APlease%20create%20a%20Gitlab%20account%20for%20me.%0A%0ABest%20regards%0AJ.%20Doe" cta_new_tab="false" >}}

{{% callout warning %}}
The NOWA Gitlab instance is exclusively reserved for direct or indirect members of the CRC/TRR 135.
Other members of Philipps-University of Marburg are invited to try out the new [Gitlab service] provided by the HRZ.
Please remember to use your university email for registration requests and maybe elaborate a bit on your relationship with the CRC (project, work group).
Thanks in advance.

[gitlab service]: https://www.uni-marburg.de/en/hrz/services/version-management

{{% /callout %}}

If you have got a Gitlab account, you can create new projects, upload work, and view other users' projects on Gitlab.
In order to authenticate git with Gitlab, please create a [personal access token] in your account's preferences.
This token will be used for Git operations in place of your account password.

## Git for Windows

Please download and install the newest release of [Git for Windows][gfw].
When you go through the installer, please adjust the following settings:

- Activate the “Add a Git Bash Profile to Windows Terminal” component
- Choose a default text editor which is installed on your computer. Git uses this editor to ask for text input, if it is run from command line. If you're in doubt, simply choose Notepad.
- Select “Override the default branch name for new git repositories” and leave the input field set to “main”

## Running Git commands

- In Windows Terminal, open a new tab by selecting Git Bash from the dropdown (CTRL + Shift + Space).
- If you don't have Windows Terminal, open Git Bash from Windows menu.
- You should see the Bash command line with the dollar prompt. Try these commands to check if it's working:
  - `git --version`
  - type `git --ver` and tab to see if tab completion works. The line should be replaced with `git --version`.
- You can set Git Bash as the default command line via Settings from dropdown or _CTRL+,_.

## Graphical Git Interface

Please download and install [Git Tower], the graphical interface used in this course, on your computer.
Please adjust these settings when you proceed through the setup assistant:

- Select the trial version
- Please enter your proper name and email, because these are added to your contributions when you work with Git, they can't be changed afterwards, and they can be visible to others if you share your work

You can add Gitlab as a service via Services -> Gitlab CE/E. Please enter these settings:

Authentication
: Personal Access Token

Host
: https://vhrz1125.hrz.uni-marburg.de/

Username
: Your Gitlab Username

Personal Access Token
: Your generated PAT

[personal access token]: https://vhrz1125.hrz.uni-marburg.de/-/profile/personal_access_tokens
[windows terminal]: https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab
[gfw]: https://gitforwindows.org
[git tower]: https://www.git-tower.com/windows
