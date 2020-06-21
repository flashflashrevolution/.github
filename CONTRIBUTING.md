# Contributor Guidelines and Procedures

Please read this entire document before contributing to the repository.

If you lack confidence in git, please read it twice, and then ask questions.

- [Contributor Guidelines and Procedures](#contributor-guidelines-and-procedures)
  - [First things first](#first-things-first)
  - [Methodologies](#methodologies)
    - [Team Composition](#team-composition)
    - [Branching](#branching)
    - [Forking](#forking)
    - [Frequent Commits](#frequent-commits)
    - [Pull Requests](#pull-requests)
  - [Processes](#processes)
    - [Source Control Management](#source-control-management)
    - [Cloning (How-To)](#cloning-how-to)
    - [Branching (How-To)](#branching-how-to)
    - [Forking (How-To)](#forking-how-to)
    - [Development Recommendations](#development-recommendations)
    - [Pull Requests (How-To)](#pull-requests-how-to)
      - [Preparation](#preparation)
      - [Creation](#creation)
      - [Process](#process)

## First things first

When you have the desire to contribute to this repository,
please first open a discussion for the change via an issue on Github and feel free to bring your issue up in the #dev-chitchat discord channel.

If you would like to claim an issue that you did not create,
please discuss it in #dev-chitchat and follow up by leaving a comment in the issue itself.
A team memeber will assign you to the issue.

## Methodologies

First, an overview of contributing to our repositories.

### Team Composition

The FFR development team is made up of three groups.

1. Steering
2. Core
3. Public

### Branching

If you are a contributor in the Steering or Core group, you will be expected to follow a specific branching structure to keep things clean and organized.

Whenever you begin work on a new feature or bugfix, it's important that you create a new branch. This keeps your changes organized, allows for parallel work, and the ability to rapidly switch between tasks.

**Utilize this naming convention when coming up with a branch name:**

> **Feature:** feat/a-fancy-new-feature
>
> **Fix:** fix/notes-go-backwards

### Forking

If you are a contributor in the Public group,
there is no such branching restrictions.
You are instead required to create a fork of the repository and work from there.

### Frequent Commits

It is highly recommended that you make your commits as small and as often as possible.
This may seem like it will get unweildly,
but it makes it easy to follow your own work and quickly restore various pieces of your code to previous revisions.

Never worry about your commits cluttering up the mainline repository,
your branch will be squashed and merged onto the master branch.
This means that, in the end, you will be responsible for one single commit and merge commit.

### Pull Requests

Pull Requests are a request for your changes to be merged into the primary repository or master branch.

In the vast majority of cases, all contributors will be required to create pull requests to have their work merged into the master branch.

This gives the steering and core contributors a chance to review your work, offer advice, critisism, or find issues.

As mentioned before, this is also usually the step where your commit history will be squashed down to one commit and merged into master.

![WARNING][icon-octicon-alert] It is highly recommended that you make your pull requests as small as possible to avoid merge conflicts and conflicts of interest during the Pull Request review process.

---

## Processes

There are two recommended methods for managing your local repository copy.

### Source Control Management

[Fork](https://git-fork.com/)
  
  Fork is an elegant and performant graphical user interface for git.
  If you are uncomfortable with using the command line to manipulate your git repository,
  We highly recommend that you use this.

[Git](https://git-scm.com/)

  Git is a powerful source control system, we use it.
  **After installing git, install git-lfs!**

  > ```bash
  > git lfs install
  > ```

  It doesn't matter where you run this command, and you only need to run it once per user.

---

### Cloning (How-To)

1. Head to [Flash Flash Revolution on Github](https://github.com/flashflashrevolution).
2. Locate and navigate to the repository you would like to clone.
3. Click on [Clone or download ▾](media/contributing-clone-button.png) and then on [![copy][icon-octicon-clippy]](media/contributing-clone-copy-url-button.png).
4. Clone the repository in either Fork or Git.
    - Fork: Use the `File > Clone...` dialog to clone the repository.
    - Git:

    > ``` bash
    > # As an example, cloning the rCubed repository.
    > cd /your/preferred/directory
    > git clone git@github.com:flashflashrevolution/rCubed.git rCubed

---

### Branching (How-To)

To create a new branch and start working within it:

```bash

# Make sure the master branch is checked out.
git checkout master

# Create a new branch with a simple name, following guidelines.
git branch <feat/fix>/<name-of-branch>

# Switch to that new branch.
git checkout <name>

# (Optional Alternative) Quickly create and switch to a new branch.
git checkout -b <feat/fix>/<name-of-branch>
```

---

### Forking (How-To)

1. Head to [Flash Flash Revolution on Github](https://github.com/flashflashrevolution).
2. Locate and navigate to the repository you would like to clone.
3. Click on [Fork](media/contributing-fork-button.png).
4. You will be transferred to your fork. See from step 3 at [Cloning (How-To)](#cloning-how-to) for how to continue.
5. After you have cloned the repository, you will need a way to keep your repository up to date.
6. Acquire the url of the repository that you forked. This can be achieved by following the first three steps at [Cloning (How-To)](#cloning-how-to). (_Not the url of your fork_.)
7. Add the repository as your fork's upstream.

    > ``` bash
    > git remote add upstream <url>
    > ```

8. Whenever you want to update your fork with the latest upstream changes, you'll need to first fetch the upstream repo's branches and latest commits to bring them into your repository:

    > ``` bash
    > # Gets the newest repository data.
    > git fetch upstream
    >
    > # Fast-Forwards your fork's master branch to the latest master.
    > git fetch upstream master:master
    > ```

If there are no unique commits on the local master branch, git will simply perform a fast-forward. You should never be making changes on your local master branch, if the previous command fails you may try the following commands and hensforth never work on master again.

![WARNING][icon-octicon-alert]![WARNING][icon-octicon-alert]
If you find yourself here, please ask for help in discord. It is easy to be confused by git and think that you have lost your work. Rest assured that in most cases git is non-destructive and your work can be restored.
![WARNING][icon-octicon-alert]![WARNING][icon-octicon-alert]

> ``` bash
> git branch work-backup
> git pull --rebase
> ```

---

### Development Recommendations

- Try to start and finish what you are working on in a session or two.
- Don't work on something that touches many files without asking,
it will save you a headache and possible frustration.
- Keep your fork up to date as often as possible.
- Rebase your work onto your fork's master as often as possible to avoid complex merge resolutions.

---

### Pull Requests (How-To)

#### Preparation

Prior to submitting your pull request, you might want to do a few things to clean up your branch and make it as simple as possible for the original repo's maintainer to test, accept, and merge your work.

If any commits have been made to the upstream master branch, you should rebase your development branch so that merging it will be a simple fast-forward that won't require any conflict resolution work.

```bash
# Fetch upstream master and merge with your repo's master branch, if there were any new commits, rebase your development branch
git fetch upstream master:master
git rebase master newfeature
```

Now, it may be desirable to squash some of your smaller commits down into a small number of larger more cohesive commits. You can do this with an interactive rebase:

```bash
# Rebase all commits on your development branch
git checkout
git rebase -i master
```

This will open up a text editor where you can specify which commits to squash.

An interactive rebase, especially if there are merge conflicts, will require a force push. The safer option in such a case is --force-with-lease.

#### Creation

Once you've committed and pushed all of your changes to GitHub, go to the page for your fork on GitHub, select your development branch, and click the pull request button. If you need to make any adjustments to your pull request, just push the updates to GitHub. Your pull request will automatically track the changes on your development branch and update.

When you submit code to the repo, you give us the rights to use the code.

#### Process

You may be confronted with comments about extraneous files that you have added unintentionally to the repository.

Read up on how to [add files to .gitignore](https://help.github.com/en/github/using-git/ignoring-files).

You may be asked to go back and make changes to your code. To avoid this situation, especially if you are working for more than a few hours on something, share your progress by commenting on your issue asking for comments or advice, or in #dev-chitchat. (Make sure you link to the branch you are working in in your fork.)

Your pull request will be merged by a core developer when you have 2 or more sign-offs.

---

[//]: # (The following section is for image embed references.)

[icon-octicon-clippy]: https://cdnjs.cloudflare.com/ajax/libs/octicons/4.4.0/svg/clippy.svg
[icon-octicon-alert]: https://cdnjs.cloudflare.com/ajax/libs/octicons/4.4.0/svg/alert.svg
