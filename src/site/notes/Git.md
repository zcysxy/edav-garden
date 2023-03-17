---
{"dg-publish":true,"permalink":"/git/"}
---

> [!meta]-
> sup:: [[App\|App]], [[Computer Science\|Computer Science]]  
> state:: done  

# Git

* Git is an implementation of **version control** (remember that it's not Git that invented the concept of version control)
* Git focuses on **plain text** files
* Git allows you to
    * revert selected files back to a previous state
    * revert the entire project back to a previous state
    * compare changes over time
    * see who last modified something that might be causing a problem

## Version Control

* **VCS (Version Control System)** is *any* system that records **changes (the history)** of a file/ set of file that helps you understand how it has progressed
    * **saving a file** is a simplified version control system, which only allows you to move forward
* History
    * Local VCS
        * keep **patch sets** (differences) in a local database
    * Centralized VCS
        * keep versioned files in a single center **server**
    * Distributed VCS
        * All **clients** don't just check out the latest snapshot of the files; rather, they **fully mirror** the repository, including its full history
        * Every **clone** is really a full backup of all the data

### Git vs Other VCS

* Snapshots vs Delta-Based VC
    * Delta(difference)-based:
        ![](https://git-scm.com/book/en/v2/images/deltas.png)
    * Snapshots:
        ![](https://git-scm.com/book/en/v2/images/snapshots.png)
* Nearly Every Operation In Git In **Local**
    * Hence Git is super fast
* Integrity by Hash
    * Git stores everything in its database not by file name but by the **hash** value of its contents
    * Git uses checksum to guarantee integrity
* Git Generally Only **Adds** Data
    * We can experiment without the danger of severely screwing things up

## Concepts

### Three States

1. **Modified**: changed the file but have not committed it to your database yet
2. **Staged**: marked a modified file in its current version to go into your next commit snapshot
    * 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
> sup:: [[App\|App]], [[Computer Science\|Computer Science]]  
> state:: done  

# Git

* Git is an implementation of **version control** (remember that it's not Git that invented the concept of version control)
* Git focuses on **plain text** files
* Git allows you to
    * revert selected files back to a previous state
    * revert the entire project back to a previous state
    * compare changes over time
    * see who last modified something that might be causing a problem

## Version Control

* **VCS (Version Control System)** is *any* system that records **changes (the history)** of a file/ set of file that helps you understand how it has progressed
    * **saving a file** is a simplified version control system, which only allows you to move forward
* History
    * Local VCS
        * keep **patch sets** (differences) in a local database
    * Centralized VCS
        * keep versioned files in a single center **server**
    * Distributed VCS
        * All **clients** don't just check out the latest snapshot of the files; rather, they **fully mirror** the repository, including its full history
        * Every **clone** is really a full backup of all the data

### Git vs Other VCS

* Snapshots vs Delta-Based VC
    * Delta(difference)-based:
        ![](https://git-scm.com/book/en/v2/images/deltas.png)
    * Snapshots:
        ![](https://git-scm.com/book/en/v2/images/snapshots.png)
* Nearly Every Operation In Git In **Local**
    * Hence Git is super fast
* Integrity by Hash
    * Git stores everything in its database not by file name but by the **hash** value of its contents
    * Git uses checksum to guarantee integrity
* Git Generally Only **Adds** Data
    * We can experiment without the danger of severely screwing things up

## Concepts

### Three States

1. **Modified**: changed the file but have not committed it to your database yet
2. **Staged**: marked a modified file in its current version to go into your next commit snapshot
    * 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
> sup:: [[App\|App]], [[Computer Science\|Computer Science]]  
> state:: done  

# Git

* Git is an implementation of **version control** (remember that it's not Git that invented the concept of version control)
* Git focuses on **plain text** files
* Git allows you to
    * revert selected files back to a previous state
    * revert the entire project back to a previous state
    * compare changes over time
    * see who last modified something that might be causing a problem

## Version Control

* **VCS (Version Control System)** is *any* system that records **changes (the history)** of a file/ set of file that helps you understand how it has progressed
    * **saving a file** is a simplified version control system, which only allows you to move forward
* History
    * Local VCS
        * keep **patch sets** (differences) in a local database
    * Centralized VCS
        * keep versioned files in a single center **server**
    * Distributed VCS
        * All **clients** don't just check out the latest snapshot of the files; rather, they **fully mirror** the repository, including its full history
        * Every **clone** is really a full backup of all the data

### Git vs Other VCS

* Snapshots vs Delta-Based VC
    * Delta(difference)-based:
        ![](https://git-scm.com/book/en/v2/images/deltas.png)
    * Snapshots:
        ![](https://git-scm.com/book/en/v2/images/snapshots.png)
* Nearly Every Operation In Git In **Local**
    * Hence Git is super fast
* Integrity by Hash
    * Git stores everything in its database not by file name but by the **hash** value of its contents
    * Git uses checksum to guarantee integrity
* Git Generally Only **Adds** Data
    * We can experiment without the danger of severely screwing things up

## Concepts

### Three States

1. **Modified**: changed the file but have not committed it to your database yet
2. **Staged**: marked a modified file in its current version to go into your next commit snapshot
    * 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
> sup:: [[App\|App]], [[Computer Science\|Computer Science]]  
> state:: done  

# Git

* Git is an implementation of **version control** (remember that it's not Git that invented the concept of version control)
* Git focuses on **plain text** files
* Git allows you to
    * revert selected files back to a previous state
    * revert the entire project back to a previous state
    * compare changes over time
    * see who last modified something that might be causing a problem

## Version Control

* **VCS (Version Control System)** is *any* system that records **changes (the history)** of a file/ set of file that helps you understand how it has progressed
    * **saving a file** is a simplified version control system, which only allows you to move forward
* History
    * Local VCS
        * keep **patch sets** (differences) in a local database
    * Centralized VCS
        * keep versioned files in a single center **server**
    * Distributed VCS
        * All **clients** don't just check out the latest snapshot of the files; rather, they **fully mirror** the repository, including its full history
        * Every **clone** is really a full backup of all the data

### Git vs Other VCS

* Snapshots vs Delta-Based VC
    * Delta(difference)-based:
        ![](https://git-scm.com/book/en/v2/images/deltas.png)
    * Snapshots:
        ![](https://git-scm.com/book/en/v2/images/snapshots.png)
* Nearly Every Operation In Git In **Local**
    * Hence Git is super fast
* Integrity by Hash
    * Git stores everything in its database not by file name but by the **hash** value of its contents
    * Git uses checksum to guarantee integrity
* Git Generally Only **Adds** Data
    * We can experiment without the danger of severely screwing things up

## Concepts

### Three States

1. **Modified**: changed the file but have not committed it to your database yet
2. **Staged**: marked a modified file in its current version to go into your next commit snapshot
    * 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




> [!meta]-
> sup:: [[App\|App]], [[Computer Science\|Computer Science]]  
> state:: done  

# Git

* Git is an implementation of **version control** (remember that it's not Git that invented the concept of version control)
* Git focuses on **plain text** files
* Git allows you to
    * revert selected files back to a previous state
    * revert the entire project back to a previous state
    * compare changes over time
    * see who last modified something that might be causing a problem

## Version Control

* **VCS (Version Control System)** is *any* system that records **changes (the history)** of a file/ set of file that helps you understand how it has progressed
    * **saving a file** is a simplified version control system, which only allows you to move forward
* History
    * Local VCS
        * keep **patch sets** (differences) in a local database
    * Centralized VCS
        * keep versioned files in a single center **server**
    * Distributed VCS
        * All **clients** don't just check out the latest snapshot of the files; rather, they **fully mirror** the repository, including its full history
        * Every **clone** is really a full backup of all the data

### Git vs Other VCS

* Snapshots vs Delta-Based VC
    * Delta(difference)-based:
        ![](https://git-scm.com/book/en/v2/images/deltas.png)
    * Snapshots:
        ![](https://git-scm.com/book/en/v2/images/snapshots.png)
* Nearly Every Operation In Git In **Local**
    * Hence Git is super fast
* Integrity by Hash
    * Git stores everything in its database not by file name but by the **hash** value of its contents
    * Git uses checksum to guarantee integrity
* Git Generally Only **Adds** Data
    * We can experiment without the danger of severely screwing things up

## Concepts

### Three States

1. **Modified**: changed the file but have not committed it to your database yet
2. **Staged**: marked a modified file in its current version to go into your next commit snapshot
    * ![[Git#^d876a5\|#^d876a5]]
3. **Committed**: the data is safely stored in your local database

![](https://git-scm.com/book/en/v2/images/areas.png)

### Commit

Someone make some changes, then they **commit** to **annotate the history of changes**. Once committed, a "snapshot" was taken of the differences made to the system at a given point in time.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-227.jpg)

### Push & Pull

When collaborating (even with yourself), you may want to host a **remote repository** (repository is just a *folder* of your project) that can accessed by anyone. **Push** is just submitting your commits (changes with annotations) to the remote; while **pull** is the opposite.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-274.jpg)

### Branches

In a large collaborating project, you may have different **lines of work** that have different focus and progress. Then you create **branches**, which leave the **main** (*used* to called **master** 😆) branch at some point and will eventually **merge** to the main branch.

In essence, when a branch gets merged into master, its commits get added to the top of the master history.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-257.jpg)

### Other

* `clone` fully copy a repository, including all the history
* `add` take changes into the control of git ^d876a5
* `fetch` get the changes from other repo but without automatically merging them
* `merge` accept the fetched changes
* `pull request` a GitHub tool that allows users to easily see the changes (the difference or "diff") that a **feature branch** is proposing as well as discuss any tweaks that said branch might require before it is merged into master
* `stash` temporarily commit

## Usage

### Update

> On [[Linux\|Linux]]

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

### Configuration

* User name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"
```

* Set the default branch to match the default branch name of GitHub (`main`)

```bash
git config --global init.defaultBranch main
```

### SSH Management

* Generate an SSH key for the first time

```bash
ssh-keygen -C "hello@gmail.com"
```

* Read and read the SSH key

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

- [!] `clip.exe` is only available on WSL, use `xclip` on other Linux systems, use `pbcopy` on [[macOS\|macOS]]

* Go to GitHub to add the SSH key
* Test the key (for GitHub)

```bash
ssh -T git@github.com
```

- [!] When first run, it will ask you to add a host to known hosts, type `yes`

### Workflow

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221018165408.png)

```bash
# Initialize a repo
git init
# Clone a repo
git clone <repo_url>
# Stage all changes in the **directory**
git add .
# Stage all changes in the **repository**
git add -A
# Commit
git commit -m "commit message"
# Check status
git status
# Push
git push [-u origin main]
# See history
git log
```

> [!rmk]
> * `origin` is the remote name
> * `main` is the brach name


</div></div>

3. **Committed**: the data is safely stored in your local database

![](https://git-scm.com/book/en/v2/images/areas.png)

### Commit

Someone make some changes, then they **commit** to **annotate the history of changes**. Once committed, a "snapshot" was taken of the differences made to the system at a given point in time.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-227.jpg)

### Push & Pull

When collaborating (even with yourself), you may want to host a **remote repository** (repository is just a *folder* of your project) that can accessed by anyone. **Push** is just submitting your commits (changes with annotations) to the remote; while **pull** is the opposite.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-274.jpg)

### Branches

In a large collaborating project, you may have different **lines of work** that have different focus and progress. Then you create **branches**, which leave the **main** (*used* to called **master** 😆) branch at some point and will eventually **merge** to the main branch.

In essence, when a branch gets merged into master, its commits get added to the top of the master history.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-257.jpg)

### Other

* `clone` fully copy a repository, including all the history
* `add` take changes into the control of git ^d876a5
* `fetch` get the changes from other repo but without automatically merging them
* `merge` accept the fetched changes
* `pull request` a GitHub tool that allows users to easily see the changes (the difference or "diff") that a **feature branch** is proposing as well as discuss any tweaks that said branch might require before it is merged into master
* `stash` temporarily commit

## Usage

### Update

> On [[Linux\|Linux]]

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

### Configuration

* User name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"
```

* Set the default branch to match the default branch name of GitHub (`main`)

```bash
git config --global init.defaultBranch main
```

### SSH Management

* Generate an SSH key for the first time

```bash
ssh-keygen -C "hello@gmail.com"
```

* Read and read the SSH key

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

- [!] `clip.exe` is only available on WSL, use `xclip` on other Linux systems, use `pbcopy` on [[macOS\|macOS]]

* Go to GitHub to add the SSH key
* Test the key (for GitHub)

```bash
ssh -T git@github.com
```

- [!] When first run, it will ask you to add a host to known hosts, type `yes`

### Workflow

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221018165408.png)

```bash
# Initialize a repo
git init
# Clone a repo
git clone <repo_url>
# Stage all changes in the **directory**
git add .
# Stage all changes in the **repository**
git add -A
# Commit
git commit -m "commit message"
# Check status
git status
# Push
git push [-u origin main]
# See history
git log
```

> [!rmk]
> * `origin` is the remote name
> * `main` is the brach name


</div></div>

3. **Committed**: the data is safely stored in your local database

![](https://git-scm.com/book/en/v2/images/areas.png)

### Commit

Someone make some changes, then they **commit** to **annotate the history of changes**. Once committed, a "snapshot" was taken of the differences made to the system at a given point in time.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-227.jpg)

### Push & Pull

When collaborating (even with yourself), you may want to host a **remote repository** (repository is just a *folder* of your project) that can accessed by anyone. **Push** is just submitting your commits (changes with annotations) to the remote; while **pull** is the opposite.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-274.jpg)

### Branches

In a large collaborating project, you may have different **lines of work** that have different focus and progress. Then you create **branches**, which leave the **main** (*used* to called **master** 😆) branch at some point and will eventually **merge** to the main branch.

In essence, when a branch gets merged into master, its commits get added to the top of the master history.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-257.jpg)

### Other

* `clone` fully copy a repository, including all the history
* `add` take changes into the control of git ^d876a5
* `fetch` get the changes from other repo but without automatically merging them
* `merge` accept the fetched changes
* `pull request` a GitHub tool that allows users to easily see the changes (the difference or "diff") that a **feature branch** is proposing as well as discuss any tweaks that said branch might require before it is merged into master
* `stash` temporarily commit

## Usage

### Update

> On [[Linux\|Linux]]

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

### Configuration

* User name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"
```

* Set the default branch to match the default branch name of GitHub (`main`)

```bash
git config --global init.defaultBranch main
```

### SSH Management

* Generate an SSH key for the first time

```bash
ssh-keygen -C "hello@gmail.com"
```

* Read and read the SSH key

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

- [!] `clip.exe` is only available on WSL, use `xclip` on other Linux systems, use `pbcopy` on [[macOS\|macOS]]

* Go to GitHub to add the SSH key
* Test the key (for GitHub)

```bash
ssh -T git@github.com
```

- [!] When first run, it will ask you to add a host to known hosts, type `yes`

### Workflow

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221018165408.png)

```bash
# Initialize a repo
git init
# Clone a repo
git clone <repo_url>
# Stage all changes in the **directory**
git add .
# Stage all changes in the **repository**
git add -A
# Commit
git commit -m "commit message"
# Check status
git status
# Push
git push [-u origin main]
# See history
git log
```

> [!rmk]
> * `origin` is the remote name
> * `main` is the brach name


</div></div>

3. **Committed**: the data is safely stored in your local database

![](https://git-scm.com/book/en/v2/images/areas.png)

### Commit

Someone make some changes, then they **commit** to **annotate the history of changes**. Once committed, a "snapshot" was taken of the differences made to the system at a given point in time.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-227.jpg)

### Push & Pull

When collaborating (even with yourself), you may want to host a **remote repository** (repository is just a *folder* of your project) that can accessed by anyone. **Push** is just submitting your commits (changes with annotations) to the remote; while **pull** is the opposite.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-274.jpg)

### Branches

In a large collaborating project, you may have different **lines of work** that have different focus and progress. Then you create **branches**, which leave the **main** (*used* to called **master** 😆) branch at some point and will eventually **merge** to the main branch.

In essence, when a branch gets merged into master, its commits get added to the top of the master history.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-257.jpg)

### Other

* `clone` fully copy a repository, including all the history
* `add` take changes into the control of git ^d876a5
* `fetch` get the changes from other repo but without automatically merging them
* `merge` accept the fetched changes
* `pull request` a GitHub tool that allows users to easily see the changes (the difference or "diff") that a **feature branch** is proposing as well as discuss any tweaks that said branch might require before it is merged into master
* `stash` temporarily commit

## Usage

### Update

> On [[Linux\|Linux]]

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

### Configuration

* User name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"
```

* Set the default branch to match the default branch name of GitHub (`main`)

```bash
git config --global init.defaultBranch main
```

### SSH Management

* Generate an SSH key for the first time

```bash
ssh-keygen -C "hello@gmail.com"
```

* Read and read the SSH key

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

- [!] `clip.exe` is only available on WSL, use `xclip` on other Linux systems, use `pbcopy` on [[macOS\|macOS]]

* Go to GitHub to add the SSH key
* Test the key (for GitHub)

```bash
ssh -T git@github.com
```

- [!] When first run, it will ask you to add a host to known hosts, type `yes`

### Workflow

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221018165408.png)

```bash
# Initialize a repo
git init
# Clone a repo
git clone <repo_url>
# Stage all changes in the **directory**
git add .
# Stage all changes in the **repository**
git add -A
# Commit
git commit -m "commit message"
# Check status
git status
# Push
git push [-u origin main]
# See history
git log
```

> [!rmk]
> * `origin` is the remote name
> * `main` is the brach name


</div></div>

3. **Committed**: the data is safely stored in your local database

![](https://git-scm.com/book/en/v2/images/areas.png)

### Commit

Someone make some changes, then they **commit** to **annotate the history of changes**. Once committed, a "snapshot" was taken of the differences made to the system at a given point in time.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-227.jpg)

### Push & Pull

When collaborating (even with yourself), you may want to host a **remote repository** (repository is just a *folder* of your project) that can accessed by anyone. **Push** is just submitting your commits (changes with annotations) to the remote; while **pull** is the opposite.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-274.jpg)

### Branches

In a large collaborating project, you may have different **lines of work** that have different focus and progress. Then you create **branches**, which leave the **main** (*used* to called **master** 😆) branch at some point and will eventually **merge** to the main branch.

In essence, when a branch gets merged into master, its commits get added to the top of the master history.

![](https://blog.red-badger.com/hubfs/Imported_Blog_Media/img-257.jpg)

### Other

* `clone` fully copy a repository, including all the history
* `add` take changes into the control of git ^d876a5
* `fetch` get the changes from other repo but without automatically merging them
* `merge` accept the fetched changes
* `pull request` a GitHub tool that allows users to easily see the changes (the difference or "diff") that a **feature branch** is proposing as well as discuss any tweaks that said branch might require before it is merged into master
* `stash` temporarily commit

## Usage

### Update

> On [[Linux\|Linux]]

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

### Configuration

* User name and email

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@example.com"
```

* Set the default branch to match the default branch name of GitHub (`main`)

```bash
git config --global init.defaultBranch main
```

### SSH Management

* Generate an SSH key for the first time

```bash
ssh-keygen -C "hello@gmail.com"
```

* Read and read the SSH key

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

- [!] `clip.exe` is only available on WSL, use `xclip` on other Linux systems, use `pbcopy` on [[macOS\|macOS]]

* Go to GitHub to add the SSH key
* Test the key (for GitHub)

```bash
ssh -T git@github.com
```

- [!] When first run, it will ask you to add a host to known hosts, type `yes`

### Workflow

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221018165408.png)

```bash
# Initialize a repo
git init
# Clone a repo
git clone <repo_url>
# Stage all changes in the **directory**
git add .
# Stage all changes in the **repository**
git add -A
# Commit
git commit -m "commit message"
# Check status
git status
# Push
git push [-u origin main]
# See history
git log
```

> [!rmk]
> * `origin` is the remote name
> * `main` is the brach name
