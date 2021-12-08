---
title: 'Version Control with Git'
event:
event_url:
location: https://uni-marburg.webex.com/uni-marburg/j.php?MTID=ma5e03a310f0ed4ee19f9c7e2a26cc0c5
summary:
abstract: |
  Publishing experimental design and analysis code is a crucial step towards Open Science,
  because it improves reproducibility of research results.
  But what does it mean to develop open source software?
  Essentially, it's all about collaboration and version control.
  It means that from the first line on you're writing code or text to be read and edited by others,
  be it your colleagues, an interested stranger, or future-yourself.

  - It should be easy for somebody else to pick up your project at the current state and continue development.
  - State transitions in the project should be easy to comprehend
  - It should be easy to revert unwanted changes and return to an earlier state
  - It should be easy to try out ideas without having to delete your current state
  - It should be easy to reintegrate parallel work

  Git has been designed to meet these requirements and became the defacto standard versioning and collaboration tool in the OSS industry.
  After taking this course, participant will know the critical parts of git and how it can bring its strengths to research projects.
  The course can also be interesting for IT or RDM staff, because git doesn't make many assumptions about the projects it is used for.

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: 2021-12-08T09:00:00+01:00
date_end: 2021-12-08T13:00:00+01:00
all_day: false

# Schedule page publish date (NOT event date).
publishDate: 2021-11-28T12:09:37+01:00

authors: [tamara-cook]
tags: [git]

# Is this a featured event? (true/false)
featured: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
  - name: 🗳 Poll for date/time
    url: https://terminplaner.dfn.de/Le28LJbXkSi9STLh

# Optional filename of your slides within your event's folder or a URL.
url_slides: slides.html

url_code:
url_pdf:
url_video:

# Markdown Slides (optional).
#   Associate this event with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ''

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: [gitlab]
---

## Agenda

During the course, I'll demonstrate Git usage.
If you want to reproduce my examples, you should have a computer running Git at hand.
Please see [this setup guide]({{<ref "../../post/2021-12-02-git-setup-guide">}}) for instructions.

09:00
: Welcome and getting prepared

09:15
: General introduction to Git

09:45
: Git anatomy: How to inspect a Git project

10:45
: Break and time for questions

11:15
: Git Surgery: How to add work to a Git project

12:15
: Remaining issues

12:45
: End, time for questions
