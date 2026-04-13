# 🗂️ Git Repository Management – Stratos DC

A reference guide for managing Git repositories and branches on the **Storage Server** within the Stratos DC environment.

---


## Task 1 – Set Up Git Repository

**Objective:** Install Git and create a central bare repository.

### Steps

1. Access the Storage Server via SSH.
2. Install the Git package using the `yum` package manager.
3. Initialize a bare repository at the specified path.

```bash
sudo yum install -y git
sudo git init --bare /opt/ecommerce.git
```

---

## Task 2 – Clone Git Repository

**Objective:** Clone an existing repository as a specific user (`natasha`) into a target directory.

### Steps

1. Navigate to the target directory: `/usr/src/kodekloudrepos`.
2. Use `sudo -u` to ensure the clone operation is performed by the user `natasha` without altering directory permissions.

```bash
cd /usr/src/kodekloudrepos
sudo -u natasha git clone /opt/blog.git
```

---

## Task 3 – Fork a Git Repository

**Objective:** Fork a repository using the Gitea Web UI.

### Steps

1. Open the Gitea UI.
2. Log in with the credentials for user **jon**.
3. Locate the repository `sarah/story-blog`.
4. Click the **Fork** button to create a copy under jon's account.

> ℹ️ No CLI commands required — this task is completed entirely through the Gitea web interface.

---

## Task 4 – Update Repository with Sample HTML

**Objective:** Transfer a file from the Jump Host and commit it to the repository on the Storage Server.

### Steps

**From the Jump Host** — copy the file to the Storage Server:

```bash
scp /tmp/index.html natasha@ststor01:/usr/src/kodekloudrepos/apps/
```

**On the Storage Server** — navigate to the repository, then add, commit, and push the changes:

```bash
cd /usr/src/kodekloudrepos/apps
git add index.html
git commit -m "Added index.html file"
git push origin master
```

---

## Task 5 – Delete Git Branch

**Objective:** Remove an obsolete branch from a local repository.

### Steps

1. Navigate to the repository located at `/usr/src/kodekloudrepos/games`.
2. Delete the specified branch and verify the deletion.

```bash
cd /usr/src/kodekloudrepos/games
git branch -d xfusioncorp_games

# Verify current branches
git branch
```
