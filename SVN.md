# 🚀 DevOps Assignment – 1

## Setting Up an SVN Server on Linux

## By: Uttkarsh Sharma

### 📌 Introduction
Subversion (SVN) is a version control system that helps manage changes to files and directories over time. This guide walks you through setting up an SVN server on Linux, configuring users, creating branches, merging changes, and resolving common errors in an easy-to-follow manner.

📖 For more details, refer to the official lecture notes: [SVN Lecture Notes](https://upessocs.github.io/#dir=/Lectures/DevOps%20CCVT/&file=037%20Unit%203%20Subversion%20(SVN).md)

---

## 🎥 Watch the SVN Demo

---

## 🔧 1. Install Subversion
On a Linux system, install Subversion using your package manager:

```sh
sudo apt update
sudo apt install subversion
```

---

## 📂 2. Create a Repository
Create a directory for your repositories and initialize a new repository:

```sh
sudo mkdir -p /var/svn/repos
sudo svnadmin create /var/svn/repos/myrepo
```

---

## ⚙️ 3. Configure svnserve
Edit the `svnserve.conf` file to configure access:

```sh
sudo nano /var/svn/repos/myrepo/conf/svnserve.conf
```

Modify the file as follows:

```ini
[general]
anon-access = none      # ❌ Disable anonymous access
auth-access = write     # ✅ Allow authenticated users to write
password-db = passwd    # 🔑 Use the passwd file for authentication
```

---

## 👤 4. Set Up Users
Edit the `passwd` file to add users:

```sh
sudo nano /var/svn/repos/myrepo/conf/passwd
```

Add user credentials:

```ini
[users]
alice = alicepassword
bob = bobpassword
```

---

## 🚀 5. Start svnserve
Start the svnserve daemon:

```sh
sudo svnserve -d -r /var/svn/repos
```

The `-d` flag runs it in daemon mode, and `-r` specifies the root directory for repositories.

---

## 🌿 6. Create a Branch
Before creating a branch, set up the standard SVN structure:

```sh
svn mkdir svn://localhost/myrepo/trunk -m "Creating trunk"
svn mkdir svn://localhost/myrepo/branches -m "Creating branches directory"
svn mkdir svn://localhost/myrepo/tags -m "Creating tags directory"
```

Then create a branch for development:

```sh
svn copy svn://localhost/myrepo/trunk svn://localhost/myrepo/branches/feature-branch -m "Creating feature branch"
```

---

## 🔀 7. Switch to a Branch
Switch your working copy to the new branch:

```sh
svn switch svn://localhost/myrepo/branches/feature-branch
```

---

## 🔄 8. Merge Changes
Merge changes from the branch back to the trunk:

```sh
svn merge svn://localhost/myrepo/branches/feature-branch
svn commit -m "Merged feature-branch into trunk"
```

---

## ⚔️ 9. Resolve Conflicts
If there are conflicts during an update or merge, resolve them:

```sh
svn resolve --accept working file.txt
```

---

## 🗑️ 10. Delete a File
Delete a file and commit the change:

```sh
svn delete file.txt
svn commit -m "Deleted file.txt"
```

---

## ❗ Common Errors and Fixes

### ❌ Error: Checked out revision 0
✅ Cause: The repository is empty. 🔧 Fix: Add and commit files:

```sh
echo "Hello, SVN!" > file.txt
svn add file.txt
svn commit -m "Added file.txt"
```

---

### ❌ Error: File not found: revision 1, path '/trunk'
✅ Cause: The repository does not have a trunk/branches/tags structure. 🔧 Fix: Create the structure:

```sh
svn mkdir svn://localhost/myrepo/trunk -m "Creating trunk"
svn mkdir svn://localhost/myrepo/branches -m "Creating branches directory"
svn mkdir svn://localhost/myrepo/tags -m "Creating tags directory"
```

Move existing files into trunk:

```sh
svn move svn://localhost/myrepo/file.txt svn://localhost/myrepo/trunk/file.txt -m "Moving file.txt to trunk"
```

---

### ❌ Error: Path '.' does not share common version control ancestry
✅ Cause: The working copy was checked out from the repository root instead of trunk. 🔧 Fix:

```sh
rm -rf myrepo  # ⚠️ WARNING: Deletes local working copy!
svn checkout svn://localhost/myrepo/trunk myrepo
cd myrepo
svn switch svn://localhost/myrepo/branches/feature-branch
```

Alternatively, force the switch:

```sh
svn switch --ignore-ancestry svn://localhost/myrepo/branches/feature-branch
```

---

This guide should help you set up and manage an SVN server with ease. 🚀🎉
