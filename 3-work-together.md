# Basic Collaborative Workflows

## Forks
The workflow described thus far depicts a scenario where you first create a local repository, and then couple it with a remote. This assumes that you are starting a project from scratch and you want to have a remote back-up or to share it with other people. 

A different, but equally common scenario is that you work on a project that has been started and published by someone else. For example you might jump in on a project started by a colleague, have your own copy of the materials for a hands-on activity, or contribute to a Python library. In these cases, you should start by _forking_ the GitHub repository of interest. 

Forking creates a copy of a GitHub repository that was created by another user. When you fork someone's repository, you are copying all its contents and the associated version history and pasting them inside your user account. Your copy will be called the _fork_ and the original repository will be called the _upstream_. The fork will live in parallel to the upstream and idependently from it, so changes made to either will not affect the other.

The video below demonstrates forking MNE's GitHub repository into my own user account:

![Forking a GitHub remote](./files/github-fork.mp4)

## Clones
Creating a fork on GitHub is not enough to start working on it: to do so, you need to pair it with a local. 

To pair any existing remote (including a fork) with a new local you need to _clone_ it. Cloning a remote creates a local copy of it, downloading all the files of the repository and their version histories to your computer. 

A clone is a full-blown repository that inherits the version history of the corresponding remote, such that your own commits will be appended to the existing history that was created by previous users. Nonetheless, your commits can be pushed freely because the remote is yours and it is completely independent from the original that you forked. Moreover, you do not need to run `git remote add origin`, as the pairing with the remote was done at the moment of cloning.  

The following video demonstrates cloning MNE-Python's GitHub repository into a local, which I arbitrarily decide to put inside directory `Documents`. As can be seen, running `git status` after cloning returns a meaningful result (and not an error), which implies that cloning returned a proper repository and not a simple folder. Subsequently, running Linux command `ls` prints a list of the repository's contents, which indeed are the same as the remote's. 

![Cloning a remote](./files/git-clone.mp4)

> [!NOTE]
> If you do not use Linux, you can print a list of a a repository's (or directory's) contents using `ls` (if Mac) or `dir` (if Windows).

> [!NOTE]
> If you clone a repository that contains something that can be installed (like MNE-Python), you are not actually performing the > installation: you are merely creating a local copy of the installable code 

## Syncing Forks and Pull Requests
By default, any change applied to the upstream does not affect its forks. However, GitHub constantly keeps track of all the changes made to the upstream and its forks, compares their version histories to see if they align, and warns users if they do not. For example, changes in the upstream are signalled  by a message that appears on top of any fork and says `This branch is <number> commits behind <name of the upstream>`. This is shown in the screenshot below, where my fork of MNE-Python is 1 commit behind of upstream `mne-tools/mne-python:main` (that is, the `main` branch of repository `mne-python` by user `mne-tools`):

![sync-fork](./files/github-sync-fork.png)

If you make some local commits and push them to the fork, the message will read `This branch is <number> commits ahead of and <number> commits behind <name of the upstream>` . 

If you want to enjoy all the changes made to the upstream after you forked it, you need to _synchronize_ your fork by pressing the `Sync fork` button (see screenshot above). Doing so will take the upstream changes into your fork but will not take your fork's changes into the upstream. This ensures that authors of a fork can stay up-to-date with the upstream while they try adding new features, but the upstream remains stable and does not incur a risk of breaking because of inappropriate changes.   

If you want your changes incorporated into the upstream, you need to submit a _pull request_ to it. A pull request is a request to the owner of the upstream to review and incorporate your changes. The owner of the upstream is free to accept or decline the pull request, and the owner of the fork has no way to force the process. To submit a pull request, you can press on the `Contribute` button that is located next to `Sync fork` (see above).