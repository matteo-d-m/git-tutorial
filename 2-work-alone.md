# One-Person Workflows
A deep understanding of Git and GitHub can require months of training, but one hour of focus is enough to acquire a theoretical minimum &mdash; that is, the essential concepts that allow anyone to get started. In particular, a basic use of Git and GitHub relies entirely on 5 simple concepts: _repository_, _tracking_, _commit_, _remote_, and _push_. 

The next sections will describe all 5 concepts in detail, providing relevant code examples for each one.

> [!NOTE]
> Most code examples come with a corresponding video that shows them in action. The videos were recorded from a Linux terminal, so they might look different from what you would see on a Windows or a Mac machine. However, the differences are only aesthetic and all concepts apply equally to any operating system. 

## 1. Repository
In version control jargon, a repository is a directory (that is, a folder) whose contents are within the scope of a VCS. If you think of the VCS as a person that looks at a scene, you can think of a repository as any object that falls within the person's visual field and as such, can be touched and manipulated by the person. Similarly, a repository falls within the "visual field" of the VCS, which can thus operate on it. 

Once Git is installed in a computer ([installation link](https://git-scm.com/)), transforming a simple directory into a repository becomes extremely simple. For example, consider a directory named `git-tutorial`. Imagine this directory is located at `/home/user/Documents/git-tutorial`. In a freshly opened terminal, transforming it into a repository is as simple as:

```bash
mkdir Documents/git-tutorial		# create the directory if not existing yet
cd Documents/git-tutorial	        # go to the directory of interest
git init					        # initialise a Git repository inside it
```
The video below shows the code in action:

![Initialize a Git Repository](./files/git-init.mp4)

## 2. Tracking
Transforming a directory into a repository does not imply that the VCS will keep track of all its contents: while it can see all the files in the repository, the VCS does not necessarily watch all all of them to record their modifications. In fact, the system only watches the files that have been explicitly added to a tracking list by the owner of the repository. 

To know which files are subject to tracking at any given time, you can use the command `git status` from within your repository. This will print a list of all the files in the directory (including subdirectories), specifying which ones are being tracked and which are not. 

In a newly created repository, no file is being tracked. To start tracking a file of interest, you use the command `git add <filename>` &mdash; where `<filename>` is the name of the file you want to track. This will add the file to the tracking list and Git will start recording the changes that you make. 

## 3. Commit
Usually, files undergo multiple modifications before reaching a satisfying stage. For example, you modify a script multiple times before it works as intended, or you draft multiple versions of a paper before submitting. Not all the modifications made to a file are worth of notice, but some are and must be saved permanently. In version control jargon, those are the modifications you _commit_ &mdash; that is, you make a commitment to keeping them. 

Importantly, committed modifications are accompanied by a _commit message_ &mdash; that is, a short sentence that summarizes what changed between the previous and current commits. For example, if you commit a document called `file.txt` after creating it, your commit message will be something like `"create file.txt"`. 

In practice, creating a commit like the one described above is as simple as:

```bash
git commit file.txt -m "create file.txt"
```

Note that by convention, commit messages are usually written in imperative style: _create_, not _created_; _add_, not _added_; _do_, not _done_; _modify_, not _modified_... etc.

It is worth noting that committing to a modification does not mean that the file cannot be modified any further: it simply means that the VCS will forever record the state of the file at the time of the commit, with a commit message to briefly describe such state and an open possibility to restore it in the future.

The video below shows the previous steps in action. First, a file is created using the Linux command `touch` (you can create the file manually if you do not use a Linux computer). Subsequently, calling `git status` shows that the file exists but is not inside the tracking list. Therefore, the file is added to the tracking list using `git add` and finally, the creation of that file is committed with a corresponding message.

![Print Git status, add to tracking list and commit](./files/git-status-add-commit.mp4)

## 4. Remote
As described above, a repository is a directory whose contents can be tracked by a VCS. This directory is located inside your own computer, as is the VCS: in other words, the repository is _local_. 

Any local repository can be coupled with a copy hosted on a remote server, which is usually managed by companies like [GitHub](https://github.com/), [GitLab](https://about.gitlab.com/) or [BitBucket](https://bitbucket.org/). The copy hosted on the remote server is the repository's _remote_ and its role is two-fold: on the one hand, provide a back-up for the local copy, and on the other, share the repository with other users (for example colleagues, students or users of a toolbox that you developed). Once you have coupled a local repository with a remote, the two repositories can exchange files _and version histories_ bidirectionally &mdash; and, if you allow them, your collaborators can act on it. 

Adding a remote to a local repository is as simple as: 

```bash
git remote add origin <remote url>
```

where `<remote url>` is the web address of the remote. 

Clearly, a remote cannot be added to a local if it does not exist. To this end, you can create a GitHub account and, once you are logged in, click on the `+` sign on the top-right side of any page. Once you have done that, you can click on `New repository` as in the screenshot below, then follow the instructions on screen to create a new remote.

![create-new-repo](./files/create-new-repo.png)

Each newly created remote is assigned a URL with the structure `https://github.com/username/repository.git`, which can be copied and pasted in the command to pair a local with the remote.

For example, creating a repository named `git-tutorial` under user `coneco-lab` would result in the URL `https://github.com/coneco-lab/git-tutorial.git`. With this URL, the command to add a remote looks like the following:

```bash
git remote add origin https://github.com/coneco-lab/git-tutorial.git
```

The video below shows all the steps described in this section, from creating a remote repository on GitHub to coupling it with a local.

![Creating and adding a GitHub remote](./files/git-create-and-add-remote.mp4)


## 5. Push
Imagine you have a local repository that is paired with a remote. You have been working on some file in your local and you have finally reached a satisfactory result. Therefore, you commit to your changes and you decide to update the remote. This will change the outdated file on the remote with the updated file from the local, while keeping an explicit trace of the changes that you have made. 

In VCS jargon, updating a remote with newly committed changes is known as _pushing_ your changes to the remote. Pushing a change to a remote is as simple as:

```bash
git push origin main
```

This command means that the `git` VCS should `push` (that is, upload) your changes to `origin`, which is the default identifier given by Git to the remote. These changes shall be pushed to the `main` branch of the repository. 

> [!NOTE] A branch is one of many sections of a repository. Branches are parallel, independent, and intended for multiple users who work on multiple subtasks within a complex project. In introductory use cases like this one, repositories can be thought of as having a single branch called _main_.

The following video demonstrates a simple push to the remote's main. 

![Pushing to a remote](./files/git-push.mp4)

As you can see, pushing to GitHub requires to insert your username (which you choose when you create your account) and a password (which is not shown in the terminal for privacy). 

> [!IMPORTANT]
> GitHub has recently implemented a new security policy that forces users to authenticate with _personal access tokens_ (instead of simple passwords) when carrying out repository operations from the terminal. Personal access tokens are basically random sequences of letters and numbers, with an expiration date. GitHub generates tokens upon request, and you can use them to authorize repository operations until their expiration date. The difference between tokens and the standard GitHub password is that the tokens are needed for repository operations in the terminal, while the standard password is needed to log into your GitHub account. You can go [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) for detailed information about access tokens, and [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic) to create a basic one.

### 5.1. Commit history on GitHub
If you navigate to any public repository on GitHub (for example, [this one](https://github.com/coneco-lab/brainstim-multimodal)) you will see a panel like the following:

![repo-panel-whole](./files/image.png)

This panel shows a list of the repository's contents (on the left), each one with the latest commit message (in the center) and the date they were last pushed to the remote (on the right): for example, file `pipeline_debriefing.ipynb` (the last one in the list) was last committed with a message that said `polish pipeline_debriefing.ipynb`, indicating that the last modification applied to the file was a mere polishing (that is, honing minor flaws). Such last modification was pushed to the remote 5 days ago (at the time of writing). 

Beside the list of files with the latest commits and push times, the panel contains two other important pieces of information, both located in the upper strip: 

![repo-panel-top-strip](./files/image-1.png)

The first piece of information concerns the latest commit, which was pushed by user `matteo-d-m` (in this case, the owner of the repository) with the commit message `update README.md`. Git assigned the commit a unique identifier (visible on the right side of the strip), which is `8421a5c` and can be used to revert subsequent file versions to the present state. 

The second piece of information is right next to the commit's identifier, and it is the total number of commits that were pushed to the remote (in this case, 50). Clicking on it opens a list of all commits with the corresponding messages and unique identifiers, as follows: 

![commit-history](./files/image-2.png)

Each item of this list can be inspected closely by clicking on it. This will open the raw contents of the file, where deletions will be highlighted in red and marked by a "minus" sign, while additions will be highlighted in green and marked by a "plus" sign:

![commit-contents](./files/image-3.png)

Here lies the power of Git and GitHub: Git keeps track of all changes, line by line, and assigns them a unique identifier once you decide to commit. Downstream, GitHub keeps a back-up of all those changes in the cloud, preserving them in case you lose access to your local and making them available to the general public if you want to. 