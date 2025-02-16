# Mercurial - Distributed Version Control System

## 📌 Introduction
Mercurial (*Hg) is a **distributed version control system (DVCS)* designed for speed and efficiency. It is primarily used for managing software projects and code versioning.

## 🚀 Features
- *Distributed Architecture*: Every clone contains the full repository history.
- *Fast & Scalable*: Optimized for handling large projects efficiently.
- *Cross-Platform*: Works on Windows, macOS, and Linux.
- *Simple & Intuitive*: Easy to learn and use.
- *Extensible*: Supports plugins for additional functionality.

## 📥 Installation
### 🔹 Windows
Download and install from: [https://www.mercurial-scm.org/downloads](https://www.mercurial-scm.org/downloads)

### 🔹 macOS
Using Homebrew:
sh
brew install mercurial


### 🔹 Linux (Debian/Ubuntu)
sh
sudo apt update && sudo apt install mercurial


## 🛠 Basic Commands
### 🔹 Initialize a Repository
sh
hg init my_project


### 🔹 Clone a Repository
sh
hg clone <repository_url>


### 🔹 Check Repository Status
sh
hg status


### 🔹 Add & Commit Changes
sh
hg add myfile.py
hg commit -m "Initial commit"


### 🔹 View Commit History
sh
hg log


### 🔹 Push & Pull Changes
sh
hg push
hg pull


## 📝 Configuration
Set up your username:
sh
hg config --edit

Example entry:
ini
[ui]
username = Saubhik Mallick <saubhikmallick@gmail.com>


## 🔗 Resources
- Official Documentation: [https://www.mercurial-scm.org/](https://www.mercurial-scm.org/)
- Tutorial: [https://www.mercurial-scm.org/guide](https://www.mercurial-scm.org/guide)

---
*Mercurial* is a powerful DVCS that makes version control easy and efficient. Happy coding! 🚀
